## Basic *nextcloud* setup with docker and PostgreSQL to use behind nginx proxy

### Build

Set environmnet varibles to you're individual parameters. Then build:
- **nginxDockerProxy**:

  run in  [nginxDockerProxy](https://github.com/mka142/nginxDockerProxy/tree/5ff11be3ac11f8693f216b85a58da63b58d7cd48) directory:
  ```
  docker-compose up -d
  ```
- **nextcloudDocker**

  run in [root](../../) directory:
  ```
  docker-compose up -d
  ```
  
### Env varibles


##### Nextcloud
- NEXTCLOUD_ADMIN_USER
- NEXTCLOUD_ADMIN_PASSWORD
- NEXTCLOUD_TRUSTED_DOMAINS
- NEXTCLOUD_HOSTNAME

##### For proxy
- LETSENCRYPT_HOST
- VIRTUAL_HOST


##### Databse
- POSTGRES_USER
- POSTGRES_PASSWORD
- POSTGRES_DB

### Mobile App can't authenticate
- Install *nano* in nextcloud container
    ```
    docker exec -it [container name or ID] bash -c 'apt-get -y update && apt -y install nano'
    ```

- add this two lines at the end of your *config.php* file in *nextcloud* container
    ```
    'forcessl' => true,
    'overwriteprotocol' => 'https',
    ```

### Help Links

https://linuxhandbook.com/install-nextcloud-docker/

https://hub.docker.com/_/nextcloud/
