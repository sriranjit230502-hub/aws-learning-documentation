# AWS RDS Database & Snapshot Creation with MySQL & PostgreSQL

### Step 1
Create a subnet group `rds-sbntgrp-010926`. Provide name, description, choose a VPC, and under VPC select the availability zones and public subnets.

### Step 2
Similarly, create parameter groups for two separate databases with MySQL and PostgreSQL engine types respectively. Provide a name, description, select preferred engine type, parameter group family and click create.

### Step 3
Now, create a database `database-mysql-010926`, with MySQL as engine type. Select MySQL, Single AZ DB as deployment option, engine latest version, instance identifier. Master username and configure password to be self-managed and auto-generated. Select `m5.large` as instance type, `gp3` as storage type, IPV4 as network type and choose the VPC.

Select the subnet group created, grant public access, choose to create new security and provide a name for it. Then enable enhanced monitoring, select all options under log exports, and under Additional Configuration, provide an initial name for the database and choose the parameter group created for MySQL, then click create database.

### Step 4
For PostgreSQL, similarly, select PostgreSQL as engine type and latest engine version. For the security group, create a new one and wherever name is needed, similarly provide unique names. Then when needed, select the parameter group created for PostgreSQL. Rest are same with MySQL database creation. Click create database.

### Step 5
Under each database created respectively, edit the inbound rules with changing the source as “anywhere IPV4” and select Endpoint under “Connect using” heading in Connectivity & Security settings, again for both the databases. Copy Master username, port number, database name and endpoint respectively for both databases.

Also, after databases are created, the notifications show an “open to details” option, click it and can copy the endpoint, Master username and password, but it's one time only.

### Step 6
Provide the details copied from the databases to the TablePlus software installed and click test then connect for each database created with engine types MySQL and PostgreSQL respectively.

### Step 7
Taking a backup / Snapshot is a similar process for both the databases. Select database, click “Actions”, under it click “Take Snapshot”. Inside the Snapshot tab, select the database, provide a Snapshot name and click create Snapshot.
