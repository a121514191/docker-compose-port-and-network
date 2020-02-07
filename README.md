# docker-compose-lamp use port

## 延續上次的CI專案 嘗試使用port 多開檔案

將設定好port的compose丟入

```
version: '3.3'

services:
  phpapache:
    build: ./php
    ports:
      - "80:80"
      - "443:443"
    depends_on:
      - mysql
    volumes:
      - /c/Users/Default/test001/www/ngbc:/var/www/html
  phpapache2:
    build: ./php
    ports:
      - "8888:80"
    depends_on:
      - mysql
    volumes:
      - /c/Users/Default/test001/www/bogo:/var/www/html      
  mysql:
    build: ./mysql
    ports:
      - "3306:3306"
    volumes:
      - ./mysql/data:/var/lib/mysql
    environment:
      MYSQL_USERNAME: titan
      MYSQL_PASSWORD: password
      MYSQL_ROOT_PASSWORD: 123456
      #MYSQL_DATABASE: testdb
  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    ports:
      - "8080:80"
    depends_on:
      - mysql
    environment:
      PMA_HOST: mysql
      PMA_PORT: 3306
```
修改port`


