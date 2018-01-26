Dépannage
=========

Récupération des logs
---------------------

Serveur
~~~~~~~

Les logs serveurs sont stockés sur ``/opt/xtc/current/Var/Logs/``.
Les logs sont configurés en mode ``INFO`` par défaut.
Le niveau DEBUG peut être activé depuis le fichier ``settings.ini``.

.. code-block::
    [Trace]
    level=DEBUG

.. note:: Il est possible de changer le niveau de logs à chaud en faisant un ``xtcl reload``

Client
~~~~~~~

Les logs du client sont disponibles dans ``<Program Files>/Extensive Testing Client/Logs/`` 
Les logs sont configurés en mode ``INFO`` par défaut.

Le niveau DEBUG peut être activé depuis les préférences du client.

.. image:: /_static/images/client/preferences_application_logs.png

.. image:: /_static/images/client/client_logs.png

Boîtes à outils
~~~~~~~~~~~~~~

Les logs de la boîte à outils sont disponibles dans ``<Program Files>/Extensive Testing Toolbox/Logs/``
Les logs sont configurés en mode ``INFO`` par défaut.

Le niveau DEBUG peut être activé depuis le fichier ``settings.ini``.

.. code-block::
    [Trace]
    level=DEBUG
    
.. image:: /_static/images/client/toolbox_logs.png
    
.. note:: Un redémarrage de la boîte à outils est nécessaire pour prendre en compte le changement

FAQ
---

Comment changer le port d'écoute (tcp/443) du serveur ?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Editer le fichier ``/etc/httpd/conf.d/extensivetesting.conf`` et modifier le port d'écoute du virtual host 443.
Ne pas oublier de modifier le fichier ``/etc/httpd/conf/httpd.conf`` pour ajouter le nouveau port d'écoute.

.. note:: Un redémarrage d'apache est nécessaire.

Comment changer le port de connexion du client ?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le port de destination peut être modifié depuis les préférences du client.
Ou bien directement depuis le fichier ``settings.ini``.

.. image:: /_static/images/client/preferences_network_ports.png

Afficher la version du serveur?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

    ./xtctl version
    Server version: 18.0.0
    
Quoi faire si l'installation du serveur ne fonctionne pas?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le déroulement de l'installation du serveur est loggué dans un fichier ``install.log`` présent dans le répertoire après extraction du paquet.
Il faut rechercher les messages d'erreurs présents dans le fichier.

Quoi faire si ma connection au serveur ne fonctionne pas?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Si la connection depuis le client au serveur ne fonctionne pas, une analyse est nécessaire.

Le 1er reflex à avoir est de se connecter sur le serveur en SSH et d'exécuter la commande ``xtctl status`` pour vérifier si le serveur tourne.

1. Si le serveur est en cours d'exécution alors il faut vérifier:
 - la connectivité réseau en le client et le serveur
 - un parefeu bloquant le flux https (443)

2. Si la connectivité réseau est bonne et que le serveur fonctionne (ou pas), il faut vérifier les logs.
Le fichier est disponible dans le répertoire ``/opt/xtc/current/Var/Logs/output.log``. Il faut rechercher les messages de type ``ERROR``

Comment corriger l'erreur "hping3 n'est pas installé" ?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cette erreur apparait durant l'exécution d'un test quand l'adaptateur ``Pinger`` est utilisé.
En effet nécessite d'avoir la librairie système hping3 d'installée sur le serveur.

Il faut récupérer les sources depuis https://github.com/antirez/hping et les compiler:

.. code-block:: bash
  
  cd hping-master
  yum install libpcap-devel-1.5.3-9.el7.x86_64
  ln -s /usr/include/pcap/bpf.h /usr/include/net/bpf.h
  ./configure
  make
  make install
  
Comment isntaller le serveur dans un répertoire spécifique?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Par défaut, le serveur s'installe dans le répertoire ``/opt/xtc/``, il est possible de changer ce répertoire
au moment de l'installation en modifiant la clé ``INSTALL`` dans le fichier ``default.cfg``

.. code-block:: bash
  
  INSTALL=/opt/xtc/
  
