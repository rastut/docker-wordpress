#Docker Nginix+PHP-FPM+Wordpress


In order to set up the environment, you need to install `docker` and `docker-compose`. You would need a database and configure it on the folder webfiles/wordpress/wp-config.php. You can copy the sample `wp-config-sample.php` and change the name, user and password for the database.

After the database has been setup you can turn it on, using docker-compose on the root path.

`docker-compose up -d`

This will setup a nginx container(the official one) with a php-fpm container(one that will be build using a dockerfile), linked internally inorder for communicate one with the other. The nginx server will be binded to the 80 host port. 
