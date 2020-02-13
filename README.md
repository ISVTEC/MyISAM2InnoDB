With recent versions of MySQL, you can convert all MyISAM tables with:

```
#!/bin/bash

set -e -o pipefail -o nounset

readonly mysql='mysql --defaults-file=/etc/mysql/debian.cnf -A'

$mysql "$db" -se "SELECT table_schema, table_name
FROM INFORMATION_SCHEMA.TABLES
WHERE engine = 'myisam'" | while read -r db table
do
  echo "$db / $table"
  echo "ALTER TABLE \`$db\`.\`$table\` ENGINE=InnoDB;" | $mysql "$db"
done
```


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
