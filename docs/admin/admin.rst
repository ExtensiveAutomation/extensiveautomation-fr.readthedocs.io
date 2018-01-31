Administration
=============

Arr�t/relance du serveur
~~~~~~~~~~~~~~~~~~~~~~

Le serveur peut �tre contr�l� en utilisant la commande ``xtctl``.
Cette commande permet 
 - de d�marrer ou arr�ter le serveur
 - de v�rifier le status du serveur
 - de mettre � disposition un nouveau client graphique ou la boite � outils
 - d'afficher la version du serveur.

Pour d�marrer le serveur il faut utiliser la commande ``xtctl start``.
 
.. code-block:: bash
  
  # xtctl start
  Checking database                                          [  OK  ]
  Saving current adapters                                    [  OK  ]
  Saving current libraries                                   [  OK  ]
  Starting Extensive Testing                                 [  OK  ]
  
  
Pour arr�ter le serveur il faut utiliser la commande ``xtctl stop``.

.. code-block:: bash
  
  # xtctl stop
  Saving current adapters                                    [  OK  ]
  Saving current libraries                                   [  OK  ]
  Stopping Extensive Testing                                 [  OK  ]
  

.. tip::

   Il est possible de v�rifier dans les logs si le serveur est correctement d�marr� ou arr�t�.
   
  .. code-block:: bash
    
    # tailf /opt/xtc/current/Var/Log/output.log
    2014-12-06 11:00:54,092 - INFO � Extensive Testing successfully started (in 14 sec.)
    ...
    2014-12-06 10:58:51,810 - INFO - Stopping server
    2014-12-06 10:58:51,911 - INFO � Extensive Testing successfully stopped!
  

Status du serveur
~~~~~~~~~~~~~~~~~~~~~~

La commande permet de v�rifier le status du serveur, il y a 3 status possible
 - ``starting``: le serveur est en cours de d�marrage
 - ``running``: le serveur est en cours d'ex�cution
 - ``stopped``: le serveur est arr�t�.

.. tip:: 
  V�rifier aussi le status du serveur ``httpd`` et la base de donn�e ``mysql``.
  
D�ploiement nouveaux paquets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

La solution permet de mettre � disposition aupr�s des utilisateurs les paquets suivants pour faciliter la diffusion:
 - le client lourd
 - la bo�te � outils
 - les diff�rents plugins.

Lorsqu'un nouveau client est disponible, il est possible de le d�poser sur le serveur pour automatiquement 
notifier les utilisateurs de la mise � jour.

Les paquets sont � d�poser dans le r�pertoire ``<INSTALL_PATH>/current/Packages/``

+-----------------+-------------------------------------------------+
|Client           | Contients la version portable et installation   |
+-----------------+-------------------------------------------------+
|ClientPlugins    |  Contients les plugins                          |
+-----------------+-------------------------------------------------+
|Toolbox          |  Contients la version portable et installation  |
+-----------------+-------------------------------------------------+
|ToolboxPlugins   |  Contients les plugins                          |
+-----------------+-------------------------------------------------+

Apr�s d�p�t, les paquets logiciels sont automatiquement disponibles depuis l'interface web.
Pour la mise � jour en mode automatique du client, il faut ex�cuter la commande ``xtctl deploy`` sur le serveur
pour prendre en compte le nouveau client d�ploy�.

.. code-block:: bash
  
  ./xtctl deploy
  Deploying clients.(ExtensiveTestingClient_X.X.X_Setup.exe)
  Deploying tools.(ExtensiveTestingToolbox_X.X.X_Setup.exe)
  Deploying portable clients... (No client)
  Deploying portable tools... (No client)
  
Configuration du serveur
~~~~~~~~~~~~~~~~~~~~~~

Le fichier ``settings.ini`` contient l'ensemble des param�tres de configuration du serveur.