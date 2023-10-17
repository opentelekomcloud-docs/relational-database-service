:original_name: rds_faq_0050.html

.. _rds_faq_0050:

How Can I Connect to a PostgreSQL Database Through JDBC?
========================================================

Although the SSL certificate is optional if you choose to connect to a database through Java database connectivity (JDBC), download an SSL certificate to encrypt the connections for security.

Prerequisites
-------------

Familiarize yourself with:

-  Computer basics.
-  Java programming language.
-  JDBC knowledge.

Obtaining and Using JDBC
------------------------

-  JDBC driver download address: https://jdbc.postgresql.org/download/
-  JDBC Interface: https://jdbc.postgresql.org/documentation/

Connection with the SSL Certificate
-----------------------------------

.. note::

   Download the SSL certificate and verify the certificate before connecting to databases.

   In the **DB Information** area on the **Basic Information** page, click |image1| in the **SSL** field to download the root certificate or certificate bundle.

#. Connect to the RDS PostgreSQL DB instance through JDBC.

   .. code-block::

      jdbc:postgresql://<instance_ip>:<instance_port>/<database_name>?sslmode=verify-full&sslrootcert=<ca.pem>

   .. table:: **Table 1** Parameter description

      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter         | Description                                                                                                                                                                                              |
      +===================+==========================================================================================================================================================================================================+
      | *<instance_ip>*   | If you attempt to access the RDS DB instance through an ECS, set *instance_ip* to the floating IP address displayed on the **Basic Information** page of the DB instance to which you intend to connect. |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                   | If you attempt to access the RDS DB instance through an EIP, set *instance_ip* to the EIP that has been bound to the DB instance.                                                                        |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<instance_port>* | Enter the database port displayed on the **Basic Information** page. Default value: **5432**                                                                                                             |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<database_name>* | Enter the name of the database to which you intend to connect. Default value: **postgres**                                                                                                               |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | sslmode           | Enter the SSL connection mode. Default value: **verify-full**                                                                                                                                            |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | sslrootcert       | Enter the directory of the CA certificate for the SSL connection. The certificate should be stored in the directory where the command is executed.                                                       |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   Example script in Java:

   .. code-block:: text

      import java.sql.Connection;
      import java.sql.DriverManager;
      import java.sql.ResultSet;
      import java.sql.Statement;

      public class MyConnTest {
          final public static void main(String[] args) {
              Connection conn = null;
              // set sslmode here.
              // with ssl certificate and path.
             String url = "jdbc:postgresql://192.168.0.225:5432/my_db_test?sslmode=verify-full&sslrootcert=/home/Ruby/ca.pem";

              try {
                  Class.forName("org.postgresql.Driver");
                  conn = DriverManager.getConnection(url, "root", "password");
                  System.out.println("Database connected");

                  Statement stmt = conn.createStatement();
                  ResultSet rs = stmt.executeQuery("SELECT * FROM mytable WHERE columnfoo = 500");
                  while (rs.next()) {
                      System.out.println(rs.getString(1));
                  }

                  rs.close();
                  stmt.close();
                  conn.close();
              } catch (Exception e) {
                  e.printStackTrace();
                  System.out.println("Test failed");
              } finally {
                  // release resource ....
              }
          }
      }

Connection Without the SSL Certificate
--------------------------------------

.. note::

   You do not need to download the SSL certificate because the certificate verification on the server is not required.

#. Connect to the RDS PostgreSQL DB instance through JDBC.

   .. code-block::

      jdbc:postgresql://<instance_ip>:<instance_port>/<database_name>?sslmode=disable

   .. table:: **Table 2** Parameter description

      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter         | Description                                                                                                                                                                                              |
      +===================+==========================================================================================================================================================================================================+
      | *<instance_ip>*   | If you attempt to access the RDS DB instance through an ECS, set *instance_ip* to the floating IP address displayed on the **Basic Information** page of the DB instance to which you intend to connect. |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                   | If you attempt to access the RDS DB instance through an EIP, set *instance_ip* to the EIP that has been bound to the DB instance.                                                                        |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<instance_port>* | Enter the database port displayed on the **Basic Information** page. Default value: **5432**                                                                                                             |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | *<database_name>* | Enter the name of the database to which you intend to connect. Default value: **postgres**                                                                                                               |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | sslmode           | Enter the SSL connection mode. **disable** means data is not encrypted.                                                                                                                                  |
      +-------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   Example script in Java:

   .. code-block:: text

      import java.sql.Connection;
      import java.sql.DriverManager;
      import java.sql.ResultSet;
      import java.sql.Statement;

      public class MyConnTest {
          final public static void main(String[] args) {
              Connection conn = null;
              // set sslmode here.
              // no ssl certificate, so do not specify path.
           String url = "jdbc:postgresql://192.168.0.225:5432/my_db_test?sslmode=disable";
              try {
                  Class.forName("org.postgresql.Driver");
                  conn = DriverManager.getConnection(url, "root", "password");
                  System.out.println("Database connected");

                  Statement stmt = conn.createStatement();
                  ResultSet rs = stmt.executeQuery("SELECT * FROM mytable WHERE columnfoo = 500");
                  while (rs.next()) {
                      System.out.println(rs.getString(1));
                  }
                  rs.close();
                  stmt.close();
                  conn.close();
              } catch (Exception e) {
                  e.printStackTrace();
                  System.out.println("Test failed");
              } finally {
                  // release resource ....
              }
          }
      }

.. |image1| image:: /_static/images/en-us_image_0000001191131453.png
