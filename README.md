# api-config


## sample
```
# /opt/settings/config.py
DATABASE_CONFIG = {
    'host': 'localhost',
    'dbname': 'company',
    'user': 'user',
    'password': 'password',
    'port': 3306
}

# main.py
import sys
import pymysql

sys.path.append('/opt/settings')
import config

def connect_db(dbname):
    if dbname != config.DATABASE_CONFIG['dbname']:
        raise ValueError("Couldn't not find DB with given name")
    conn = pymysql.connect(host=config.DATABASE_CONFIG['host'],
                           user=config.DATABASE_CONFIG['user'],
                           password=config.DATABASE_CONFIG['password'],
                           db=config.DATABASE_CONFIG['dbname'])
    return conn

connect_db('company')
```


## 프로비저닝 스크립트
```
cd /opt/settings
git clone git@github.com/company/config.git

cd /opt/app
git clone git@github.com/company/api-server.git
```

* ref: https://mingrammer.com/ways-to-manage-the-configuration-in-python/
