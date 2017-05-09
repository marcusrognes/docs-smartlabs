---
title: Heroku scripts
permalink: /docs/heroku-scripts/
---
## Base heroku
### Setup project
```bash
heroku git:remote -a app-name
```

### Push to live
```bash
git push heroku master
```

## Postgres
### Create backup
```bash
heroku pg:backups:capture --app app-name
```

### Cancel backup
```bash
heroku pg:backups:cancel
```

### Download backup
```bash
heroku pg:backups:download
```

### Import to local db (NOT HEROKU)
```bash
pg_restore --verbose --clean --no-acl --no-owner -h localhost -U root -d database-name file-to-import
```
