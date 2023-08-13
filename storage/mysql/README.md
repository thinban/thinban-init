## 集群部署
### 集群验证
```
## master
docker exec -ti mysql-master bash
mysql -uroot -p123456
CREATE DATABASE `sync-data`;
USE `sync-data`;
CREATE TABLE `sync-data`(
id INT(10) AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(20) NOT NULL DEFAULT '' COMMENT '名称'
) ENGINE=INNODB;
INSERT INTO `sync-data`(`name`) VALUES('zhangsan'),('lisi');


## slave
docker exec -ti mysql-slave1 bash
mysql -uroot -p123456
SELECT * FROM `sync-data`.`sync-data`;

```