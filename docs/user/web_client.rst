Interface Web
=============

.. image:: /_static/images/webinterface/tests_center_main_page.png

Partie tests
------------

Variables réutilisables
~~~~~~~~~~~~~~~~~~~~~~~

Les variables réutilisables permettent de décrire un jeux de données. Le format ``JSON`` doit être utilisé.
Ils sont accessibles automatiquement au niveau de chaque test depuis les propriétés.

Partie administration
---------------------

Utilisateurs
~~~~~~~~~~~~

La solution nécessite de créer des comptes utilisateurs.
La création peut se faire à travers l'interface Web ou bien depuis directement depuis l'API.

La création d'un utilisateur nécessite à minima de préciser: 
 - un nom d'utilisateur
 - un mot de passe
 - son niveau d'accès (administrateur, testeur)
 - les projets autorisés

.. note:: Si une adresse email est précisée, alors il est possible de recevoir les résultats des tests automatiquement dans sa boite mail.

.. warning: Ne pas oublier de modifier les mots de passes des utilisateurs ``admin`` et ``tester``, par défaut ils n'ont pas de mot de passe.

Projets
~~~~~~~

Les tests peuvent être organisés par projet.
L'ajout ou la suppression de projet peut se faire depuis l'interface web ou directement depuis l'api REST.

.. note:: Le projet ``Common`` existe par défaut et accessible par l'ensemble des utilisateurs, il ne peut pas être supprimé.

Partie système
--------------

La partie système système permet de voir le status du serveur.