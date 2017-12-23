# My Personal Docs

This is for all my tips, snippets, and gotchas

## Dokku

#### Pre/Post Deploy scripts

```
{
  "scripts": {
    "dokku": {
      "predeploy": "sputnik --name spacy --repository-url http://index.spacy.io install en==1.1.0"
    }
  }
}
```

#### Notes
  * Use Procfile for processes
  * Use requirements.txt for python dependencies
  * Use nltk.txt for NLTK downloads
  * Use apt-packages for installs via apt-get

## Postgres

#### Dump

```
pg_dump --host=aa1xsbm3n9zfguj.c9hgttwrfmsn.us-west-1.rds.amazonaws.com --port=5432 --username=trivianote --password --dbname=ebdb --no-owner --no-privileges --no-acl -Fc > backup-production-2017-12-22.dump
```
  * -Fc is for custom format, which allows the .dump file type

#### Restore

```
pg_restore --verbose --exit-on-error --single-transaction --host=localhost --port=5432 --username=josh --dbname=test --no-owner ./backup-production-2017-12-22.dump
```

## Procfile

web: bundle exec puma -C config/puma.rb
web2: gunicorn --config config/gunicorn.py application:app

## Python

#### Notes
  * Keep config files like gunicorn.py out of the root directory, because it will cause errors when running commands like "gunicorn app:app"