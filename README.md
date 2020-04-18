# wordpress-zh_cn

The latest version 5.4.0-php7.2-apache

### docker-compose

```
version: '3.1'
services:
  db:
    image: mysql:5.7
    volumes:
      - ./mysql/data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: 123456
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: 111111

  wordpress:
    depends_on:
      - db
    image: catcto/wordpress-zh_cn
    volumes:
      - ./html:/var/www/html
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: 111111
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_CONFIG_EXTRA: |
        /* Multisite */
        define('WPLANG', 'zh_CN');

```
