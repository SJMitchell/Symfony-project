symfony-project.com
===================
# Shane Mitchell #
# Mitchell.ShaneJ@gmail.com #

<strong>This project is just a simple implementation of a Symfony3 project in order to learn familiarize with the Symfony3 Framework.</strong>

Prerequesites:
*  PHP >= 5.5.9</br>
*  Composer</br>
*  MySQL</br>
** Apache2/Nginx (only if you don't want to use php's built in web server, like in production)</br>
</br>
1. Installing Symfony - (http://symfony.com/doc/current/book/installation.html)
    A.  Using Symfony Installer:</br>
      I. Get the installer by running the following commands:</br>
          $ sudo curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony</br>
          $ sudo chmod a+x /usr/local/bin/symfony</br>
      II. Create a new project by running the following command:</br>
        $ symfony new symfony-project.com</br>
        ** Note that you can specify specific versions of symfony by adding another parameter of the version you wish to install (even the latest lts).  Example: symfony new my_project_name 3.0 or symfony new my_project_name lts</br>
</br>
    B.  Using Composer: (My preferred method)</br>
      I Run the following command: (after you have composer installed)</br>
        $ composer create-project symfony/framework-standard-edition symfony-project.com</br>
        ** Note that you can specify specific versions of symfony by adding another parameter of the version you wish to install.  Example: $ composer create-project symfony/framework-standard-edition my_project_name "3.0.*"</br>
</br></br>
2. Settup Permissions - http://symfony.com/doc/current/book/installation.html#book-installation-permissions</br>
    A.  Using Linux: </br>
    Most Linux and BSD distributions don't support chmod +a, but do support another utility called setfacl. You may need to enable ACL support on your partition and install setfacl before using it. This uses a command to try to determine your web server user and set it as HTTPDUSER:</br>
      I. Run the following commands:</br>
        $ HTTPDUSER=`ps axo user,comm | grep -E '[a]pache|[h]ttpd|[_]www|[w]ww-data|[n]ginx' | grep -v root | head -1 | cut -d\  -f1`</br>
        $ sudo setfacl -R -m u:"$HTTPDUSER":rwX -m u:`whoami`:rwX var</br>
        $ sudo setfacl -dR -m u:"$HTTPDUSER":rwX -m u:`whoami`:rwX var</br>
</br>
    B. Using MacOS:</br>
    MacOS X allows you to use the chmod +a command. This uses a command to try to determine your web server user and set it as HTTPDUSER:</br>
      I. Run the following commands:</br>
        $ rm -rf var/cache/* var/logs/* var/sessions/*</br>
        $ HTTPDUSER=`ps axo user,comm | grep -E '[a]pache|[h]ttpd|[_]www|[w]ww-data|[n]ginx' | grep -v root | head -1 | cut -d\  -f1`</br>
        $ sudo chmod -R +a "$HTTPDUSER allow delete,write,append,file_inherit,directory_inherit" var</br>
        $ sudo chmod -R +a "`whoami` allow delete,write,append,file_inherit,directory_inherit" var</br>


- If you decided to use PHPs built in web server to host your application then you will have to start the application by running the following command inside the root of your project:</br>
    $ bin/console server:run</br>
        **There are an array of built in commands provided by symfony.  You can list them as well as any custom commands that you create in your project by just running "$ bin/console" (ommitting any specific command) from the root of your project.</br>
-- From there you will just go to browse to http://localhost:8000 in your browser to see symfony's default template page. (append this url with /app_dev.php in order to view the application's dev environment)</br>
</br>
- If you decide to use another web servper (aache2 or Nginx) check out the symfony cookbook at http://symfony.com/doc/current/cookbook/configuration/web_server_configuration.html then see the default project page by going to:  http://symfony-project.com/app_dev.php

