# SQL Server

Microsoft SQL Server is a relational database management system developed by Microsoft.
As a database server, it is a software product with the primary function of storing and retrieving data as requested by other software applications—which may run either on the same computer or on another computer across a network (including the Internet).
Microsoft markets at least a dozen different editions of Microsoft SQL Server, aimed at different audiences and for workloads ranging from small single-machine applications to large Internet-facing applications with many concurrent users.

## Install SQL Server and create a database on Red Hat

**Notes**: for more information, visit Microsoft's documentation: https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-red-hat?view=sql-server-ver15. 

**Prerequisites**:
You must have a RHEL 7.3 - 7.8, or 8.0 - 8.3 machine with at least 2 GB of memory.

1. verify that python2 is selected as the interpreter:

```bash
# Install python2 if not installed:
sudo yum install python2
# Configure python2 as the default interpreter: 
sudo alternatives --config python
```
2. Download the Microsoft SQL Server 2019 Red Hat repository configuration file:

```bash
# For RHEL7
sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2019.repo

# For RHEL8
sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/mssql-server-2019.repo
```

3. Run the following commands to install SQL Server:

```bash
sudo yum install -y mssql-server
```

4. After the package installation finishes, run mssql-conf setup and follow the prompts to set the SA password and choose your edition.

```bash
sudo /opt/mssql/bin/mssql-conf setup
```

5. Once the configuration is done, verify that the service is running:

```bash
systemctl status mssql-server
```

6. To allow remote connections, open the SQL Server port on the firewall on RHEL. The default SQL Server port is TCP 1433. If you are using FirewallD for your firewall, you can use the following commands (**Don't use this code in aliyun server!**):

```bash
sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
sudo firewall-cmd --reload
```

## SQL Server frequently used command

**Command** `sp_helpindex`: Reports information about the indexes on a table or view.

```SQL
USE [database name]
EXEC sp_helpindex [table name]
GO
```
