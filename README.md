# MyISAM2InnoDB

Converts all MySQL tables using the MyISAM engine to InnoDB.

# Usage for the impatient

```
mysqldump -dAQn | myisam2innodb | mysql
```

# Safer usage

Dry-run:

```
mysqldump -dAQn | myisam2innodb > convert.sql
```

Review:
```
$EDITOR convert.sql
```

Convert all MyISAM engines to InnoDB:
```
mysql < convert.sql
```
