Exemples de tests
=================

Cas de test (unit)
-----------

Cette exemple montre comment utiliser un cas de test simple.
Un cas de test se compose de 4 sections exécutées automatiquement par le framework de test ainsi que les paramètres de tests associés.

.. image:: /_static/images/client/exemple_testunit.png

Cas de test (suite)
-----------

Une suite de test permet d'éxécuter à la suite plusieurs cas de test.
L'exemple montre comment boucler sur un cas de test tout en modifiant les données entrantes.

.. image:: /_static/images/client/exemple_testsuite.png

Il est donc possible d'ajouter autant d'argument que nécessaire au niveau de la fonction `execute`
et de les ajouter à l'identiquer au niveau des 4 sections.

.. notes:: Il est possible d'ajouter un préfixe au niveau du cas du test en utilisant l'argument `prefix`.

Variables de test
----------------

Les variables sont utilisables depuis un test, il en existe plusieurs types.
L'exemple ci-dessous montre comment récupèrer un paramètre depuis son test.

Un paramètre de test peut être récupéré au niveau du test en utilisant la fonction `input`.
Le nom du paramètre à récupérer est à préciser.

.. image:: /_static/images/client/exemple_variables.png

.. tip: Essayez de prendre l'habitude de mettre systèmatiquement en variable l'ensemble des valeurs présentes dans le test pour faciliter la maintenance.

Scénario
--------

Un scénario permet d'exécuter plusieurs cas de tests à la suite avec des conditions de résultats entre eux.
Il est possible de surchager les paramètres de tests au niveau du scénario.

.. image:: /_static/images/client/exemple_testplan.png

Campagne de test
----------------

Une campagne permet d'exécuter plusieurs scénarios. Il est possible de surcharger les paramètres de tests
au niveau des paramètres de la campagne.

.. image:: /_static/images/client/exemple_testglobal.png

Rest API
--------

L'exemple suivant montre comment réaliser des tests d'une API REST.
Pour ce faire les tests réutisables sont utilisés.

Contrôles SSH
-------------

L'exemple suivant montre comment réaliser des tests d'une API REST.
Pour ce faire les tests réutisables sont utilisés.

Navigateurs Internet
--------------------

L'exemple suivant montre comment utiliser l'assistant pour écrire un test d'une application web

Mobile Android
--------------
L'exemple suivant montre comment utiliser l'assistant pour écrire un test d'une application mobile
