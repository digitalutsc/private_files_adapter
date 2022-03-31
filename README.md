# Private Files Adapter

## Download Islandora Lite playbook: 

````
git clone -b islandora_lite https://github.com/digitalutsc/islandora-playbook.git islandora-lite-playbook
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
