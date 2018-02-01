Client lourd
============

Le client lourd permet d'écrire et d'exécuter des tests automatiques mais aussi d'analyser
les résultats en temps réel ou différé. Il permet aussi de partager les tests de manière simple et efficace.
Pour utiliser le client, il faut obligatoirement un compte utilisateur et pouvoir se connecter au serveur de test (tcp/443).

Le client peut aussi être utilisé pour effectuer le développement des extensions (adaptateurs et librairies) 
permettant de communiquer avec le système à tester ou piloter.

Enfin l'interface graphique change en fonction du niveau d'accès:
 - niveau testeur: écriture/exécution de tests, et analyse des résultats
 - niveau admin: accès à l'ensemble des fonctionnalités

L'interface se divise en 3 parties principales:
 - l'espace de travail
 - l'analyseur
 - l'explorateur

.. image:: /_static/images/client/workspace.png
   
.. note:: Le client est disponible sur Windows et Linux, en mode 64bits

L'espace de travail
-------------------

L'espace de travail se décompose en 3 parties principales:
 - l'accès à l'ensemble des dépôts de fichiers
 - l'accès à la conception des tests
 - la documentation en ligne

.. image:: /_static/images/client/workspace_comments.png

Dépôt des tests
~~~~~~~~~~~~~~~

Le client permet d'accéder aux deux dépôts de tests: distant et local.

Le ``dépôt distant`` permet de stocker ses tests sur le serveur de tests, donc de les partager avec les autres utilisateurs.
L'arborescence se compose de fichiers et répertoires. La gestion des tests peut se faire depuis le client.
Les tests peuvent être organisés par projet si nécessaire.

.. image:: /_static/images/client/workspace_remote_tests.png

.. note:: Le projet ``Common`` contient les tests réutisables et divers exemples.

.. note:: Les répertoires ``Recycle`` et ``Sandbox`` sont des répertoires réservés, les supprimer est impossible.

.. note:: Il est possible d'ouvrir un test en faisant un drag and drop du fichier vers l'espace d'écriture.

Le **dépôt local** donne la possibilité de stocker ses tests sur son poste, donc non partagé.
Cette fonctionnalité n'est pas activée par défaut car ce n'est pas dans la philosophie de la solution de l'utiliser.
Néanmoins le dépôt peut être activé à travers les préférences du client.

.. warning:: Certaines fonctionnalités sont manquantes dans le dépôt local, son utilisation n'est pas conseillée!


Dépôt des extensions
~~~~~~~~~~~~~~~~~~~~

Le client permet l'accès aux dépôts des extensions (adaptateurs et librairies) et peut aussi être utilisé pour en développer des nouvelles, 
qui seront stockées là aussi. Ces extensions sont organisées par version.

.. image:: /_static/images/client/workspace_remote_adapters.png

.. note:: Les extensions sont développées en ``Python``.

..
	Il faut une explication des raisons pour créer une nouvelle extension, comment faire, 
	et comment l'intégrer au dépôt, comment les gérer (versions), les règles de nomenclature

Propriétés d'un test
~~~~~~~~~~~~~~~~~~~~

Les tests peuvent être enrichis avec un certain nombre de propriétés. 
Les propriétés disponibles sont: 
 - la description du test (auteur, date de création, etc...)
 - les variables entrantes et sortantes
 - la définition des agents et sondes utilisées par le test
 
La fenêtre ``Test properties > Test Data > Inputs`` contient la liste des variables accessibles depuis le test.
L'ajout de variable peut se faire en faisant un clic droit 'Add parameter'.

.. image:: /_static/images/client/workspace_tests_properties_inputs.png

.. note:: Pour insérer un paramètre dans un test, il suffit de faire un drag & drop.

.. note:: 
 Il est possible de choisir la version des adaptateurs et librairies à utiliser pour le test
 
 .. image:: /_static/images/client/workspace_tests_properties.png

Conception graphique
~~~~~~~~~~~~~~~~~~~~

La conception d'un test sous forme graphique est possible avec le test de type ``abstract``.
Ce mode de conception ne nécessite aucune connaissance en développement. 

.. image:: /_static/images/client/workspace_new_test_abstract.png

Un clic droit sur la zone de dessin permet de choisir l'élement à ajouter.

.. image:: /_static/images/client/workspace_test_abstract.png


Conception textuelle
~~~~~~~~~~~~~~~~~~~~

La conception d'un test en mode ``scripting`` est possible avec led testd de type ``unit`` et ``suite``. 
Ce mode de conception nécessite des connaissances en développement, i.e. python.

.. image:: /_static/images/client/workspace_new_test_unit_suite.png

Le test de type ``unit`` représente un cas de test. Il se découpe en 4 sections appelées automatiquement par le framework.

.. image:: /_static/images/client/workspace_test_unit.png

Le test de type "suite" représente un ou plusieurs cas de test. Ce type de test permet d'exécuter plusieurs fois le même 
cas de test en changeant les paramètres d'entrées.

.. image:: /_static/images/client/workspace_test_suite.png

.. note:: Le raccourci ``Ctrl+F`` permet de rechercher du texte dans vos tests.

Conception assistée
~~~~~~~~~~~~~~~~~~~

L'assistant de conception permet d'écrire des tests sans connaissances en développement.
Il couvre les différentes actions suivantes:
 - Appel aux fonctions de base du framework de test
 - Test SSH
 - Test d'application avec capture d'écran (basé sur le projet Sikuli)
 - Test de site internet (basé sur le projet Selenium)
 - Test d'application mobile Android

L'assistant consiste à décrire les actions à effectuer, et si désiré les exporter vers un test unit ou suite.

.. image:: /_static/images/client/workspace_assistant.png

Conception conditionnelle
~~~~~~~~~~~~~~~~~~~~~~~~~

La conception conditionnelle permet de construire des scénarios ou des campagnes de tests.
Cette approche ne nécessite pas de connaissances en développement. 
Pour réaliser ce type de test, il est nécessaire de créer un nouveau test ``plan`` ou ``global``.

.. image:: /_static/images/client/workspace_new_test_plan_global.png

Le test "plan" permet d'écrire des scénarios de test en incluant des tests de type "abstract", "unit" ou "suite".

.. image:: /_static/images/client/workspace_test_plan.png

Le test "global" permet de décrire des campagnes de tests en incluant des tests "plan", "abstract", "unit" ou "suite".

.. note:: Il est possible de surcharger les paramètres de tests.

Documentations en ligne
~~~~~~~~~~~~~~~~~~~~~~~

La documentation en ligne est générée par le serveur, elle décrit l'ensemble des fonctions disponibles 
dans le framework de test et les différentes extensions.

.. image:: /_static/images/client/workspace_help_online.png

.. note:: Un drag & drop depuis la documentation sur un test insère automatiquement le squelette de la fonction.

L'analyseur
-----------

L'analyseur permet de suivre l'exécution d'un test en temps réél ou différé. 
Il permet d'afficher l'ensemble des évènements du test et de faciliter l'analyse du bon déroulement ou des erreurs.

.. image:: /_static/images/client/analyseur.png

Visualisation des évènements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Différents types d'évènements sont possibles (colonne event type):

 - DEBUG
 - INFO
 - WARNING
 - ERROR
 
 - SEND
 - RECEIVED
 
 - STEP-STARTED
 - STEP-PASSED
 - STEP-FAILED
 
 - MATCH-STARTED
 - MATCH-INFO
 - MATCH-STOPPED
 - MATCH-EXCEEDED

.. note:: Filtrer sur l'évènement ``ERROR`` permet de voir rapidement pourquoi le test est en erreur. 

.. note:: Le filtre ``SEND|RECEIVED`` permet d'afficher les messages envoyés ou reçus par le système à tester/piloter. 

Vue détaillée
~~~~~~~~~~~~~

Sélectionner un évènement dans la liste permet d'afficher la vue détaillée.
La vue détaillée affiche le contenu de l'évènement et plus encore.

.. image:: /_static/images/client/analyseur_details.png

L'explorateur
-------------

Visualisation des résultats
~~~~~~~~~~~~~~~~~~~~~~~~~~

L'historique complet des résultats de tests est disponible depuis le client.
Ils sont triés par date et heure d'exécution. 
Le client permet d'afficher les rapports et télécharger les logs générés durant l'exécution du test.

.. image:: /_static/images/client/explorer_historique.png

Visualisation des rapports de tests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Les rapports de tests sont visibles directement depuis le client. 
Deux types de rapports sont disponibles:
 - rapport avancé
 - rapport simple
 
.. image:: /_static/images/client/explorer_rapport.png

.. note:: Les rapports sont exportables aux formats html, xml et csv.

Préférences de configuration
----------------------------

Le comportement du client peut être modifié à travers les préférences du client.

.. image:: /_static/images/client/preferences.png

.. note:: Les préférences sont stockées dans le fichier ``settings.ini`` .

Compléments
-----------

Il est possible d'ajouter des plugins dans le client. Les plugins sont à ajouter dans le répertoire ``Plugins``.

.. image:: /_static/images/client/plugins_client_install.png

Les plugins sont accessibles dans le menu ``Plugins`` après redémarrage du client.

.. image:: /_static/images/client/ite_plugins_menu.png

.. note:: Il est nécessaire de redémarrer le client pour prendre en compte les plugins déployés.

Plugin HP ALM
~~~~~~~~~~~~~~

Le plugin ``HP ALM`` permet d'exporter les tests et résultats depuis le client Extensive vers HP ALM QualityCenter.
Cette approche permet d'être autonome vis à vis de QC.

La configuration du plugin se fait dans la page ``Settings``, il faut configurer à minima:
 - nom d'utilisateur
 - le mot de passe
 - le domaine
 - le projet

Pour exporter un test, il faut générer le design d'un test depuis le client et cliquer sur le plugin HP ALM disponible dans la barre d'outils.

.. image:: /_static/images/client/qc_plugin.png

L'export des résultats peut se faire depuis la fenêtre exploration des archives,
Le plugin doit être disponible dans la barre d'outil lors qu'un rapport de test est chargé.
 
.. note:: Le plugin est compatible avec un HP ALM QC >= 12, l'api REST est utilisée.

Plugin Jenkins
~~~~~~~~~~~~~~

Le plugin ``Jenkins`` ne fait pas grand chose dans cette version...
Il fournit juste un lien vers l'interface web de son Jenkins préféré.


Plugin Shell Recorder
~~~~~~~~~~~~~~~~~~~~~~

Le plugin ``Shell Recorder`` permet d'importer une séquence de commandes shell dans l'assistant de conception et de générer le test associé.
Il permet donc de rejouer facilement une séquence de commandes.

La 1ière étape consiste à importer une session ssh (depuis un terminal putty par exemple) depuis le presse papier
ou en important directement un fichier texte contenant la séquence des commandes shell.

Le plugin détecte automatiquement le prompt dans la séquence pour parser les commandes et résultats associés.
Si le prompt n'est pas détecté, il est possible de le modifier manuellement.

.. image:: /_static/images/client_plugins/plugin_shell_recorder.png

Plugin SeleniumIDE
~~~~~~~~~~~~~~~~~~

L'utilisation du plugin ``SeleniumIDE`` implique une utilisation basique. Il permet de convertire un fichier enregistré avec le plugin SeleniumIDE de firefox 
dans l'assistant de conception.

.. tip:: Il est plus efficace d'utiliser l'assistant en direct pour être en phase avec la philosophie de la solution.