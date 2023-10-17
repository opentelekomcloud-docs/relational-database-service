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

When you restore data from backup files to self-built MySQL databases, ensure that the target MySQL version is later than or equal to the original MySQL version.

During data restoration, run the following command to view the restoration process:

**ps -ef \| grep mysql**

Procedure
---------

#. Download the qpress RPM file `qpress-11-1.el7.x86_64.rpm <https://repo.percona.com/yum/release/7/RPMS/x86_64/qpress-11-1.el7.x86_64.rpm>`__. Enterprise Linux 7 (CentOS 7, RHEL 7, Rocky Linux 7, and AlmaLinux 7) is used as an example.

   For details about RPM files of other OSs, see https://repo.percona.com/yum/release/.

#. Upload the qpress RPM file to the ECS.

#. Install qpress on the ECS.

   **rpm -ivh** *qpress-11-1.el7.x86_64.rpm*

#. Download `XtraBackup <https://www.percona.com/downloads/Percona-XtraBackup-2.4/LATEST/>`__ from the website, for example, percona-xtrabackup-24-2.4.9-1.el7.x86_64.rpm.

   .. important::

      -  For MySQL 5.6 and 5.7, download `XtraBackup 2.4.9 <https://www.percona.com/downloads/Percona-XtraBackup-2.4/LATEST/>`__ or later versions.
      -  For MySQL 8.0, download `XtraBackup 8.0 <https://www.percona.com/downloads/Percona-XtraBackup-8.0/LATEST/>`__ or later versions.

#. Upload XtraBackup to the ECS.

#. Install XtraBackup on the ECS.

   **rpm -ivh** *percona-xtrabackup-24-2.4.9-1.el7.x86_64.rpm* **--nodeps --force**

#. On the ECS, decompress the full backup file that has been downloaded.

   a. Create a temporary directory **backupdir**.

      **mkdir** *backupdir*

   b. Decompress the package.

      **xbstream -x** **-p 4** **<** **./**\ *Full backup file*\ **.qp** **-C** **./backupdir/**

      -  For MySQL 5.6 and 5.7, run **innobackupex --parallel 4 --decompress** **./backupdir**.
      -  For MySQL 8.0, run **xtrabackup --parallel 4 --decompress --target-dir=\ ./backupdir**.

      **find** *./backupdir/* **-name** ``'*.qp'`` **\|** *xargs* **rm -f**

#. Apply the log.

   -  For MySQL 5.6 and 5.7, run **innobackupex --apply-log** **./backupdir**.
   -  For MySQL 8.0, run **xtrabackup --prepare --target-dir=./backupdir**.

#. Back up data.

   a. Stop MySQL database services.

      **service** *mysql* **stop**

      .. note::

         For MySQL 5.7, run the following command to stop MySQL database services:

         **/bin/systemctl stop mysqld.service**

   b. Back up the original database directory.

      **mv** /var/lib/mysql/data /var/lib/mysql\ */data_bak*

   c. Create a new database directory and change the permissions.

      **mkdir** */var/lib/mysql/data*

      **chown** *mysql:mysql* */var/lib/mysql/data*

#. Copy the full backup file and modify the directory permissions.

   -  For MySQL 5.6 and 5.7, run **innobackupex --defaults-file=/etc/my.cnf --copy-back** **./backupdir**.
   -  For MySQL 8.0, run **xtrabackup --defaults-file=/etc/my.cnf --copy-back --target-dir=./backupdir**.

   **chown -R** *mysql:mysql /var/lib/mysql/data*

   .. note::

      Clear the content in the *var/lib/mysql/data* directory in advance.

#. Start the database.

   **service** *mysql* **start**

   .. note::

      For MySQL 5.7, run the following command to start the database:

      **/bin/systemctl start mysqld.service**

#. Log in to the database and view the restoration result.

   **mysql -u -root**

   **show databases**


   .. figure:: /_static/images/en-us_image_0000001426447917.png
      :alt: **Figure 1** Viewing the restoration result

      **Figure 1** Viewing the restoration result
