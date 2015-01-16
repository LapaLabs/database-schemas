# User table

## Column list
```
-- SHOW COLUMNS FROM user;
+------------+--------------+------+-----+---------+----------------+
| Field      | Type         | Null | Key | Default | Extra          |
+------------+--------------+------+-----+---------+----------------+
| id         | int(11)      | NO   | PRI | NULL    | auto_increment |
| email      | varchar(255) | NO   | UNI | NULL    |                |
| username   | varchar(255) | NO   | UNI | NULL    |                |
| password   | varchar(255) | NO   |     | NULL    |                |
| salt       | varchar(255) | NO   |     | NULL    |                |
| token      | varchar(255) | YES  | UNI | NULL    |                |
| enabled    | tinyint(1)   | NO   |     | NULL    |                |
| locked     | tinyint(1)   | NO   |     | NULL    |                |
| created_at | datetime     | NO   |     | NULL    |                |
| updated_at | datetime     | YES  |     | NULL    |                |
| last_login | datetime     | YES  |     | NULL    |                |
+------------+--------------+------+-----+---------+----------------+
```

## Create schema
``` sql
-- SHOW CREATE TABLE user;
CREATE TABLE `user` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `email` varchar(255) COLLATE utf8_unicode_ci NOT NULL,
  `username` varchar(255) COLLATE utf8_unicode_ci NOT NULL,
  `password` varchar(255) COLLATE utf8_unicode_ci NOT NULL,
  `salt` varchar(255) COLLATE utf8_unicode_ci NOT NULL,
  `token` varchar(255) COLLATE utf8_unicode_ci DEFAULT NULL,
  `enabled` tinyint(1) NOT NULL,
  `locked` tinyint(1) NOT NULL,
  `created_at` datetime NOT NULL,
  `updated_at` datetime DEFAULT NULL,
  `last_login` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `email_UNIQUE` (`email`),
  UNIQUE KEY `username_UNIQUE` (`username`),
  UNIQUE KEY `token_UNIQUE` (`token`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci
```

## Example with demo data
```
-- SELECT * FROM user;
+----+------------------+----------+----------------------------------+----------------------------------+----------------------------------+---------+--------+---------------------+---------------------+---------------------+
| id | email            | username | password                         | salt                             | token                            | enabled | locked | created_at          | updated_at          | last_login          |
+----+------------------+----------+----------------------------------+----------------------------------+----------------------------------+---------+--------+---------------------+---------------------+---------------------+
|  1 | admin@local.host | admin    | 25e4ee4e9229397b6b17776bfceaf8e7 | 3042d7230c565a47d72a21d39759cb3d | NULL                             |       1 |      0 | 2015-01-16 11:32:26 | 2015-01-16 11:37:51 | 2015-01-16 12:07:28 |
|  2 | user@local.host  | user     | 63e780c3f321d13109c71bf81805476e | 4a46c802b867334f41c80948272fe3b7 | 7b6e492f1a222026f8467ebeeaa3e559 |       0 |      0 | 2015-01-16 11:44:09 | NULL                | NULL                |
+----+------------------+----------+----------------------------------+----------------------------------+----------------------------------+---------+--------+---------------------+---------------------+---------------------+
```

## Demo data dump
``` sql
INSERT INTO `user` VALUES 
  (1,'admin@local.host','admin','25e4ee4e9229397b6b17776bfceaf8e7','3042d7230c565a47d72a21d39759cb3d',NULL,1,0,'2015-01-16 11:32:26','2015-01-16 11:37:51','2015-01-16 12:07:28'),
  (2,'user@local.host','user','63e780c3f321d13109c71bf81805476e','4a46c802b867334f41c80948272fe3b7','7b6e492f1a222026f8467ebeeaa3e559',0,0,'2015-01-16 11:44:09',NULL,NULL);
```
