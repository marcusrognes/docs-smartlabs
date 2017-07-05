---
title: MongoDB
permalink: /docs/mongodb/
---

##MongoDB

### Export
```bash
mongodump --host <mongodburl / ip> -d <dbname> --port <port> -u <username>  -p <password> --out <output directory>
```

### Import
```bash
mongorestore --host <mongodburl / ip> --port <port> -u <if applicable:username>  -p <if applicable:password> --db <db to import to> <<Output directory>/<DB to import from>>
```

