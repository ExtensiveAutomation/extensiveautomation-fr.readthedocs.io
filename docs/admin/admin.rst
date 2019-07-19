Administration
=============

Arrêt/relance du serveur
~~~~~~~~~~~~~~~~~~~~~~

Le serveur peut être contrôlé en utilisant la commande ``./extensiveautomation``.
Cette commande permet 
 - de démarrer ou arrêter le serveur
 - de vérifier le status du serveur
 - d'installer un adaptateur
 - de générer la clé API
 - d'afficher la version du serveur.

Pour démarrer le serveur il faut utiliser la commande ``./extensiveautomation start``.
 
.. code-block:: bash
  
  # ./extensiveautomation start

  
Pour arrêter le serveur il faut utiliser la commande ``./extensiveautomation stop``.

.. code-block:: bash
  
  # ./extensiveautomation stop

.. tip::

   Il est possible de vérifier dans les logs si le serveur est correctement démarré ou arrêté.
   
  .. code-block:: bash
    
    # tailf Var/Log/output.log
    2014-12-06 11:00:54,092 - INFO - Extensive Automation successfully started (in 1 sec.)
    ...
    2014-12-06 10:58:51,810 - INFO - Stopping server
    2014-12-06 10:58:51,911 - INFO - Extensive Automation successfully stopped!
  

Status du serveur
~~~~~~~~~~~~~~~~~~~~~~

La commande permet de vérifier le status du serveur, il y a 3 status possible
 - ``starting``: le serveur est en cours de démarrage
 - ``running``: le serveur est en cours d'exécution
 - ``stopped``: le serveur est arrêté.

Configuration du serveur
~~~~~~~~~~~~~~~~~~~~~~

Le fichier ``settings.ini`` contient l'ensemble des paramètres de configuration du serveur.
Les paramètres de configuration sont découpés en plusieurs sections:
 - Boot
 - Notifications
 - Client_Channel
 - Agent_Channel
 - WebServices
 - TaskManager
 - Network
 - Paths
 - Bin
 - Server
 - Bind
 - Misc
 - Trace
 - Supervision
 - Users_Session

Scripts crontab
~~~~~~~~~~~~~~~~~~~~

Les scripts sont disponibles dans le répertoire ``Build`` depuis les sources du serveur.

``cron.cleanup-testsresult``: ce script permet de supprimer les résultats plus vieux que 30 jours.
Le nombre de jours est configurable.