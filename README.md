# ibd_analyst_db
workflow to get access to IBD  db

# Adminstrator Options
1. Install UnixODBC, which is required for all databases on workstation with db `sudo apt-get install unixodbc unixodbc-dev --install-suggests`
2. Install PostgreSQL ODBC ODBC Drivers on workstation with db that users will connect from `sudo apt-get install odbc-postgresql`
3. Apply the template file provided to setup driver odbcinst.ini file `sudo odbcinst -i -d -f /usr/share/psqlodbc/odbcinst.ini.template`
4. Apply the template file provided to setup datasource odbc.ini file for all users on system `sudo odbcinst -i -s -l  -n ibd-pg -f /usr/share/doc/odbc-postgresql/examples/odbc.ini.template`
5. Modify the SYSTEM DATA SOURCES: /etc/odbc.ini to match db settings. This file should be filled with the details corresponding to the Role for all database users (e.g. ibd_analyst) `sudo nano /etc/odbc.ini`
6. Apply the template file provided to setup datasource odbc.ini file for admin user `cp /usr/share/doc/odbc-postgresql/examples/odbc.ini.template /home/[NAME]/.odbc.ini`
7. Modify the USER DATA SOURCES: /home/name/.odbc.ini to match db settings. This file should be filled with the details corresponding to the Role for the database adminstrator. `sudo nano /home/[NAME]/.odbc.ini`

# Analyst Start-Up
1. In RSTUDIO install the DBI and odbc package. You only need to do this once. `install.packages("DBI")` `install.packages("odbc")`
2. Load the DBI and odbc package `library(DBI)` `library(odbc)`
3. Run `odbcListDataSources()` to see if you have avaialble DSNs. You should see something like <pre>                    name     description
1 PostgreSQL ibd_analyst PostgreSQL ANSI </pre> If you do great! If not, contact an admin. 
4. Navigate to the connection pane in Rstudio (shared with your Environment), click "New Connection" and select DSN `PostgreSQL ibd_analyst` 
5. In R terminal or script, create a connection object that you can use to query the database `con <- dbConnect(odbc::odbc(), "PostgreSQL ibd_analyst")`
