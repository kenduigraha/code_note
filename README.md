# code_note
This repository belongs to my personal guidance note to download & install "things" that i needed in Ubuntu 16.04

# npm & node.js (Ubuntu)
Source :
[https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions)

Node.js v6 :
`curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs`

OR

Node.js v7 :
`curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash -
sudo apt-get install -y nodejs`

Install build tools :
`sudo apt-get install -y build-essential`

# zsh

Source :
[https://github.com/mhaidarh/super-zsh-kit-basic](https://github.com/mhaidarh/super-zsh-kit-basic)

# git kit basic

Source : [https://github.com/mhaidarh/super-git-kit-basic](https://github.com/mhaidarh/super-git-kit-basic)

# MongoDB (Ubuntu 16.04)

Source :
[https://docs.mongodb.com/master/tutorial/install-mongodb-on-ubuntu/?_ga=1.34925153.1562600274.1484908965](https://docs.mongodb.com/master/tutorial/install-mongodb-on-ubuntu/?_ga=1.34925153.1562600274.1484908965)

1. `sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6`

2. `echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list`

3. `sudo apt update`

4. `sudo apt-get install -y mongodb-org`

### Start
`sudo service mongod start`

### Check Log
`/var/log/mongodb/mongod.log`

### Stop
`sudo service mongod stop`

### Restart
`sudo service mongod restart`

# XAMPP
Download : [https://www.apachefriends.org/download.html](https://www.apachefriends.org/download.html)

Install : [https://www.apachefriends.org/faq_linux.html](https://www.apachefriends.org/faq_linux.html)

### Start
`sudo /opt/lampp/lampp start`

### Stop
`sudo /opt/lampp/lampp stop`

# Tree
### Install
`sudo apt install tree`

### How to use
`tree`

2 Depths
`tree -L 2`

Only folders/directories
`tree -d`

Ignore file or folder
`tree -I <file name || folder name >`

Show hidden files
`tree -a`

Run how to use tree
`man tree`

# Express.js
Source :
[http://expressjs.com/](http://expressjs.com/)

How to
#### 1. Create & go to new folder
`mkdir new_folder`
`cd new_folder`

#### 2. Npm init
`npm init`
or
`npm init -y`

#### 3. Install express
##### Generator :
`sudo npm i -g express-generator`

then

`express`
(Only if you want to install in that directory with jade template engine (default))

OR

`express --view=<name_template_engine>`

```
name_template_engine :
- ejs
- pug
- hbs
- hogan
```

then

`npm install`

then

`npm start`

check in browser :
`localhost:3000`


OR



##### Scratch :
`npm i -S express`

then

create new file name server.js or app.js and do magic there

# PostgreSQL
Source :
[https://www.postgresql.org/download/linux/ubuntu/](https://www.postgresql.org/download/linux/ubuntu/)

Install :
`sudo apt install postgresql`

## PgAdmin 4.1.1

```
sudo apt-get install virtualenv python-pip libpq-dev python-dev

cd
virtualenv pgadmin4
cd pgadmin4
source bin/activate

wget https://ftp.postgresql.org/pub/pgadmin3/pgadmin4/v1.1/pip/pgadmin4-1.1-py2-none-any.whl

pip install pgadmin4-1.1-py2-none-any.whl

gedit lib/python2.7/site-packages/pgadmin4/config_local.py

Configure

Write the following in lib/python2.7/site-packages/pgadmin4/config_local.py to configure to run in single-user mode:

SERVER_MODE = False

Create the configuration database

python lib/python2.7/site-packages/pgadmin4/setup.py

Run

python lib/python2.7/site-packages/pgadmin4/pgAdmin4.py
Access at http://localhost:5050

setting password :
http://stackoverflow.com/questions/24917832/how-connect-postgres-to-localhost-server-using-pgadmin-on-ubuntu
```

## pg

`sudo npm i -g pg`

## ORM : Sequelize
`sudo npm i -g sequelize-cli`

`sudo npm i -g sequelize`

go to your project's directory

`sequelize init`

go to pgadmin, create new database

edit config/config.json, username, password, database, dialect

example :
```
{
  "development": {
    "username": "postgres",
    "password": "postgres",
    "database": "db_user_skills",
    "host": "127.0.0.1",
    "dialect": "postgres"
  },
  "test": {
    "username": "postgres",
    "password": "postgres",
    "database": "db_user_skills",
    "host": "127.0.0.1",
    "dialect": "postgres"
  },
  "production": {
    "username": "postgres",
    "password": "postgres",
    "database": "db_user_skills",
    "host": "127.0.0.1",
    "dialect": "postgres"
  }
}

```

create new table, run in terminal

`sequelize model:create --name <table_name> --attributes "<field>:<data_type>,<field>:<data_type>,etc"`

migrate

`sequelize db:migrate`

seeders
`sequelize seed:create --name <file_seeder_name>`

edit seeder's file

example:
```javascript
'use strict';

module.exports = {
  up: function (queryInterface, Sequelize) {
    /*
      Add altering commands here.
      Return a promise to correctly handle asynchronicity.

      Example:
      return queryInterface.bulkInsert('Person', [{
        name: 'John Doe',
        isBetaMember: false
      }], {});
    */
    return queryInterface.bulkInsert('Users', [{
      username  : 'admin',
      password  : 'admin',
      email     : 'admin@admin.com',
      createdAt : new Date(),
      updatedAt : new Date()
    }])
  },

  down: function (queryInterface, Sequelize) {
    /*
      Add reverting commands here.
      Return a promise to correctly handle asynchronicity.

      Example:
      return queryInterface.bulkDelete('Person', null, {});
    */
    return queryInterface.bulkDelete('Users', null)
  }
};

```

execute the seeder
`sequelize db:seed --seed seeders/<file_seeder_name>.js`

add new field into existing table
`sequelize migration:create --name <file_new_field_name>`


edit the file_new_field_name :

example:
```javascript
'use strict';

module.exports = {
  up: function (queryInterface, Sequelize) {
    /*
      Add altering commands here.
      Return a promise to correctly handle asynchronicity.

      Example:
      return queryInterface.createTable('users', { id: Sequelize.INTEGER });
    */
    return queryInterface.addColumn('Skills', 'name', {
      type : Sequelize.STRING
    })
  },

  down: function (queryInterface, Sequelize) {
    /*
      Add reverting commands here.
      Return a promise to correctly handle asynchronicity.

      Example:
      return queryInterface.dropTable('users');
    */
    return queryInterface.removeColumn('Skills', 'name')
  }
};

```

migrate:
`sequelize db:migrate`

add FK
`sequelize migration:create --name <file_add_FK_name>`

edit file_add_FK_name
example:
```javascript
'use strict';

module.exports = {
  up: function (queryInterface, Sequelize) {
    /*
      Add altering commands here.
      Return a promise to correctly handle asynchronicity.

      Example:
      return queryInterface.createTable('users', { id: Sequelize.INTEGER });
    */
    return queryInterface.addColumn(
      'Skills',
      'UserId',
      {
        type: Sequelize.INTEGER,
        references :{
            model : 'Users',
            key: 'id'
        },
        onDelete: 'SET NULL',
        onUpdate: 'CASCADE'
      }
    )
  },

  down: function (queryInterface, Sequelize) {
    /*
      Add reverting commands here.
      Return a promise to correctly handle asynchronicity.

      Example:
      return queryInterface.dropTable('users');
    */
    return queryInterface.removeColumn('Skills','UserId')
  }
};

```

migrate:

`sequelize db:migrate`
