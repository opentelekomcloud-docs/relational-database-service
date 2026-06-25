:original_name: rds_08_0044.html

.. _rds_08_0044:

Restoring from Backup Files to a Self-Built MySQL Database
==========================================================

Scenarios
---------

You can download backup files by referring to :ref:`Downloading a Backup File <rds_08_0006>` and restore data from them.

.. important::

   Backup data cannot be restored to local databases that run the Windows operating system.

   Only x86 packages of the open-source backup tool XtraBackup are supported. Therefore, you are advised to restore backup data to self-built databases on Arm-based ECSs by migrating data with DRS or exporting and importing data. For details, see :ref:`Data Migration <rds_05_0001_02>`.

Prerequisites
-------------

-  This section only covers restoring a full backup of an RDS for MySQL 5.7 or 8.0 DB instance to an on-premises database of the corresponding version. Incremental backup restoration is not included.

-  The minor version of the on-premises MySQL database must be the same as that of your RDS for MySQL DB instance.

-  During the restoration, do not run other workloads on the on-premises database.

-  During data restoration, run the following command to view the restoration process:

   .. code-block::

      ps -ef | grep mysql

Procedure
---------

#. Download the qpress RPM file `qpress-11-1.el7.x86_64.rpm <https://repo.percona.com/yum/release/7/RPMS/x86_64/qpress-11-1.el7.x86_64.rpm>`__. Enterprise Linux 7 (CentOS 7, RHEL 7, Rocky Linux 7, and AlmaLinux 7) is used as an example.

   For details about RPM files of other OSs, see https://repo.percona.com/yum/release/.

#. Upload the qpress RPM file to the ECS.

#. Install qpress on the ECS.

   **rpm -ivh** *qpress-11-1.el7.x86_64.rpm*

#. Download `XtraBackup <https://www.percona.com/downloads/Percona-XtraBackup-2.4/LATEST/>`__ from the website, for example, percona-xtrabackup-24-2.4.9-1.el7.x86_64.rpm.

   .. important::

      -  For MySQL 5.7, download `XtraBackup 2.4.9 <https://www.percona.com/downloads/Percona-XtraBackup-2.4/LATEST/>`__ or later versions.
      -  For MySQL 8.0, download `XtraBackup 8.0 <https://www.percona.com/downloads/Percona-XtraBackup-8.0/LATEST/>`__ or later versions.

#. Upload XtraBackup to the ECS.

#. Install XtraBackup on the ECS.

   .. code-block::

      rpm -ivh percona-xtrabackup-24-2.4.9-1.el7.x86_64.rpm --nodeps --force

#. On the ECS, decompress the full backup file that has been downloaded.

   a. Create a temporary directory **backupdir**.

      .. code-block::

         mkdir backupdir

   b. Decompress the package.

      -  MySQL 5.7:

         .. code-block::

            xbstream  -x --parallel 4 < ./full_backup.qp -C ./backupdir/
            innobackupex --parallel 4 --decompress ./backupdir

      -  MySQL 8.0:

         .. code-block::

            xbstream  -x --parallel 4 < ./full_backup.qp -C ./backupdir/
            xtrabackup --parallel 4 --decompress --target-dir=./backupdir

#. Delete the .qp file.

   .. code-block::

      find ./backupdir/  -name '*.qp' | xargs rm -f

#. Apply the log.

   -  MySQL 5.7:

      .. code-block::

         innobackupex --apply-log ./backupdir

   -  MySQL 8.0:

      .. code-block::

         xtrabackup --prepare --target-dir=./backupdir

#. Back up data.

   a. Stop MySQL database services.

      .. code-block::

         service mysql stop

      .. note::

         For MySQL 5.7, run the following command to stop MySQL database services:

         .. code-block::

            /bin/systemctl stop mysqld.service

   b. Back up the original database directory.

      .. code-block::

         mv /usr/local/mysql/data  /usr/local/mysql/data_bak
         mkdir /usr/local/mysql/data

   c. Create a new database directory and change the permissions.

      .. code-block::

         chown mysql:mysql /usr/local/mysql/data

#. Copy the full backup file and modify the directory permissions.

   -  MySQL 5.7:

      .. code-block::

         innobackupex --defaults-file=/etc/my.cnf --copy-back ./backupdir
         chown -R mysql:mysql /usr/local/mysql/data

   -  MySQL 8.0:

      .. code-block::

         xtrabackup --defaults-file=/etc/my.cnf --copy-back --target-dir=./backupdir
         chown -R mysql:mysql /usr/local/mysql/data

   .. note::

      Clear the content in the *usr/local/mysql/data* directory in advance.

#. Start the database.

   .. code-block::

      service mysql start

   .. note::

      For MySQL 5.7, run the following command:

      .. code-block::

         /bin/systemctl start mysqld.service

#. Log in to the database and view the restoration result.

   .. code-block::

      show databases


   .. figure:: /_static/images/en-us_image_0000001426447917.png
      :alt: **Figure 1** Viewing the restoration result

      **Figure 1** Viewing the restoration result
