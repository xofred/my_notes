**Connect To The Database Server**

Connect to the database using the MySQL client:
```shell
mysql -u root -p
```
Enter your root password set at the previous step:
```
# Enter password:
# ..
# .
mysql>
```
**Create A New Database**
Let's begin with creating a default database for our Rails application.

Run the following command to create a new MySQL database:
```
# Usage: create database [database_name];
# Example:
create database rails_myapp;
```
**Create A New Database User**

For reasons of security, let's now create a database user for Rails application to use that will have remote access.

Add the new user with both local and remote access:
```
# Usage:
# CREATE USER '[user name]'@'localhost' IDENTIFIED BY '[password]';
# CREATE USER '[user name]'@'%' IDENTIFIED BY '[password]'; 
# Example:
CREATE USER 'rails_myapp_user'@'localhost' IDENTIFIED BY 'pwd';
CREATE USER 'rails_myapp_user'@'%' IDENTIFIED BY 'pwd';
```
To verify that the users have been created, run the following:
```
SELECT User,host FROM mysql.user;

# Example:
# +------------------+-----------+
# | User             | host      |
# +------------------+-----------+
# | rails_myapp_user | %         |
# | root             | 127.0.0.1 |
# | rails_myapp_user | localhost |
# | root             | localhost |
# +------------------+-----------+ 
```
**Granting Privileges**

Run the following commands to grant privileges to a specific user:
```
# Usage:
# GRANT ALL ON [database name].* TO '[user name]'@'localhost';
# GRANT ALL ON [database name].* TO '[user name]'@'%';
# Example:
GRANT ALL ON rails_myapp.* TO 'rails_myapp_user'@'localhost';
GRANT ALL ON rails_myapp.* TO 'rails_myapp_user'@'%';
```

Reference: [Scaling Ruby on Rails: Setting Up A Dedicated MySQL Server (part 2) | DigitalOcean](https://www.digitalocean.com/community/tutorials/scaling-ruby-on-rails-setting-up-a-dedicated-mysql-server-part-2)