Utilisateurs
============

La solution peut être utilisée en mode multi-utilisateur.
Des utilisateurs suivants existent par défaut:
 - ``Admin``
 - ``Tester``
 - ``Monitor``

.. note:: Ne pas oublier de désactiver les comptes par défaut dans un environnement de production.

Ajout d'un utilisateur
----------------------

L'ajout d'un utilisateur peut se faire avec un compte administrateur. 
La création d'un utilisateur nécessite à minima les paramètres suivants et peut se faire via l'interface web ou bien l'API
 - nom d'utilisateur
 - mot de passe

.. image:: /_static/images/webinterface/add_user.png

.. note:: L'email est utilisée par la solution pour envoyer les rapports de tests et résultats.

.. note:: Il est possible de configurer plusieurs adresses email pour un utilisateur en les séparants avec ``;``

Suppression d'un utilisateur
----------------------

La suppression d'un utilisateur peut se faire avec un compte administrateur. 
Cette action peut se faire à travers l'interface web ou bien l'API.

.. image:: /_static/images/webinterface/delete_user.png
