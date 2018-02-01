Administration
=============

Arrêt/relance du serveur
~~~~~~~~~~~~~~~~~~~~~~

Le serveur peut être contrôlé en utilisant la commande ``xtctl``.
Cette commande permet 
 - de démarrer ou arrêter le serveur
 - de vérifier le status du serveur
 - de mettre à disposition un nouveau client graphique ou la boite à outils
 - d'afficher la version du serveur.

Pour démarrer le serveur il faut utiliser la commande ``xtctl start``.
 
.. code-block:: bash
  
  # xtctl start
  Checking database                                          [  OK  ]
  Saving current adapters                                    [  OK  ]
  Saving current libraries                                   [  OK  ]
  Starting Extensive Testing                                 [  OK  ]
  
  
Pour arrêter le serveur il faut utiliser la commande ``xtctl stop``.

.. code-block:: bash
  
  # xtctl stop
  Saving current adapters                                    [  OK  ]
  Saving current libraries                                   [  OK  ]
  Stopping Extensive Testing                                 [  OK  ]
  

.. tip::

   Il est possible de vérifier dans les logs si le serveur est correctement démarré ou arrêté.
   
  .. code-block:: bash
    
    # tailf /opt/xtc/current/Var/Log/output.log
    2014-12-06 11:00:54,092 - INFO - Extensive Testing successfully started (in 14 sec.)
    ...
    2014-12-06 10:58:51,810 - INFO - Stopping server
    2014-12-06 10:58:51,911 - INFO - Extensive Testing successfully stopped!
  

Status du serveur
~~~~~~~~~~~~~~~~~~~~~~

La commande permet de vérifier le status du serveur, il y a 3 status possible
 - ``starting``: le serveur est en cours de démarrage
 - ``running``: le serveur est en cours d'exécution
 - ``stopped``: le serveur est arrêté.

.. tip:: 
  Vérifier aussi le status du serveur ``httpd`` et la base de donnée ``mysql``.
  
Déploiement nouveaux paquets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

La solution permet de mettre à disposition des utilisateurs les paquets suivants pour faciliter la diffusion:
 - le client lourd
 - la boîte à outils
 - les différents plugins.

Lorsqu'un nouveau client est disponible, il est possible de le déposer sur le serveur pour automatiquement 
notifier les utilisateurs de la mise à jour.

Les paquets sont à déposer dans le répertoire ``<INSTALL_PATH>/current/Packages/``

+-----------------+-------------------------------------------------+
|Client           | Contients la version portable et installation   |
+-----------------+-------------------------------------------------+
|ClientPlugins    |  Contients les plugins                          |
+-----------------+-------------------------------------------------+
|Toolbox          |  Contients la version portable et installation  |
+-----------------+-------------------------------------------------+
|ToolboxPlugins   |  Contients les plugins                          |
+-----------------+-------------------------------------------------+

Après dépôt, les paquets logiciels sont automatiquement disponibles depuis l'interface web.
Pour la mise à jour en mode automatique du client, il faut exécuter la commande ``xtctl deploy`` sur le serveur
pour prendre en compte le nouveau client déployé.

.. code-block:: bash
  
  ./xtctl deploy
  Deploying clients.(ExtensiveTestingClient_X.X.X_Setup.exe)
  Deploying tools.(ExtensiveTestingToolbox_X.X.X_Setup.exe)
  Deploying portable clients... (No client)
  Deploying portable tools... (No client)

Configuration du serveur
~~~~~~~~~~~~~~~~~~~~~~

Le fichier ``settings.ini`` contient l'ensemble des paramètres de configuration du serveur.
Les paramètres de configuration sont découpés en plusieurs sections:
 - Boot
 - Notifications
 - Client_Channel
 - Agent_Channel
 - Probe_Channel
 - WebServices
 - TaskManager
 - Network
 - Paths
 - Bin
 - Server
 - Web
 - Bind
 - Misc
 - MySql
 - Trace
 - Backups
 - Default
 - Csv_Test_Results:
 - Tests_Framework
 - Events_Colors
 - Supervision
 - Users_Session
  
Sauvegardes automatiques
~~~~~~~~~~~~~~~~~~~~~~
  
Par défaut la solution sauvegarder l'ensemble des tests, adaptateurs et libraries chaques jours.
Les sauvegardes sont disponibles dans ``opt/xtc/current/Var/Backups``.

La périodicité peut être configuré dans la section ``Backups`` du fichier ``settings.ini``.

.. code-block:: bash
  
  [Backups]
  ; tests repository
  ; 0=disable 1=enable
  tests=1
  ; backup zip name
  tests-name=tests-automatic-backup
  ; backup weekly on sunday at 23:40:00
  tests-at=5|23,40,00
  
Rythme de sauvegarde disponible:
 - 6: une fois par semaine
 - 5: une fois par jour
 - 4: une fois par heure