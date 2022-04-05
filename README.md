# Private Files Adapter

Related issue: https://github.com/digitalutsc/islandora_group/issues/4

## Download Islandora Lite playbook: 

````
composer require digitalutsc/private_files_adapter
````

**OR**

````
git clone -b islandora_lite https://github.com/digitalutsc/islandora-playbook.git islandora-lite-playbook
````

## Apply a patch for Openseadragon Viewer

* Openseadragon Viewer module: https://github.com/Islandora/openseadragon
* Run the following commands: 

````  
cd /var/www/html/drupal/web/modules/contrib/openseadragon  
wget https://raw.githubusercontent.com/digitalutsc/private_files_adapter/main/scripts/openseadragon.authentication.patch
patch -p1 < openseadragon.authentication.patch
````

## How to adjust Cantaloupe in Islandora Lite Playbook

* Copy the delegate.rb to `/opt/cantaloupe`

````
sudo cp /var/www/html/drupal/web/modules/custom/private_files_adapter/scripts/delegates.rb /opt/cantaloupe
````

* Change configuration of Cantaloupe to enable Delegate Script for Lookup 

````
sudo mv /opt/cantaloupe/cantaloupe.properties /opt/cantaloupe/cantaloupe.bk
sudo cp /var/www/html/drupal/web/modules/custom/private_files_adapter/scripts/cantaloupe.properties /opt/cantaloupe
````

* Restart Cantaloupe

````
sudo service tomcat9 restart
````

## Enable the module

```` 
git clone https://github.com/digitalutsc/private_files_adapter.git /var/www/html/drupal/web/modules/contrib/private_files_adapter
drush en -y private_files_adapter
````

## Create and set JWT keys
