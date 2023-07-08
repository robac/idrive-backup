# idrive
  * Clone of https://github.com/RenoFischa/idrive.git
  * ARM64v8/ubuntu base image

## Requirements
* Docker installed
* IDrive account

## docker-compose example
````
services:
  idrive:
    container_name: idrive
    image: renofischa/idrive:latest
    restart: unless-stopped
    volumes:
      - config:/work/IDriveForLinux/idriveIt
      - dependencies:/work/IDriveForLinux/scripts/Idrivelib/dependencies
      - files:/mnt/files
      - $BACKUPDIR:/mnt/backup:ro
    environment:
      - TZ=$TZ
      
volumes:
  config:
  dependencies:
  files:
````
* volumes config, dependencies and files are necessary for persisting account settings and IDrive services.
* $BACKUPDIR points to the local path you need to backup
* Optional timezone environment variable, default is set to Europe/Vienna in dockerfile


## Configuration after first start
Configure your IDrive account after first start.
* Exec into container
* Run ````./account_setting.pl````
* Login with your account details and configure other basic settings. Important is your Backup location.
* Now you should see your container in your IDrive dashboard.
