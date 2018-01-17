Installation
============

Serveur
-------

Installation automatique
~~~~~~~~~~~~~~~~~~~~~~~~

    Network already configured on the server
    Yum working fine, you can reach default repositories without problems
    Ntpd properly configured and running

	

    Upload the tar.gz package on your target and uncompressed-it. Before to untar, please to check if you have enough disk space. Go inside the new folder ./ExtensiveTesting.X.X.X

    # tar xf ExtensiveTesting-X.X.X.tar.gz
    # cd ExtensiveTesting-X.X.X

    Go inside the folder and execute the script ./install.sh:

    ./install.sh
    Are you sure to install the product? (yes or no) yes
    ======================================================
    =  - Installation of the ExtensiveTesting product -  =
    =                    Denis Machard                   =
    =               www.extensivetesting.org             =
    ======================================================
    * Detecting the operating system (centos 7)                [  OK  ]
    * Detecting the system architecture (x86_64)               [  OK  ]
    * Detecting Perl, Python                                   [  OK  ]
    * Detecting primary network address (XXX.XXX.XXX.XXX)      [  OK  ]
    * Adding external libraries .................              [  OK  ]
    * Adding external libraries .......                        [  OK  ]
    * Adding interop libraries .......                         [  OK  ]
    * Detecting Apache                                         [  OK  ]
    * Detecting MySQL/MariaDB                                  [  OK  ]
    * Detecting Postfix                                        [  OK  ]
    * Detecting Openssl                                        [  OK  ]
    * Detecting Php                                            [  OK  ]
    * Copying source files                                     [  OK  ]
    * Adding startup service                                   [  OK  ]
    * Updating configuration files                             [  OK  ]
    * Creating extensivetesting user                           [  OK  ]
    * Updating folders rights                                  [  OK  ]
    * Updating php configuration                               [  OK  ]
    * Updating httpd configuration                             [  OK  ]
    * Adding virtual host                                      [  OK  ]
    * Restarting httpd                                         [  OK  ]
    * Restarting MySQL/MariaDB                                 [  OK  ]
    * Restarting postfix                                       [  OK  ]
    * Adding the ExtensiveTesting database                     [  OK  ]
    * Starting ExtensiveTesting X.X.X                          [  OK  ]
    =========================================================================
    - Installation terminated!
    - Continue and go to the web interface (https://XXX.XXX.XXX.XXX/web/index.php)
    =========================================================================

    Check the status of server, perform until to have the “running” message.

    # xtctl status
    Extensive Testing is starting...


    ...

    # xtctl status
    Extensive Testing is running

    This step is optionnal, follow this page if you want to add the additionals packages.

Notes:

    Don’t forget to change all default passwords!

	
Installation personnalisée
~~~~~~~~~~~~~~~~~~~~~~~~

This part is only for advanced user! If you use the recommanded system (centOS), the custom installation is not needed.

    Prepare the table before to start the custom install
    Key 	Value
    EXTERNAL_IP 	
    EXTERNAL_FQDN 	
    MYSQL_IP 	
    MYSQL_LOGIN 	
    MYSQL_PASSWORD 	

    Upload the tar.gz package on your target and uncompressed-it. Go inside the new folder ExtensiveTesting.X.X.X

    # tar xf ExtensiveTesting-X.X.X.tar.gz
    # cd ExtensiveTesting-X.X.X

    Execute the script ./custom.sh and respond to each questions

    ./custom.sh
    ======================================================
    =  - Installation of the ExtensiveTesting product -  =
    =                    Denis Machard                   =
    =               www.extensivetesting.org             =
    ======================================================
    * Detecting the operating system (XXXXXXXX)                [  OK  ]
    * Detecting the system architecture (XXXXXX)               [  OK  ]
    * Detecting Perl, Python                                   [  OK  ]
    * Detecting primary network address (XX.XX.XX.XX)          [  OK  ]
    * Download automatically all missing packages? [Yes] 
    * In which directory do you want to install the ExtensiveTesting product? [/opt/xtc/]
    * What is the directory that contains the init scripts? [/etc/init.d/]
    * What is the external ip of your server? [XX.XX.XX.XX] <EXTERNAL_IP>
    * What is the FQDN associated to the external ip of your server? [XX.XX.XX.XX] <EXTERNAL_FQDN>
    * What is the database name? [xtcXXX]
    * What is the table prefix? [xtc]
    * What is the ip of your mysql/mariadb server? [127.0.0.1] <MYSQL_IP>
    * What is the login to connect to your mysql/mariadb server? [root] <MYSQL_LOGIN>
    * What is the password of previous user to connect to your mysql/mariadb server? [] <MYSQL_PASSWORD>
    * What is the sock file of your mysql/mariadb server? [/var/lib/mysql/mysql.sock]
    * Do you want to configure iptables automatically? [Yes]?
    * Do you want to configure php automatically? [Yes]?
    * Where is your php conf file? [/etc/php.ini]
    * Do you want to configure apache automatically? [Yes]?
    * What is the directory that contains the httpd conf file? [/etc/httpd/conf/]
    * What is the directory that contains the httpd virtual host conf files? [/etc/httpd/conf.d/]
    * What is the directory that contains the virtual host? [/var/www/]
    * Do you want to configure selinux automatically? [No]?
    * What is the path of the openssl binary? [/usr/bin/openssl]

    Wait during the process of installation

    * Adding external libraries ......................         [  OK  ]
    * Adding external libraries ..........                     [  OK  ]
    * Adding interop libraries .......                         [  OK  ]
    * Detecting Apache                                         [  OK  ]
    * Detecting MySQL/MariaDB                                  [  OK  ]
    * Detecting Postfix                                        [  OK  ]
    * Detecting Openssl                                        [  OK  ]
    * Detecting Php                                            [  OK  ]
    * Copying source files                                     [  OK  ]
    * Adding startup service                                   [  OK  ]
    * Updating configuration files                             [  OK  ]
    * Creating extensivetesting user                           [  OK  ]
    * Updating folders rights                                  [  OK  ]
    * Updating iptables                                        [  OK  ]
    * Updating php configuration                               [  OK  ]
    * Updating httpd configuration                             [  OK  ]
    * Adding wstunnel module                                   [  OK  ]
    * Adding virtual host                                      [  OK  ]
    * Restarting httpd                                         [  OK  ]
    * Restarting firewall                                      [  OK  ]
    * Restarting Mysql/MariaDB                                 [  OK  ]
    * Restarting postfix                                       [  OK  ]
    * Adding the ExtensiveTesting database                     [  OK  ]
    * Starting ExtensiveTesting X.X.X server                   [  OK  ]
    ==================================================================
    - Installation terminated!
    - Continue and go to the web interface (https://XXX.XXX.XXX.XXX/web/index.php)
    ==================================================================

    Check the status of server, perform until to have the “running” message.

    # xtctl status
    Extensive Testing is starting...


    ...

    # xtctl status
    Extensive Testing is running

    You can access to the web interface of the server with https://<EXTERNAL_FQDN>/ Several default accounts exists after the installation without password:
        Admin
        Tester
        Developer
        Leader
        Automaton

		
Installation manuelle
~~~~~~~~~~~~~~~~~~~~~
	
<décrier les packages python à installer>

Mise à jour
~~~~~~~~~~~

This part can be useful to deploy a new test server with old data. Read the backup page for more details about backups.
Migration

    Make a new from scratch deployment, follow the installation guide.

    Retrieve all backups from the old server (folder /opt/xtc/current/Var/Backups)
        Tests
        Adapters
        Librairies
        Database dump
        Tasks

    Restore adapters package in /opt/xtc/current/Packages/SutAdapters/

    Restore libraries package in /opt/xtc/current/Packages/SutLibraries/

    Import the dump of the database
        users table
        projects table
        environment data table

    Restore all tests, unzip your backup in /opt/xtc/current/Var/Tests/

    And finally, restore tasks backup in /opt/xtc/current/Var/Backups/Tasks/

	
Retour arrière
~~~~~~~~~~~

Rollback

    Go inside the folder used to install the product

    Execute the script ./rollback.sh and provies the previous targetted version X.X.X

# ./rollback.sh X.X.X
==================================================
=  - Rollback of the ExtensiveTesting product -  =
=                 Denis Machard                  =
=            www.extensivetesting.org            =
==================================================
* Detecting the operating system                           [  OK  ]
* Detecting the system architecture                        [  OK  ]
* Stopping the ExtensiveTesting server                     [  OK  ]
* Rollbacking to ExtensiveTesting-X.X.X                    [  OK  ]
* Restarting the ExtensiveTesting server                   [  OK  ]
=========================================================================
- Rollback terminated!
=========================================================================


Désintallation
~~~~~~~~~~~~~~

Uninstall

    Go inside the folder used to install the product

    Execute the script ./uninstall.sh

# ./uninstall.sh 
===================================================
=  - Uninstall of the ExtensiveTesting product -  =
=                 Denis Machard                   =
=            www.extensivetesting.org             =
===================================================
* Detecting the operating system                           [  OK  ]
* Detecting the system architecture                        [  OK  ]
* Stopping the ExtensiveTesting server                     [  OK  ]
* Stopping httpd                                           [  OK  ]
* Removing the ExtensiveTesting database                   [  OK  ]
* Removing the ExtensiveTesting source                     [  OK  ]
* Removing the ExtensiveTesting service                    [  OK  ]
* Removing ExtensiveTesting user                           [  OK  ]
* Restoring php                                            [  OK  ]
* Removing httpd configuration                             [  OK  ]
* Restarting httpd                                         [  OK  ]
=========================================================================
- Uninstallation terminated!
=========================================================================

Notes:

    If errors occurred during uninstall, you can retry and continue the uninstallation with the option force.

	
Déploiement
~~~~~~~~~~~

Push a new client

Use this feature can be useful to dispatch to all testers a new version of the client.

    Deploy a new client version for Windows
    Deploy a new client version for Linux

Deploy a new client version for Windows

    Go to the folder <INSTALL_PATH>/current/Packages/Client

    Upload the new Windows version in the folder /win32/ or /win64/

    [ win32]# ls
    ExtensiveTesting_Client_X.X.X_Setup.exe

    No restart needed, just re-deploy the new client as below:

    # xtctl deploy
    Deploying clients.(ExtensiveTestingClient_X.X.X_Setup.exe)
    Deploying tools.(ExtensiveTestingToolbox_X.X.X_Setup.exe)
    Deploying portable clients... (No client)
    Deploying portable tools... (No client)

Deploy a new client version for Linux

    Go to the folder <INSTALL_PATH>/current/Packages/Client

    Upload the new version in the folder /linux2/

    [ linux2]# ls
    ExtensiveTesting_Client_X.X.X_Setup.tar.gz

    No restart needed, just re-deploy the new client as below:

    # xtctl deploy
    Deploying clients.(ExtensiveTestingClient_X.X.X_Setup.exe)
    Deploying tools.(ExtensiveTestingToolbox_X.X.X_Setup.exe)
    Deploying portable clients... (No client)
    Deploying portable tools... (No client)


	
	
Client
------

Installation Windows
~~~~~~~~~~~~~~~~~~~~

Installer for Windows

    Go to your online test center and navigate in the menu to Overview > Packages. Download the Windows package.

    Execute the package ExtensiveTestingClient_XX.XX.XX_<32bit|64bit>_Setup.exe, read and accept the license agreement and click on Next.

    You are ready to install the client. Click on the button Install.

    Click on Finish. Read the release notes if you want.

    Click on the icon to open the application

Portable version for Windows

    Use the portable version if you have restricted rights on your Windows pc. Go to your online test center and navigate in the menu to Overview > Packages. Download the portable version.

    Unzip the file ExtensiveTestingClient_XX.XX.XX_<32bit|64bit>_Portable.zip and go inside.

    Click on ExtensiveTestingClient.exe to open the client.


	
Installation Linux
~~~~~~~~~~~~~~~~~~



    Go to your online test center and navigate in the menu to Overview > Packages. Download the Linux package.

    Untar the file ExtensiveTestingClient_XX.XX.XX_Setup.tar.gz and go inside.

    Execute the file ./ExtensiveTestingClient

	
Mise à jour
~~~~~~~~~~~

Automatic or manual mode are supported to update the client. Client binaries are stored on the server and can be downloaded by tester.
Manual Update

The user can also check manually from the menu Get Started > Check for update The other way is to download the package directly from the web interface.
Automatic Update

    Open the application and connect to the test center with your account.

    A popup appears to inform of the availability of a new client. Click on the button Download and wait during the download.

    When the download is finished, click on OK to close the popup. After that, the application is closed automatically too.

    Go the folder Update in the installation directory and execute the new package. Install the client as usual without remove the previous version to keep the configuration.

Notes:

    The update of the client with a major version is mandatory!

	
Boite à outils
--------------

Installation Windows
~~~~~~~~~~~~~~~~~~~~

Installer for Windows

    Connect to the test center and go to the menu Overview > Packages > Toolbox. Download the toolbox package according to your environment (Windows or Linux)

    Execute the package ExtensiveTestingToolbox_XX.XX.XX_<32bit|64bit>_Setup.exe

    Accept the license

    Select components to install, select all by default

    Follow steps of the wizard installation. The installation takes some minutes. When the installation is terminated, open-it! A shortcut is also available on your desktop. The toolbox is automatically installed on the startup folder of the operating system.

Portable version for Windows

    Use the portable version if you have restricted rights on your Windows pc. Go to your online test center and navigate in the menu to Overview > Packages. Download the portable version.

    Unzip the file ExtensiveTestingToolbox_XX.XX.XX_<32bit|64bit>_Portable.zip and go inside.

    Execute the file ExtensiveTestingToolbox.exe to open the toolbox.


	
Installation Linux
~~~~~~~~~~~~~~~~~~



    Go to your online test center and navigate in the menu to Overview > Packages. Download the Linux package.

    Untar the file ExtensiveTestingToolbox_XX.XX.XX_Setup.tar.gz and go inside.

    Execute the script ./toolagent or ./toolprobe to display the help

    ./toolagent
    Command line tool launcher


    Usage: ./toolagent [test-server-ip] [test-server-port] [ssl-support] [ftp|sikulix|socket|dummy|database|selenium|gateway-sms|command|soapui|file|adb|ssh] [tool-name] [tool-description] [[proxy-ip] [proxy-port]]


    * Server parameters
    [test-server-ip]: your test server ip or hostname. This option is mandatory.
    [test-server-port]: your test server port. This option is mandatory.
    [ssl-support=True/False]: ssl support. This option is mandatory.


    * Tools parameters
    [Values expected: ftp|sikulix|socket|dummy|database|selenium|gateway-sms|command|soapui|file|adb|ssh]: tool type to start. This option is mandatory.
    [tool-name]: The tool name. This option is mandatory.
    [tool-description]: The tool description. This option is mandatory.


    * Proxy parameters
    [proxy-ip]: proxy address. This option is optional.
    [proxy-port]: proxy port. This option is optional.


    ./toolprobe
    Command line tool launcher


    Usage: ./toolprobe [test-server-ip] [test-server-port] [ssl-support] [dummy|textual|network|file] [tool-name] [tool-description] [[proxy-ip] [proxy-port]]


    * Server parameters
    [test-server-ip]: your test server ip or hostname. This option is mandatory.
    [test-server-port]: your test server port. This option is mandatory.
    [ssl-support=True/False]: ssl support. This option is mandatory.


    * Tools parameters
    [Values expected: dummy|textual|network|file]: tool type to start. This option is mandatory.
    [tool-name]: The tool name. This option is mandatory.
    [tool-description]: The tool description. This option is mandatory.


    * Proxy parameters
    [proxy-ip]: proxy address. This option is optional.
    [proxy-port]: proxy port. This option is optional.


	
Mise à jour
~~~~~~~~~~~

La mise à jour de la boites à outils est à faire manuellement.
Il faut récupérer le paquet depuis le site internet ou bien depuis le serveur de test.

La mise à jour nécessite
 - supprimer la version courante
 - ajouter la nouvelle version et reconfigurer les agents ou sondes à redémarrer.
 
.. notes: La mise à jour automatique n'est pas encore supportée.