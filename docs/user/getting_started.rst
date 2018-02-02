Première utilisation (script)
=============================

Connexion du client au serveur
------------------------------

Après avoir ouvert le client, la première étape consiste à se connecter au serveur de test.
Pour ce faire il faut avoir à disposition son compte utilisateur ainsi que l'adresse du serveur.

La fenêtre de connexion est disponible depuis le menu ``Get Started > Connect`` ou bien directement sur la page d'accueil.
Une fois la connexion réussie, l'utilisateur peut accéder à l'ensemble des tests automatiques existant sur le serveur.

.. image:: /_static/images/client/client_connect.png

.. note:: L'utilisateur ``admin`` peut être utilisé dans le cadre de la découverte de la solution.

Écriture d'un test script
---------------------------------

La première utilisation consiste à créer un très simple premier cas de test en affichant la valeur d'un paramètre du test.

1. Créer un test de type ``Unit``
   
   .. image:: /_static/images/client/client_new_tux.png

2. Ajouter le paramètre MON_PARAMETRE de type ``str`` avec la valeur "bonjour"
   
   .. image:: /_static/images/client/client_new_param.png

3. Modifier le test au niveau de la section ``definition`` pour afficher la valeur du paramètre.
   
   .. image:: /_static/images/client/client_new_trace.png
   
   
   .. note:: 
   
     Il est possible de vérifier la syntaxe du test avant exécution en cliquant sur le bouton ``Syntax``.
       
     .. image:: /_static/images/client/check_syntax.png
   
4. Enregistrer le test dans le dépôt avec le nom "Test_A" dans le répertoire ``Sandbox``
   
   .. image:: /_static/images/client/client_new_save.png

Ecriture d'un scénario
----------------------

.. note:: Ce mini guide part du principe que vous avez suivi le chapitre ``Ecriture d'un test script``.

L'exemple suivant explique comment créer son premier scénario avec une surcharge des variables de tests.

1. Créer un test de type ``Plan``.
   
   .. image:: /_static/images/client/client_new_tpx.png

2. Insérer le test "Test_A" dans le scénario. Cliquer sur le bouton ``Insert Child`` et sélectionner le test `Test_A`.

   .. image:: /_static/images/client/client_new_insert.png

3. Après insertion, cliquer sur le test `Test_A` et insérer de nouveau le même test.

   .. image:: /_static/images/client/client_new_insert_again.png

4. Enregistrer le scénario dans le dépôt de test avec le nom "Scenario_A" dans le répertoire ``Sandbox``.

5. Ajouter le paramètre MON_PARAMETRE avec la valeur "au revoir" au niveau du scénario.

.. tip:: 
  Ne pas hésitez à définir un alias pour le nom du test pour rendre le scénario plus lisible.

  .. image:: /_static/images/client/snippets_alias.png

Exécution d'un test
-------------------

.. note:: Ce mini guide part du principe que vous avez suivi les chapitres `Ecriture d'un test script` et `Ecriture d'un scénario`.

L'exécution d'un test peut se faire en cliquant sur le bouton ``Execute``.
Ouvrir les tests `Test_A` et `Scenario_A` et les exécuter.

.. image:: /_static/images/client/client_execute.png

Analyse des résultats
---------------------

.. note:: Ce mini guide part du principe que vous avez suivi les chapitres `Ecriture d'un test script` et `Ecriture d'un scénario`.


La 1ière fenêtre d'analyse montre l'exécution du test "Test_A" et notamment le message "bonjour".

.. image:: /_static/images/client/test_result_simple.png

La 2ième fenêtre d'analyse montre l'exécution du test "Scenario_A" et notamment le message "au revoir".

.. image:: /_static/images/client/test_result_surcharge.png

Ce premier usage montre comment exécuter un test et un scénario ansi que la surcharge des variables de tests.


Les bonnes pratiques
---------------------

.. tip::

  Pour garder une bonne lisibilité dans les tests de type scripts, il ne faut pas utiliser de `try/except`.
  Le framework intercepte toutes les exceptions à sont niveau.
  
.. tip::
  
  Il faut absolument prendre le temps de déclarer les étapes de tests car ils permettent 
   - de comprendre rapidement le test sans le script.
   - d'avoir des rapports de test pertinants et compréhensible.
   
.. tip::

   Pour faciliter la maintenance de vos tests et les rendres réutilisables, 
   il ne faut pas avoir de valeur en dur dans votre test.
   Il faut systématiquement les mettres en paramètres de tests, c'est fait pour.
   
