# MyISAM2InnoDB

Converts all MySQL tables using the MyISAM engine to InnoDB.

# Usage

Dry-run:

```
mysqldump -dAQn | myisam2innodb
```

Convert all MyISAM engines to InnoDB:

```
mysqldump -dAQn | myisam2innodb | mysql
```
