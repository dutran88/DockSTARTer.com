# Bitwarden

[Bitwarden](https://bitwarden.com/) is a free and open-source password management service that stores sensitive information such as website credentials in an encrypted vault. This is a Bitwarden server API implementation written in Rust compatible with [upstream Bitwarden clients](https://bitwarden.com/#download), perfect for self-hosted deployment where running the official resource-heavy service might not be ideal.

The GIT Repository for Bitwarden is located at [https://github.com/dani-garcia/bitwarden_rs](https://github.com/dani-garcia/bitwarden_rs)

Bitwarden Install

When installing the Bitwarden container, the installer will install under Appdata directory as the root user, however once it is installed you can change the owner/group of it to whatever is required

Run the below command (from a terminal) to change the permissions if required.

`sudo chown -R owner:group ~/.config/appdata/bitwarden`

Having the owner group change will allow you to edit the files if required without running into permission issues.

## Using MariaDB for your database instead of the self container

Great way to go about this would be installing phpmyadmin and MariaDB from the selected docker apps. 

![Sudo DS](https://i.ibb.co/yh3ppPR/screenshot-of-mariadb-and-phpmyadmin.png)

By default, MariaDB and PhpMyAdmin is already linked together. So go ahead and open your PhpMyAdmin portal

Once on the PhPMyAdmin Portal. Create a new database and user for your bitwarden account. 

![PhpMyAdmin_Portal](https://i.ibb.co/LhkFS9p/phpmyadmin-db-creation.png)

If that's seems too long, I find it easy to create users and databases is to run ``` docker exec ``` command

On your DockStarter terminal; type in the command below to connect to your container. Once there, use ``` mysql ``` command and database username and password. 

```bash
DockStarter@192.168.2.1:~$ docker exec -it mariadb bash
```

```bash
# if you didnt set a root password inside your enviorment file, then just hit return.
root@192.168.1.1:/# mysql --user=root --password="somepassword"
```
If you see the message below, continue on and create your bitwarden database and user

```sql
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 1163
Server version: 10.4.11-MariaDB-1:10.4.11+maria~bionic-log mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

# input these commands

MariaDB [(none)]> CREATE DATABASE 'bitwarden_db';

# do not forget to replay "bitwarden_password" with your own!!

MariaDB [(none)]> CREATE USER 'bitwarden_user' IDENTIFIED BY 'bitwarden_password';

# Grant permission to acess and use the MariaDB server to localhost. Below is the most secure and common configuration. 

MariaDB [(none)]> GRANT USAGE ON *.* TO 'bitwarden_user'@192.168.1.1 IDENTIFIED BY 'bitwarden_password';

# Grant all privileges to bitwarden_user to access bitwarden_db: 

MariaDB [(none)]> GRANT ALL privileges ON `bitwarden_db:`.* TO 'bitwarden_user'@192.168.1.1 ;

MariaDB [(none)]> FLUSH PRIVILEGES;
```
VERIFY and Database

```sql
MariaDB [(none)]> SHOW GRANTS FOR 'bitwarden_user'@192.168.1.1;
+-----------------------------------------------------------------------------------------------------------------------------------------+
| Grants for bitwarden-usr@%                                                                                                              |
+-----------------------------------------------------------------------------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'bitwarden-user'@'%' IDENTIFIED BY PASSWORD '*10101010111001010101' WITH GRANT OPTION |
| GRANT ALL PRIVILEGES ON `bitwarden_db`.* TO 'bitwarden-user'@'192.168.1.1'                                                                            |
+-----------------------------------------------------------------------------------------------------------------------------------------+
2 rows in set (0.000 sec)

MariaDB [(none)]> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| bitwarden_db       |
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
5 rows in set (0.001 sec)
```
Finally create an Override file: 

```yaml
version: "3.4"  # this must match the version in docker-compose.yml
services:
  bitwarden:
    environment:
    - DATABASE_URL=mysql://BITWARDEN_USER:BITWARDEN_PASSWORD@mariadb/BITWARDEN_DB # Remember to replace with your own configuration
    - ENABLE_DB_WAL=false
    image: bitwardenrs/server-mysql
```

Save and run ``` ds -c ```

