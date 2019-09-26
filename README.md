# Magento 2 Docker Images
___

Enhanced Docker images for Magento 2 development.

These two images are based in the [magento-cloud-docker images](https://github.com/magento-dockerhub/magento-cloud-docker).

### Use

1. Install docker and docker-compose.

2. Create a docker-compose.yml file in your project folder based on the following content:

```
version: '3.1'
services:
  web:
    image: mariohd/magento2-nginx
    container_name: magento2-nginx
    restart: always
    ports:
      - 80:80
    environment:
      - MAGENTO_RUN_MODE=developer
    volumes:
      - ./app:/app
    links:
      - fpm
  fpm:
    image: mariohd/magento2-php-fpm
    container_name: magento2
    restart: always
    volumes:
      - ./app:/app

```

3. Run `docker-compose up -d`

4. You can access to the php-fpm container to run Magento cli commands by running `docker exec -it magento2 bash`

5. Don't forget to use the Magento file system owner using `su magento2`



This will prepare your php-fpm and nginx environment that fullfill all the [Magento 2 prerequisites](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/prereq-overview.html).

Then you can continue the Magento installation guide from the [Get Magento software section](https://devdocs.magento.com/guides/v2.3/install-gde/install/get-software.html).

### Differences with the default magento-cloud-docker images

**PHP**

Includes composer and creates the magento2 user

**NGINX**

Fixes setup and updates configuration in nginx default.conf

___

**Tested for Magento 2.3.2**