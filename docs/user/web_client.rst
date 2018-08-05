Interface Web
=============

.. image:: /_static/images/webinterface/tests_center_main_page.png

Partie tests
------------

Variables globales
~~~~~~~~~~~~~~~~~~~~~~~

Les variables globales permettent de décrire un jeu de données pour l'ensemble d'un projet. 
Ils sont automatiquement accessibles au niveau de chaque test depuis les propriétés.

Le format ``JSON`` doit être utilisé.

Partie administration
---------------------

Utilisateurs
~~~~~~~~~~~~

La solution nécessite de créer des comptes utilisateurs.
La création peut se faire à travers l'interface Web ou bien directement depuis l'API.

La création d'un utilisateur nécessite à minima de préciser: 
 - un nom d'utilisateur
 - un mot de passe
 - son niveau d'accès (administrateur, testeur)
 - les projets autorisés

.. note:: Si une adresse email est précisée, alors il est possible de recevoir les résultats des tests automatiquement dans cette boite mail.

.. warning: Ne pas oublier de modifier les mots de passe des utilisateurs ``admin`` et ``tester``, par défaut ils n'ont pas de mot de passe.

Projets
~~~~~~~

Les tests peuvent être organisés par projet.
L'ajout ou la suppression de projet peut se faire depuis l'interface web ou directement depuis l'api REST.

.. note:: Le projet ``Common`` existe par défaut et est accessible par l'ensemble des utilisateurs, il ne peut pas être supprimé.

Partie système
--------------

La partie système permet de voir le statut du serveur.
