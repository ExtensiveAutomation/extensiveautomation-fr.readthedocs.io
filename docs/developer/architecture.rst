Architecture
============

La solution est basée sur un mode client/serveur.
Les tests, adaptateurs sont centralisés dans un serveur qui permet de fournir rapidement le même 
environnement de test à l'ensemble des utilisateurs.

La solution se compose de plusieurs composants:
 - Un serveur
 - Un client graphique
 - Des agents
 - Des sondes
 
.. image:: /_static/images/testlibrary/archi-extensivetesting.png

Serveur
-------

Le serveur se compose :
 - d'un reverse proxy (apache)
 - d'un ordonnanceur 
 - d'une serveur API REST
 - du framework de test
 - des adaptateurs et librairies 
 - des extensions outils
 - d'une interface web

Client Graphique
----------------

Le client graphique utilise un flux tcp/443 (https) entre le client et le serveur.
Les flux sont bidirectionnels.
 - le client effectue des appels vers l'API REST du serveur
 - le client peut recevoir des évènements du serveur via des WebSockets.

Agents
------

Un agent est contrôlé par un adaptateur, il permet de déporter le point de communication
avec le système à tester ou piloter.
Les agents utilisent un flux tcp/443 (https) pour communiquer avec le serveur.


Sondes
------

les sondes permettent de récupérer durant l'exécution d'un test des traces réseaux, fichiers de configuration ou logs.
La communication avec le serveur s'effectue sur le port tcp/443 (https).
