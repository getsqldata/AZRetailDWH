
# AZRetailDWH
An OLTP to OLAP warehouse implementation in SQL Server and SSAS. For a complete description, see my site: http://www.jlbdatasci.com/jobs/lbdwi/

# Requirements: 
1) Visual Studio 2017 with SSDT installed on server.
2) An edition of SQL server with report services available. 
3) Administrative (full control of SQL server with native login) is assumed with included settings. 

# Instructions:

# Get Files and Restore OLTP database
1) Download and unzip files. 
2) Download OLTP .bak file from: https://drive.google.com/open?id=1pWFTv9mLn7riFC9-PIQv_e3i3e77NmDq
Unzip this file and place in the backup directory of your server. Then click on the root folder in the database and select "Restore Database from Backup".  DO NOT CHANGE THE NAME OF THIS DATABASE.

# Create warehouse and stage databases
3) Run make_databases.bat by double-clicking.

# Run ETL to populate DWH

4) Open Visual Studio and open the Project ETL\InititalLoad_AZRetailDWH\InitialLoad_OnlineRetailDWH_SOL
5) Once project is loaded in Visual Studio open dtsx Load_AZRetailDWH.dtsx. Run this package.

# Test the SCD and CDC capability

6) Double-click on change_static_tables.sql to open in SSMS, or open file in Notepad, etc and copy and paste to run. This makes changes to the databases, including new orders, deleting old orders, changing a store name, and adding a new customer.
7) Test these changes and how they are applied in the DWH. Open Visual Studio 2017 again and open ETL\IncrementalLoad_AZRetailDWH\IncrementalLoadAZRetailer_SOL. Open dtsx IncrementalLoad_AZRetailDWH. You should see the new new orders and customer after running it a second time.

# Create CUBE

8) Open Cube\AZRetailDWHSSAS_SOL in Visual Studio. Once loaded, right-click on projct name and select Build. Once it is built, right click on project name and select Deploy. Finally, right-click and select Process. Boom, you have a CUBE with a backing warehouse. NOTE: This will work if you have a Report Server setup with the default SQL server. Default in this case means a server that is accessible through the . or localhost shortcut on the connection mangers.
