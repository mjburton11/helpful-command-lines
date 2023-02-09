# helpful-command-lines

## git

* remove all branchs not on remote 
```bash
git fetch -p && git branch -vv | grep ': gone]' | awk '{print $1}' | xargs git branch -D
```

## docker

* remove all images and containers
  * kill containers `docker kill $(docker ps -q)`
  * remove containers `docker rm $(docker ps -a -q)`
  * remove images `docker rmi $(docker images -q)`

## wifi

* http://captive.apple.com

## macOS

* copy heic to jpg 
```bash
for i in *.HEIC(:r) ; sips -s format jpeg "$i.HEIC" --out "$i.jpg"
```

## postgres

* db table size
```sql
SELECT
    table_name,
    pg_size_pretty(table_size) AS table_size,
    pg_size_pretty(indexes_size) AS indexes_size,
    pg_size_pretty(total_size) AS total_size
FROM (
    SELECT
        table_name,
        pg_table_size(table_name) AS table_size,
        pg_indexes_size(table_name) AS indexes_size,
        pg_total_relation_size(table_name) AS total_size
    FROM (
        SELECT ('"' || table_schema || '"."' || table_name || '"') AS table_name
        FROM information_schema.tables
    ) AS all_tables
    ORDER BY total_size DESC
) AS pretty_sizes;
```
