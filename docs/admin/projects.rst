Projets
=======

La solution peut être utilisée en mode multi-projet. Il est donc possible d'organiser les tests par projets et d'accorder des droits d'accès pour les 
utilisateurs.

.. note:: Le projet ``Common`` existe par défaut, il est accessible par l'ensemble des utilisateurs et ne peux pas être supprimé.

Ajout d'un projet
-----------------

L'ajout d'un projet peut se faire avec un compte administrateur. 
La création d'un projet nécessite de préciser son nom et peut se faire via l'interface web ou bien l'API

Suppression d'un projet
----------------------

La suppression d'un projet peut se faire avec un compte administrateur.
Cette action peut se faire à travers l'interface web ou bien l'API.

.. note:: Si le projet est associé à un utilisateur, la suppression n'est pas autorisée.

Associer un projet à un utilisateur
------------------------------------

Un utilisateur peut accéder à plusieurs projets, en fonction des autorisations accordées.
L'autorisation s'effectue depuis le profil d'un utilisateur avec un compte administrateur.
Un administrateur peut sélectionner les projets autorisés, il est aussi possible 
de configurer le projet par défaut, ie. celui qui sera affiché par défaut à la connexion.