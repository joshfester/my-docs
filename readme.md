# Postgres

### Dump and Restore

```
pg_dump --host=aa1xsbm3n9zfguj.c9hgttwrfmsn.us-west-1.rds.amazonaws.com --port=5432 --username=trivianote --password --dbname=ebdb --no-owner --no-privileges --no-acl -Fc > backup-production-2017-12-22.dump
```
..* -Fc is for custom format, which allows the .dump file type


```
pg_restore --verbose --exit-on-error --single-transaction --host=localhost --port=5432 --username=josh --dbname=test --no-owner ./backup-production-2017-12-22.dump
```

# Procfile

web: bundle exec puma -C config/puma.rb
web: gunicorn --config config/gunicorn.py application:app