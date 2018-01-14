Client lourd
============

Le client lourd permet d'écrire et d'exécuter des tests automatiques mais aussi d'analyser
les résultats en temps réel ou différé. Il permet aussi de partager les tests de manière simple et efficace.
Pour utiliser le client, il faut obligatoire un compte utilisateur et se connecter au serveur de test (tcp/443).

Le client peut aussi être utilisé pour effectuer le développement des extensions (adaptateurs et librairies) 
permettants de communiquer avec le système à tester ou piloter.

Enfin l'interface graphique change en fonction du niveau d'accès:
 - niveau testeur: écriture/exécution de tests, et analyse des résultats
 - niveau admin: accès à l'ensemble des fonctionnalités

L'interface se divise en 3 parties principales:
 - l'espace de travail
 - l'analyseur
 - l'explorateur
  
.. note:: Le client est disponible sur Windows et Linux, en mode 64bits

.. image:: /_static/images/client/workspace.png
 
L'espace de travail
-------------------

L'espace de travail se décompose en 3 parties principales:
 - l'accès à l'ensemble des dépôts de fichiers
 - l'accès à la conception des tests
 - la documentation en ligne

.. image:: /_static/images/client/workspace_comments.png

Dépôt des tests
~~~~~~~~~~~~~~~

Le client permet d'accéder aux dépôts de tests local et distant.

Le **dépôt local** donne la possibilité de stocker ses tests sur son poste, donc non partagé.
Cette fonctionnalité n'est pas activé par défaut car ce n'est pas dans la phylosophie de la solution de l'utiliser.
Néanmoins le dépôt peut être activé à travers les préférences du client.

.. warning:: Certaines fonctionnalités sont manquantes dans le dépôt local de test, son utilisation n'est pas conseillé!

Le **dépôt distant** permet de stocker ses tests sur le serveur de tests, donc de les partager avec les autres utilisateurs.
L'arborescence se compose de fichiers et répertoires. La gestion des tests peut se faire depuis le client.
Les tests peuvent être organisés par projet si nécessaire.

.. image:: /_static/images/client/workspace_remote_tests.png

.. note:: Le projet "Common" contient les tests réutisables et divers exemples.

.. note:: Les répertoires "Recycle" et "Sandbox" sont des répertoires réservés, les supprimer est impossible.

Dépôt des extensions
~~~~~~~~~~~~~~~~~~~~

Le client peut être utilisé pour développer les extensions. Il permet l'accès aux dépôts des adaptateurs et librairies.
Les extensions sont organisées par version.

.. image:: /_static/images/client/workspace_remote_adapters.png

.. note:: Les extensions sont développées en Python.

Propriétés d'un test
~~~~~~~~~~~~~~~~~~~~

Les tests peuvent être enrichis avec un certain nombre de propriétés. 
Les propriétés disponibles sont: 
 - la description du test (auteur, date de création, etc...)
 - les variables entrantes et sortantes
 - la définition des agents et sondes utilisés par le test

La fenêtre 'Test properties > Test Data > Inputs' contient la liste des varaiables accessible depuis le test.
L'ajout de variable peut se faire en faisant un clic droit 'Add parameter'.

.. image:: /_static/images/client/workspace_tests_properties_inputs.png

.. note:: 
 Il est possible de choisir la version des adaptateurs et librairies à utiliser pour le test
 
 .. image:: /_static/images/client/workspace_tests_properties.png

Conception graphique
~~~~~~~~~~~~~~~~~~~~

La conception d'un test sous forme graphique est possible avec le test de type "abstract".
Ce type de test ne nécessite aucune connaissance en développement. 

.. image:: /_static/images/client/workspace_new_test_abstract.png

Un clic droit sur la zone de dessin permet de choisir l'élement à ajouter.

.. image:: /_static/images/client/workspace_test_abstract.png


Conception textuel
~~~~~~~~~~~~~~~~~~

La conception d'un test en mode "scripting" est possible avec le test de type "unit" et "suite". 
Ce type d'écrire nécessite des connaissances en développement.

.. image:: /_static/images/client/workspace_new_test_unit_suite.png

Le test de type "unit" représente un cas de test. Il se découpe en 4 sections appélés automatiquement par le framework.

.. image:: /_static/images/client/workspace_test_unit.png

Le test de type "suite représente un cas de test ou plusieurs. Ce type de test permet d'exécuter plusieurs fois le même 
cas de test en changeant les paramètres d'entrés.

.. image:: /_static/images/client/workspace_test_suite.png

.. note:: le raccourci Ctrl+F permet de rechercher du texte dans vos tests

Conception assisté
~~~~~~~~~~~~~~~~~~

L'assistant de conception permet d'écrire des tests sans connaissance en développement.
Il couvre les différents actions possibles:
 - Appel aux fonctions de base du framework de test
 - Test SSH
 - Test d'application avec capture d'écran (basé sur le projet Sikuli)
 - Test de site internet (basé sur le projet Selenium)
 - Test d'application mobile Android
 
Conception conditionnel
~~~~~~~~~~~~~~~~~~~~~~~

La conception conditionnel permet de construire des scénarios de tests ou des campagnes.
Cette approche ne nécessite pas de connaissance en développement. 
Pour réaliser ce type de test, il est nécessaire de créer un nouveau test "plan" ou "global".

.. image:: /_static/images/client/workspace_new_test_plan_global.png

Le test "plan" permet d'écrire des scénarios de test en incluant des tests de type "abstract", "unit" ou "suite".

.. image:: /_static/images/client/workspace_test_plan.png

Le test "global" permet de décrire des campagnes de tests en incluant des tests "plan", "abstract", "unit" ou "suite".

.. note:: Il est possible de surcharger les paramètres de tests.

Documentations en ligne
~~~~~~~~~~~~~~~~~~~~~~~


L'analyseur
-----------

L'explorateur
-------------

Visualisation des résultats
~~~~~~~~~~~~~~~~~~~~~~~~~~

Visualisation des rapports de tests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Préférences de configuration
---------------------------

Compléments
-----------