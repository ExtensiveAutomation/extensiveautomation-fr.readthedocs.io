Tests réutilisables
===================

Les tests réutilisables sont à utiliser en mode test "plan". 
L'intérêt premier est de pouvoir réutiliser des morceaux de tests dans le but de créer des scénarios.

Données partagées
-----------------

Mise en cache d'une valeur
~~~~~~~~~~~~~~~~~~~~~~~~~~

Ce test réutilisable conciste à sauvegarder une valeur dans le cache de données disponible durant l'exécution d'un texte.

Les paramètres à configurer:
 - DATAS
 
# Sauvegarde d'une valeur.
[!TO:CACHE:<NOM_DE_LA_CLE>:];ma valeur

# Mise en cache d'un paramètre
[!TO:CACHE:<NOM_DE_LA_CLE:];[!FROM:INPUT:<MON_PARAMETRE:]

.. note:: Il est possible de sauvegarder plusieurs valeurs avec ce test.


Affichage d'une valeur
~~~~~~~~~~~~~~~~~~~~~~

Ce test réutilisable permet d'afficher la valeur d'une clé présente dans le cache durant l'exécution du test.

Les paramètres à configurer:
 - MESSAGES
 
# ma valeur à afficher 
[!FROM:CACHE:<NOM_DE_LA_CLE>:]

.. note:: Il est possible d'afficher plusieurs valeurs en une seule fois

Reset du cache
~~~~~~~~~~~~~~

Ce test réutilisable permet de vider totalement le cache.
Aucun paramètre à configurer.

.. note:: Ce test peut être utilise lorsque plusieurs scénarios sont enchainés dans un test global.

Vérification d'une valeur dans le cache
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Actions basiques
----------------

Générateurs
-----------

Protocoles réseaux
------------------

Interface utilisateur
---------------------

Vérifications
-------------