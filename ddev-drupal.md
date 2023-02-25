## How to install New Drupal project using DDEV? ##

To install new drupal project follow these steps:

- Install DDEV by following the instructions for your operating system on the DDEV website (https://ddev.readthedocs.io/en/stable/).
- Open a terminal window and navigate to the directory where you want to create your new Drupal website.
- Run the ddev config command to generate a new configuration file for your project. You will be prompted to answer a series of questions about your project, including the project name, web server type, and PHP version.

  Example: **ddev config**
  
  Or You can mention required arguements along with ddev config command.
  
  Example:
  
  **ddev config --project-type=drupal9 --docroot=web --project-name=my-site --webserver-type=apache-fpm --php-version=7.4**
  
  **Note:** If you want to install drupal in root dir(without web folder) you can add use like that **--docroot=.**
  
- After running ddev config, you should see a new file called **.ddev/config.yaml** in your project directory. Open this file in a text editor if you want to update something like port, version & hooks. So you can update accoring to requirement.
- Run the **ddev start** command to start your DDEV environment. This command will create and start the necessary containers for your Drupal website.
- Now run following commands
```
ddev composer create drupal/recommended-project
ddev composer require drush/drush
ddev drush site:install --account-name=admin --account-pass=admin -y
ddev drush uli
ddev launch
```
- You can use the ddev describe command to get information about your site, including the URL you can use to access it in your web browser. 
Example: **ddev describe**

If you face any issue [follow this official doc of DDEV](https://ddev.readthedocs.io/en/stable/users/quickstart/#drupal).

## How to migrate an existing Drupal project into DDEV? ##

To migrate existing drupal project follow below steps:

- Copy your existing Drupal project into a new directory on your local machine or navigate to your existing drupal project or clone repo . This directory will be the root directory for your DDEV project than Open a terminal window and navigate to the root directory of your DDEV project.
- Run the ddev config command to generate a new configuration file for your project. You will be prompted to answer a series of questions about your project, including the project name, web server type, and PHP version.

  Example: **ddev config**
  
  ![DDEV Config](/images/ddev-config.png)
  
  Or You can mention required arguements along with ddev config command.
  
  Example:
  
  **ddev config --project-type=drupal9 --docroot=web --project-name=my-site --webserver-type=apache-fpm --php-version=7.4**
  
  **Note:** If you want to install drupal in root dir(without web folder) you can add use like that **--docroot=.**

   ![DDEV Config](/images/ddev-config1.png)
   
- If you want to add additional add-ons or services [follow this official doc](https://ddev.readthedocs.io/en/latest/users/extend/additional-services/).

- After running ddev config, you should see a new file called **.ddev/config.yaml** in your project directory. Open this file in a text editor if you want to update something like port, version & hooks. So you can update accoring to requirement.
```
hooks:
  post-start:
    - exec: composer install
  post-db-import:
    - exec: drush cr
```
These lines tell DDEV to run composer install after starting the containers, and to run drush cr after importing the database. This will ensure that your Drupal site is set up correctly.

- You will need to export the database from your existing drupal site and import it into your DDEV environment. To do this, first export the database from your existing site using a tool like phpMyAdmin or the command line. Save the database export file to a location you can access from your DDEV environment.

**Note:** Clear your cache before exporting your database. This will help you save more space.

- In your DDEV environment, run the ddev import-db command to import the database into your site.

  Example: **ddev import-db --src=/path/to/your/drupal-db.sql or drupal-db.sql.gz**
  
   ![DDEV db import](/images/ddev-db-import-ss.png)
  
- Run the **ddev start** command to start your DDEV environment. This command will create and start the necessary containers for your Drupal website.
  
- You can use the **ddev describe** command to get information about your site, including the URL you can use to access it in your web browser.

   ![DDEV describe](/images/ddev-describe.png)
   
### Note: If you face any issues, remove everything and start again. ###

## [DDEV most used commands](https://ddev.readthedocs.io/en/latest/users/usage/cli/) ##

1. **ddev config:** This command is used to create a new configuration file for your project. The configuration file specifies the settings for your local development environment, such as the web server, database, and PHP version. Example: **ddev config**

    Running this command will prompt you for information about your project, such as the name of your project, the web server you want to use (e.g. Apache or Nginx), and the version of PHP you want to use. Once you have provided all the necessary information, Ddev will generate a configuration file (.ddev/config.yaml) in your project directory.

2. **ddev install:** This command is used to create and start your local development environment based on the configuration specified in your .ddev/config.yaml file. Example: **ddev install**

    Running this command will use Docker to create a containerized environment for your project, based on the settings specified in your .ddev/config.yaml file. This will include creating a web server, database server, and other necessary services.

3. **ddev start** - This command starts your ddev project by spinning up the required containers. Example: **ddev start**

4. **ddev stop** - This command stops your ddev project by shutting down the containers. Example: **ddev stop**

5. **ddev restart** - This command restarts your ddev project by stopping and then starting the containers. Example: **ddev restart**

6. **ddev describe** - This command shows detailed information about your ddev project, including container statuses and environment variables. Example: **ddev describe**

7. **ddev ssh** - This command allows you to SSH into the web container of your ddev project. Example: **ddev ssh**

8. **ddev import-db** - This command imports a database into your ddev project from a SQL file. Example: **ddev import-db --src=/path/to/database.sql**

9. **ddev export-db** - This command exports the database from your ddev project to a SQL file. Example:**ddev export-db --target=/path/to/database.sql**

10. **ddev snapshot** - Creates a snapshot of the local development environment. Example: **ddev snapshot my_snapshot**

11. **ddev db** - This command opens the database client for your ddev project, allowing you to interact with the database. Example: **ddev db**

12. **ddev exec** - This command allows you to run a command inside the web container of your ddev project. Example: **ddev exec drush cr**
   **Note:** We can also use like that **ddev drush cr** or **ddev composer install** 
   
13. **ddev logs** - This command allows you to view the logs for your ddev project. Example: **ddev logs**

14. **ddev list** - This command lists all of your ddev projects. Example: **ddev list**

15. **ddev delete** - This command deletes a ddev project and all of its associated containers. Example: **ddev delete**

16. **ddev poweroff** - This command stops all running ddev projects. Example: **ddev poweroff**

[<< Previous Page](README.md)
