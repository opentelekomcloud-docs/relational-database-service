:original_name: rds_faq_0059.html

.. _rds_faq_0059:

How Can I Obtain Microsoft SQL Server Error Logs Using Commands?
================================================================

#. Log in to the Microsoft SQL Server client as user **rdsuser**.

#. Run the following statement to query error logs:

   **EXECUTE master.dbo.rds_read_errorlog** *FileID*,\ *LogType*,\ *FilterText,FilterBeginTime,FilterEndTime*

   -  *FileID*: indicates the ID of an error log. The value **0** indicates the latest logs.
   -  *LogType*: indicates the log type. The value **1** indicates error logs and value **2** indicates agent logs.
   -  *FilterText*: indicates a keyword, which can be **NULL**.
   -  *FilterBeginTime*: indicates the start time in queries, which can be **NULL**.
   -  *FilterEndTime*: indicates the completion time in queries, which can be **NULL**.

   Example:

   **EXEC master.dbo.rds_read_errorlog 0,1,'FZYUN','2018-06-14 14:30',\ '2018-06-14 14:31'**

   :ref:`Figure 1 <rds_faq_0059__f84f34c123aa54ed78685e291aea78a31>` shows the query results.

   .. _rds_faq_0059__f84f34c123aa54ed78685e291aea78a31:

   .. figure:: /_static/images/en-us_image_0000001469940677.png
      :alt: **Figure 1** Example query results

      **Figure 1** Example query results
