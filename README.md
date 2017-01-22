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
