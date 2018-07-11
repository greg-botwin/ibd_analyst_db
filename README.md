# ibd_analyst_db
workflow to get access to IBD analyst db

# Adminstrator Options
1. Install UnixODBC, which is required for all databases `sudo apt-get install unixodbc unixodbc-dev --install-suggests`
2. Install PostgreSQL ODBC ODBC Drivers `sudo apt-get install odbc-postgresql`
3. Apply the template file provided to setup driver odbcinst.ini file `sudo odbcinst -i -d -f /usr/share/psqlodbc/odbcinst.ini.template`
4. Apply the template file provided to setup datasource odbc.ini file`sudo odbcinst -i -s -l  -n ibd-pg -f /usr/share/doc/odbc-postgresql/examples/odbc.ini.template`
5. Modify the obdc.ini to match db settings. 
