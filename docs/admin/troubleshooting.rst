Dépannage
=========

Récupération des logs
---------------------

Serveur
~~~~~~~

Les logs serveurs sont stockés sur `/opt/xtc/current/Var/Logs/`.
Les logs sont configurés en mode INFO par défaut.
Le niveau DEBUG peut être activé depuis le fichier settings.ini

.. code-block::
    [Trace]
    level=DEBUG

.. notes:: Il est possible de changer le niveau de logs à chaud en faisant un `xtcl reload`

Client
~~~~~~~

Les logs du client sont disponibles dans <Program Files>/Extensive Testing Client/Logs/ Client 
Les logs sont configurés en mode INFO par défaut.

Le niveau DEBUG peut être activé depuis les préférences du client.

.. image:: /_static/images/client/preferences_application_logs.png

.. image:: /_static/images/client/client_logs.png

Boites à outils
~~~~~~~~~~~~~~

Les logs de la boite à outils sont disponibles dans <Program Files>/Extensive Testing Toolbox/Logs/
Les logs sont configurés en mode INFO par défaut.

Le niveau DEBUG peut être activé depuis le fichier `settings.ini`.

.. code-block::
    [Trace]
    level=DEBUG
    
.. image:: /_static/images/client/toolbox_logs.png
    
.. notes: Un redémarrage de la boite à outils est nécessaire pour prendre en compte le changement

FAQ
---

Comment changer le port d'écoute (tcp/443) du serveur ?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Editer le fichier `/etc/httpd/conf.d/extensivetesting.conf` et modifier le port d'écoute du virtual host 443.
Ne pas oublier de modifier le fichier `/etc/httpd/conf/httpd.conf` pour ajouter le nouveau port d'écoute.

Un redémarrage d'apache est nécessaire.

Comment changer le port de connexion du client ?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le port de destination peut être modifié depuis les préférences du client.
Ou bien directement depuis le fichier `settings.ini`

Afficher la version du serveur?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

    ./xtctl version
    Server version: 18.0.0
    
