Notes de version
================

Version courante
---------------

.. note::

 **Version 21.2.0 disponible depuis le 20/09/2019**
 
 - Quelques bugs corrigés au niveau de l'API REST
 - Support PEP8 python
 - Nouvelle fonction pour retourner l'ensemble des tâches depuis l'API

Une release notes détaillée est disponible dans le paquet du serveur.

Versions précédentes
-------------------

..

 **Version 21.1.0 disponible depuis le 25/08/2019**

 - Désactivation de la notification par email sur Windows
 - Le chiffrement des variables dans la base de donnée est supprimée
 - Le grain de sel est maintenant généré durant la création de la base de donnée
 - Création automatique des répertoires du projets au démarrage du serveur
 - Nettoyage du modèle de la table utilisateurs
 - Les utilisateurs, projets et variables par défauts sont maintenant déclarés dans des fichiers json
 - Support de l'authentification LDAP pour les utilisateurs

..

 **Version 21.0.0 disponible depuis le 10/08/2019**

 - Support complet de Python3 côté serveur
 - Support de Windows pour l'exécution du serveur
 - Le répertoire "backups" est supprimé
 - Réorganisation du projet pour une meilleure gestion des imports
 - Test interop fusionné dans les sut adapters
 - Nouvelle image docker du serveur basée sur Python3
 - Nouveau mode d'installation du serveur à travers pypi
 - Nouveau mode d'installation des plugins à travers pypi

..

 **Version 20.0.0 disponible depuis le 20/07/2019**
 
 - Image docker disponible
 - Rest API: CORS support
 - Procédure d'installation automatique du produit supprimée 
 - Suppression d'un maximum de dépendances
 - Plus de plugins embarqués par défaut
 - Les sondes sont supprimés du produit, utilisation des agents à la place
 - Supression de la base de donnée MySQL, remplacer par une base Sqlite
 - Optimisation du framework de test pour réduire la consommation CPU
 - Nouveau version majeure du client lourd, simplification de l'interface
 - Nouvelle version majeure de la boite à outils
 - Nouvelle version majeure de l'interface web totalement indépendante, non fournie par défaut.
 - Corrections de bugs divers

..

 **Version 19.0.1 sortie le 09/08/2018**
 
 - Changement du nom de produit de la solution par ExtensiveAutomation
 - Fichiers stockés en mode XML par défaut (plus de compression) 
 - Améliorations et corrections diverses au niveau de l'API REST
 - Support initial docker
 - Python 2.6 n'est plus supporté côté serveur
 - Prévisualisation du cache durant l'écriture des tests dans le client
 - Simplification des paramètres de tests avec les types "text" et "json"
 - Optimisation du nombre de requête SQL sur le serveur
 - Support initial de python 3.5 côté serveur
 - Le client lourd n'est plus embarqué sur le serveur par défaut
 - Nouvelle fonction permettant d'ajouter un message de sécurité sur la page de connexion
 - Mise à jour de selenium en 3.13.0 dans la boite à outils
 - Nouvelle version majeure pour le client lourd 
 - Nouvelle version majeure pour la boite à outils
 - Correction bug deploiement serveur, utilisation de la commande pip

..

 **Version 18.0.0 sortie le 11/02/2018**
 
 - Suppression de l'API XmlRPC sur le serveur
 - Refonte complète de l'API REST
 - Nouveau client majeur utilisant l'api rest exclusivement
 - Support de Qt5.9 pour le client et la boite à outils
 - Support de python 3.6 pour le client et la boite à outils
 - Nettoyage important de l'ensemble du code source
 - Corrections de bugs divers
 - Mise à jour de selenium en 3.9.0 dans la boite à outils
 - La boite à outils n'est plus embarquée par défaut sur le serveur

..

 **Version 17.1.0 sortie le 22/10/2017**
 
 - Amélioration de l'API REST
 - Ajout de fonctionnalités majeures dans le framework de test
 - Apport de corrections
 - Amélioration de l'interface graphique sur le client
 - Support expérimental du client sur Ubuntu

..

 **Version 17.0.0 sortie le 04/06/2017**
 
 - Passage en mode 64bits par défaut pour le client et la boite à outils
 - Ajout de fonctionnalités majeures dans le framework de test
 - Mise à disposition d'un swagger pour l'API rest
 - Mise à jour de selenium 3 et 2 dans la boite à outils
 - Apport de corrections

..
 
 **Version 16.1.0 sortie le 30/03/2017**
 
 - Apport de corrections
 - Amélioration de l'interface graphique sur le client
 - Amélioration de l'installation
 
..

 **Version 16.0.0 sortie le 25/02/2017**
 
 - Apport de corrections
 - Amélioration de l'api REST
 - Modifications diverses dans le coeur du serveur
 - Ajout de fonctionnalités dans le framework de test
 - Optimisation du nombre de requêtes SQL sur le serveur
 - Amélioration de l'interface graphique sur le client
 - Support 64bits du client et de la boite à outils
 
..

 **Version 15.0.3 sortie le 04/11/2016**
 
 - Apport de corrections
 - Nouveau plugins pour le client
 - Amélioration de l'api REST
 - Ajout de fonctionnalités dans le framework de test
 - Ajout du module intéropérabilité
 
..

 **Version 14.0.0 sortie le 27/08/2016**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans le framework de test
 - Amélioration majeures de l'API REST
 - Plus d'évolutions dans l'API XmlRPC côté serveur, correction de bugs seulement
 - Ajout de fonctionnalités dans l'interface web
 - Python2.7 n'est plus supporté sur windows pour le client et la boite à outils
 - Utilisation de l'api REST au niveau du client
 - Amélioration de l'interface graphique sur le client
 - Nouveau plugin HP QC ALM
 
..

 **Version 13.0.0 sortie le 23/06/2016**
 
 - Apport de corrections
 - Ajout API REST sur le serveur
 - Ajout de fonctionnalités dans le framework de test
 - Améliorations diverses dans le coeur du serveur
 - Support des plugins pour le client et à la boite à outils
 - Amélioration de l'interface graphique sur le client
 
..

 **Version 12.1.0 sortie le 29/04/2016**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans le framework de test
 - Quelques modifications au niveau l'API XmlRPC
 - Amélioration de l'interface graphique sur le client
 
..

 **Version 12.0.0 sortie le 12/02/2016**
 
 - Apport de corrections
 - Ajout de fonctionnalités au niveau l'API XmlRPC
 - Ajout de fonctionnalités dans le framework de test
 - Ajout de fonctionnalités dans l'interface web
 
.. 

 **Version 11.2.0 sortie le 22/11/2015**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans le framework de test
 - Amélioration de l'ordonnanceur
 - Ajout d'un dépôt public utilisé par le framework de test
 - Support installation sans accès internet
 - Modification mineures dans l'API XmlRPC
 
..

 **Version 11.1.0 sortie le 18/10/2015**
 
 - Apport de corrections
 - Ajout de fonctionnalités au niveau l'API XmlRPC
 - Ajout de fonctionnalités dans l'interface web
 
.. 

 **Version 11.0.0 sortie le 14/09/2015**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans l'interface web
 - Fusion des agents et sondes dans la boite à outils
 - Modifications au niveau de l'API XmlRPC
 - Support de python 3.4 pour le client et la boite à outils
 
..

 **Version 10.1.0 sortie le 12/07/2015**
 
 - Apport de corrections
 - CentOS 4 et 5 ne sont plus supportés officiellement
 - Ajout de fonctionnalités dans le framework de test
 - Ajout de fonctionnalités dans l'interface web
 
..

 **Version 10.0.0 sortie le 28/05/2015**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans l'interface web
 - Modifications diverses dans le coeur du serveur
 - Mise à jour des documentations
 - Amélioration de l'interface graphique sur le client
 
.. 

 **Version 9.1.0 sortie le 22/03/2015**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans le framework de test
 - Amélioration de l'installation du produit
 - Amélioration de l'interface graphique sur le client
 
..

 **Version 9.0.0 sortie le 05/01/2015**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans le framework de test
 - Python 2.4 n'est plus supporté
 - Ajout de fonctionnalités dans l'interface web
 - Amélioration de l'interface graphique sur le client
 
..

 **Version 8.0.0 sortie le 25/10/2014**
 
 - Apport de corrections
 - Amélioration de l'interface graphique sur le client
 - Ajout de fonctionnalités dans le framework de test
 - Modifications mineures au niveau de l'API XmlRPC
 - Ajout de fonctionnalités dans l'interface web
 
..

 **Version 7.1.0 sortie le 20/09/2014**
 
 - Apport de corrections
 - Mise à jour documentations
 - Optimisation pour réduire le temps de construction d'un test sur le serveur
 - Ajout de fonctionnalités dans le coeur du serveur
 - Ajout de fonctionnalités dans le framework de test
 - Amélioration de l'interface graphique sur le client
 
.. 

 **Version 7.0.0 sortie le 08/08/2014**
 
 - Apport de corrections
 - Amélioration de l'ordonnanceur
 - Ajout d'apache en mode reverse sur le serveur
 - Support des websockets activé par défaut
 - Ajout de documentations
 - Communication des composants unifiées sur le port tcp/443 ssl
 - Support proxy SSL
 - Utilisation SSL par défaut sur les agents et sondes
 - Amélioration de l'interface graphique sur le client
 
.. 

 **Version 6.2.0 sortie le 02/06/2014**
 
 - Apport de corrections
 - Mise à jour des agents
 - Modifications mineures au niveau de l'API XmlRPC
 - Ajout de fonctionnalités dans le framework de tests
 - Modifications au niveau de l'ordonnanceur
 
..

 **Version 6.1.0 sortie le 25/04/2014**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans l'interface web
 - Ajout de fonctionnalités dans le framework de tests
 - Amélioration du module agents
 
..

 **Version 6.0.0 sortie le 23/03/2014**
 
 - Apport de corrections
 - Nouveau mode de paquetage pour les adaptateurs et librairies
 - Ajout de fonctions dans l'API XmlRPC 
 - Ajout de fonctionnalités dans le framework de tests
 - Supression de la dépendance avec le projet twisted
 - Support SSL activé par défaut pour l'API XmlRPC
 - Support proxy socks4
 - Support des agents
 
..

 **Version 5.2.0 sortie le 12/01/2014**
 
 - Apport de corrections
 - Ajout de fonctionnalités mineures
 
..

 **Version 5.1.0 sortie le 08/12/2013**
 
 - Ajout de fonctionnalités dans l'interface web
 - Apport de corrections
 - Ajout de fonctionnalités dans le framework de tests
 
.. 

 **Version 5.0.0 sortie le 15/09/2013**
 
 - Apport de corrections
 - Ajout majeurs de fonctionnalités dans le framework de tests
 - Amélioration dans l'ordonnanceur

.. 

 **Version 4.2.0 sortie le 08/04/2013**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans l'interface web
 
..

 **Version 4.1.0 sortie le 10/03/2013**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans l'interface web
 - Support de CentOS 6
 - Amélioration dans l'ordonnanceur
 
..

 **Version 4.0.0 sortie le 30/01/2013**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans le framework de tests
 - Support SSL pour l'interface web
 - Nouveau mécanisme d'authentification avec salt et sha1
 - Ajout de fonctions dans l'API XmlRPC 
 
.. 

 **Version 3.2.0 sortie le 29/09/2012**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans le framework de tests
 
..

 **Version 3.1.0 sortie le 14/07/2012**
 
 - Apport de corrections
 - Ajout de fonctionnalités dans le framework de tests
 - Amélioration de l'ordonnanceur
 - Ajout de fonctions dans l'API XmlRPC 
 
..

 **Version 3.0.0 sortie le 09/06/2012**
 
 - Apport de corrections
 - Ajout de fonctions dans l'API XmlRPC 
 - Amélioration de l'ordonnanceur
 - Nouveau dépôt pour les adaptateurs et sauvegardes
 
.. 

 **Version 2.2.0 sortie le 28/03/2012**
 
 - Ajout de fonctions majeures dans l'API XmlRPC 
 - Apport de corrections
 - Ajout de fonctionnalités dans le framework de tests
 
..

 **Version 2.0.0 sortie le 27/02/2012**
 
 - Ajout de fonctions dans l'API XmlRPC 
 - Ajout de la génération de la documentation du framework et adaptateurs
 - Apport de corrections
 - Support des sondes
 
..

 **Version 1.2.0 sortie le 14/01/2012**
 
 - Amélioration de l'ordonnanceur
 - Ajout de fonctions dans l'API XmlRPC 
 - Ajout de fonctionnalités dans le framework de tests
 - Ajout d'une interface web
 - Apport de corrections
 
..

 **Version 1.0.0 sortie le 13/12/2011**
 
 - 1ière version officielle
 - Support CentOS 5
 - Apport de corrections
 
.. 

 **Version 0.1.0 sortie le 17/05/2010**
 
 - 1ière version beta