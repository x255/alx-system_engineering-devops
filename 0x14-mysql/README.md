# `MySQL Master-Slave Replication`

- MySQL replication is a process that enables data from one MySQL database server (the master) to be copied automatically to one or more MySQL database servers (the slaves).
- It is usually used to spread read access on multiple servers for scalability, although it can also be used for other purposes such as for failover, or analyzing data on the slave in order not to overload the master.

![](https://bs-uploads.toptal.io/blackfish-uploads/components/blog_post_page/content/cover_image_file/cover_image/1279580/retina_1708x683_staging.toptal.net_mysql_mysql-master-slave-replication-tutorial-c4941d5e44de507b5850d42c138eddc0.png)




#!/usr/bin/env bash
# backup and compress my databases

# Variables
day=$(date +"%d")
month=$(date +"%m")
year=$(date +"%Y")
file_name="$day-$month-$year.tar.gz"

# Dump databases to backup.sql
mysqldump --all-databases -u root --password="$1" > backup.sql

# Compress backup.sql to a tarball
tar -czvf "$file_name" backup.sql

# Remove the backup.sql file
rm backup.sql