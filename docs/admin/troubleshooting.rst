Dépannage
=========

Récupération des logs
---------------------

Serveur
~~~~~~~

Les logs serveurs sont stockés sur ``[...]Var/Logs/``.
Les logs sont configurés en mode ``INFO`` par défaut.
Le niveau DEBUG peut être activé depuis le fichier ``settings.ini``.

.. code-block::
    [Trace]
    level=DEBUG

.. note:: Il est possible de changer le niveau de logs à chaud en faisant un ``./extensiveautomation reload``

Client
~~~~~~~

Les logs du client sont disponibles dans ``<Program Files>/Extensive Automation Client/Logs/`` 
Les logs sont configurés en mode ``INFO`` par défaut.

Le niveau DEBUG peut être activé depuis les préférences du client.

.. image:: /_static/images/client/preferences_application_logs.png

.. image:: /_static/images/client/client_logs.png

Boîtes à outils
~~~~~~~~~~~~~~

Les logs de la boîte à outils sont disponibles dans ``<Program Files>/Extensive Automation Toolbox/Logs/``
Les logs sont configurés en mode ``INFO`` par défaut.

Le niveau DEBUG peut être activé depuis le fichier ``settings.ini``.

.. code-block::
    [Trace]
    level=DEBUG
    
.. image:: /_static/images/client/toolbox_logs.png
    
.. note:: Un redémarrage de la boîte à outils est nécessaire pour prendre en compte le changement

Foire aux questions
---------------------


Comment changer le port de connexion du client ?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le port de destination peut être modifié depuis les préférences du client.
Ou bien directement depuis le fichier ``settings.ini``.

.. image:: /_static/images/client/preferences_network_ports.png

Afficher la version du serveur?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

    ./extensiveautomation --version
    Server version: 20.0.0

Quoi faire si ma connection au serveur ne fonctionne pas?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Si la connection depuis le client au serveur ne fonctionne pas, une analyse est nécessaire.

Le 1er reflex à avoir est de se connecter sur le serveur en SSH et d'exécuter la commande ``./extensiveautomation --status`` pour vérifier si le serveur tourne.

1. Si le serveur est en cours d'exécution alors il faut vérifier:
 - la connectivité réseau en le client et le serveur
 - un parefeu bloquant le flux https (443)

2. Si la connectivité réseau est bonne et que le serveur fonctionne (ou pas), il faut vérifier les logs.
Le fichier est disponible dans le répertoire ``(...]Var/Logs/output.log``. Il faut rechercher les messages de type ``ERROR``

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
