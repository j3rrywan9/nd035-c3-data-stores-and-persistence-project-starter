# Database Setup

## MySQL

### Server and Adminer

#### Docker Compose

```
docker-compose up

docker-compose ps

docker-compose down
```

### Client

Connect to `critter_db_1` as `root` using `example` as password:
```
docker run -it --network critter_default --rm mysql:8.0 mysql -h critter_db_1 -u root -pexample
```

Create user `finley` and grant all privileges:
```sql
create user 'finley'@'localhost' identified by 'password';

grant all on *.* to 'finley'@'localhost' with grant option;

create user 'finley'@'%' identified by 'password';

grant all on *.* to 'finley'@'%' with grant option;
```

Create database `critterdb`:
```sql
create database critterdb;

show databases;
```

Connect to `critter_db_1` as `finley` using `password` as password:
```
docker run -it --network critter_default --rm mysql:8.0 mysql -h critter_db_1 -u finley -ppassword

use critterdb;

select database from dual;
```

## H2

## References

* [MySQL CREATE USER Statement](https://dev.mysql.com/doc/refman/8.0/en/create-user.html)
* [MySQL GRANT Statement](https://dev.mysql.com/doc/refman/8.0/en/grant.html)
* [MySQL CREATE DATABASE Statement](https://dev.mysql.com/doc/refman/8.0/en/create-database.html)
