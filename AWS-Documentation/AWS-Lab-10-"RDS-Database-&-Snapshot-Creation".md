# AWS RDS Database & Snapshot Creation with MySQL & PostgreSQL

### Step 1
Create a subnet group `rds-sbntgrp-010926`. Provide name, description, choose a VPC, and under VPC select the availability zones and public subnets.

<img width="1110" height="1001" alt="RDS-A-sbntgrp-01" src="https://github.com/user-attachments/assets/3043a21e-0012-4ce2-b51f-f398fc0c38a5" />

<img width="1133" height="1045" alt="RDS-A-sbntgrp-02" src="https://github.com/user-attachments/assets/8e8b87ec-aca7-47c4-9389-42b8fa9f7c95" />


### Step 2
Similarly, create parameter groups for two separate databases with MySQL and PostgreSQL engine types respectively. Provide a name, description, select preferred engine type, parameter group family and click create.

<img width="1131" height="340" alt="RDS-B00-pmtrgrp-01" src="https://github.com/user-attachments/assets/36564032-3cb7-4d23-9a6e-5eca31a3dec2" />

<img width="1126" height="609" alt="RDS-B01-pmtrgrp-02-mysql" src="https://github.com/user-attachments/assets/34d406c2-9d42-42ff-8a5b-0af615fb813f" />

<img width="1126" height="605" alt="RDS-B02-pmtrgrp-03-pgsql" src="https://github.com/user-attachments/assets/7e4f9a0e-520e-42de-98a8-010747b69ac3" />


### Step 3
Now, create a database `database-mysql-010926`, with MySQL as engine type. Select MySQL, Single AZ DB as deployment option, engine latest version, instance identifier. Master username and configure password to be self-managed and auto-generated. Select `m5.large` as instance type, `gp3` as storage type, IPV4 as network type and choose the VPC.

Select the subnet group created, grant public access, choose to create new security and provide a name for it. Then enable enhanced monitoring, select all options under log exports, and under Additional Configuration, provide an initial name for the database and choose the parameter group created for MySQL, then click create database.

<img width="1133" height="1045" alt="RDS-C00-database-01" src="https://github.com/user-attachments/assets/cb3c3bf2-c064-4ff3-9cfe-cd71b4250c61" />

<img width="1133" height="1045" alt="RDS-C01-database-02-mysql" src="https://github.com/user-attachments/assets/d141fbd7-a0ff-4a74-952e-c837807916cc" />

<img width="1133" height="1045" alt="RDS-C01-database-03-mysql" src="https://github.com/user-attachments/assets/9e0c3d83-8afa-4575-854d-812f9393fc7f" />

<img width="1133" height="1045" alt="RDS-C01-database-04-mysql png" src="https://github.com/user-attachments/assets/f0eb8127-42ff-4a93-8869-5294f7f107be" />

<img width="1133" height="1045" alt="RDS-C01-database-05-mysql" src="https://github.com/user-attachments/assets/fb88edba-c5de-483e-aaa6-93bcfe375b27" />

<img width="1133" height="1045" alt="RDS-C01-database-06-mysql" src="https://github.com/user-attachments/assets/abeff4e4-860c-4a56-9837-d30546aeb99f" />

<img width="1133" height="1045" alt="RDS-C01-database-07-mysql" src="https://github.com/user-attachments/assets/e409d7f0-2317-467f-8e5e-9b88858a405d" />

<img width="1111" height="869" alt="RDS-C01-database-08-mysql" src="https://github.com/user-attachments/assets/4b358f67-1626-4e66-8084-cd9f52355331" />


### Step 4
For PostgreSQL, similarly, select PostgreSQL as engine type and latest engine version. For the security group, create a new one and wherever name is needed, similarly provide unique names. Then when needed, select the parameter group created for PostgreSQL. Rest are same with MySQL database creation. Click create database.

<img width="1133" height="1045" alt="RDS-C00-database-01" src="https://github.com/user-attachments/assets/1c5f3ea2-434b-4897-9c86-40d62a901101" />

<img width="1133" height="1045" alt="RDS-C02-database-09-pgsql" src="https://github.com/user-attachments/assets/13c3c0d8-1deb-452e-a67f-80932b67a5e7" />

<img width="1133" height="1045" alt="RDS-C02-database-10-pgsql" src="https://github.com/user-attachments/assets/781f63ef-972d-46f3-bbae-1f5162d33ff8" />

<img width="1133" height="1045" alt="RDS-C02-database-11-pgsql" src="https://github.com/user-attachments/assets/03400f8c-4a5e-49df-9c7c-8be6bab6cd26" />

<img width="1133" height="1045" alt="RDS-C02-database-12-pgsql" src="https://github.com/user-attachments/assets/fa8bc60d-a963-4216-aa9e-8a135869e290" />

<img width="1133" height="1045" alt="RDS-C02-database-13-pgsql" src="https://github.com/user-attachments/assets/cbcad733-3b8f-4d81-ab19-31efe20a3d69" />

<img width="1084" height="446" alt="RDS-C02-database-14-pgsql" src="https://github.com/user-attachments/assets/048ff01f-38a6-4206-9865-ca4a19aa9d2b" />


### Step 5
Under each database created respectively, edit the inbound rules with changing the source as “anywhere IPV4” and select Endpoint under “Connect using” heading in Connectivity & Security settings, again for both the databases. Copy Master username, port number, database name and endpoint respectively for both databases.

Also, after databases are created, the notifications show an “open to details” option, click it and can copy the endpoint, Master username and password, but it's one time only.

<img width="1133" height="1045" alt="RDS-D01-mysql-01-secgrp" src="https://github.com/user-attachments/assets/bd853601-7a5b-46c9-baf7-4a48d9614772" />

<img width="1119" height="263" alt="RDS-D01-mysql-02-secgrp" src="https://github.com/user-attachments/assets/5ad804f0-858e-464a-8999-7ac3e22f7225" />

<img width="1133" height="1045" alt="RDS-D01-mysql-03-endpt" src="https://github.com/user-attachments/assets/81d5de65-c6b3-47d4-a48a-72d720037d16" />

<img width="1133" height="1045" alt="RDS-D02-pgsql-01-secgrp" src="https://github.com/user-attachments/assets/f37caaaf-515c-4a51-8d16-ebb4a628637a" />

<img width="1126" height="262" alt="RDS-D02-pgsql-02-secgrp" src="https://github.com/user-attachments/assets/d9974cf0-ae1b-448f-8d51-65708905a29e" />

<img width="1133" height="1045" alt="RDS-D02-pgsql-03-endpt" src="https://github.com/user-attachments/assets/a64e4c90-2905-4301-8fd9-eefeb06321f3" />


### Step 6
Provide the details copied from the databases to the TablePlus software installed and click test then connect for each database created with engine types MySQL and PostgreSQL respectively.

### Step 7
Taking a backup / Snapshot is a similar process for both the databases. Select database, click “Actions”, under it click “Take Snapshot”. Inside the Snapshot tab, select the database, provide a Snapshot name and click create Snapshot.
