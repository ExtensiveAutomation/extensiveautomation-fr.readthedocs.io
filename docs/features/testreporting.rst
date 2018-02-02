La traçabilité
===========

Les évènements
----------

L'exécution d'un test se découpe en évènements, l'ensemble de ces évènements sont stockés et peuvent être visualisés après coup.
Un évènement peut représenter: 
 - une action effectuée par le framework de test
 - une action effectuée par le test
 - une donnée reçue par le système à tester ou contrôler.
 - une donnée à envoyer au système à tester ou contrôler.

L'exécution évènementielle permet d'avoir des tests robustes grâce à la définition des intervalles d'observations.
L'approche consiste à écrire les tests avec le formalisme suivant:
 - J'exécute une action dans mon test.
 - Pendant un interval donné, je regarde et compare tous les évènements reçues avec un attendu.
 - Je décide de l'action suivante
    * après avoir reçu l'évènement que j'attendais
    * ou bien quand l'intervalle d'observation est terminé.

Durant l'exécution d'un test, le framework capture tous les évènements générés par le système testé ou piloté.
Les évènements sont ensuite convertis et stockés dans un message appelé ``modèle``.

Un ``modèle`` se découpe en une ou plusieurs ``couches``.
Une ``couche`` se définit par un ensemble de clé/valeur. La valeur d'une couche
peut être une autre couche aussi.
 
.. image:: /_static/images/testlibrary/template_message.png

Création d'un modèle
~~~~~~~~~~~~~

La création d'un modèle peut se faire en utilisant le framework de test ``TestTemplates``.

.. code-block:: python
  
  tpl = TestTemplates.TemplateMessage()
  layer = TestTemplates.TemplateLayer(name='response')
  layer.addKey(name='code', data='200')
  layer.addKey(name='msg', data='hello world')
  tpl.addLayer(layer=layer) 
  
Ce modèle indique que l'évènement devra contenir:
 - une couche s'appelant `response` et contenant la clé `code` et `msg`
 - la clé code devra être strictement égale à la valeur 500
 - la clé msg devra être strictement égale au texte hello world.
 
Exemple d'un message attendu visible depuis le client graphique:

.. image:: /_static/images/testlibrary/template_expected.png

Les opérateurs
~~~~~~~~~~~~~

Des opérateurs sont disponibles pour faciliter la comparaison des modèles reçus.

+-----------------+-------------------------------------------------------------------+
|Nom              |   Description                                                     |
+-----------------+-------------------------------------------------------------------+
| Any             | Accepte toute les valeurs                                         |
+-----------------+-------------------------------------------------------------------+
| Contains        | Vérifie si la chaîne de caractères contients des caractères       |
+-----------------+-------------------------------------------------------------------+
| Endswith        | Vérifie si la chaîne de caractères se termine par                 |
+-----------------+-------------------------------------------------------------------+
| Startswith      | Vérifie si la chaîne de caractères commence par                   |
+-----------------+-------------------------------------------------------------------+
| GreaterThan     | Vérifie si un entier est plus grand que                           |
+-----------------+-------------------------------------------------------------------+
| LowerThan       | Vérifie si un entier est plus petit que                           |
+-----------------+-------------------------------------------------------------------+
| RegEx           | Vérifie si la chaîne de caractères répond à l'expression régulière|
+-----------------+-------------------------------------------------------------------+

Exemple de modèle utilisant les opérateurs de comparaison:

.. code-block:: python
  
  tpl = TestTemplates.TemplateMessage()
  layer = TestTemplates.TemplateLayer(name='response')
  layer.addKey(name='code', data=TestOperators.LowerThan(x=500)))
  layer.addKey(name='msg', data=TestOperators.Contains(x="hello"))
  tpl.addLayer(layer=layer) 
  
Ce modèle indique que l'évènement devra contenir:
 - une couche s'appelant `response` et contenant la clé `code` et `msg`
 - la clé code devra être inférieur à la valeur 500
 - la clé msg devra contenir le texte hello.
 
La visualisation
~~~~~~~~~~~~~

Le client permet de visualiser graphiquement la comparaison effectuée par le framework.

.. image:: /_static/images/client/client_event_mismatch.png

Définition du code couleur:

+-----------------+------------------------------------------------------------------+
|Vert             |   Correspondance parfaite entre la valeur reçue et attendue      |
+-----------------+------------------------------------------------------------------+
|Rouge            |   La valeur reçue ne correspond pas à la valeur attendue         |
+-----------------+------------------------------------------------------------------+
|Jaune            |   La valeur attendue n'a pas été vérifiée                        |
+-----------------+------------------------------------------------------------------+

Les rapports de tests
-----------------

Après chaque exécution d'un test, le framework génère automatiquement les rapports de tests associés.

Il existe 2 type rapports:
 - Un rapport avancé
 - Un rapport basique (accessible par défaut depuis le client graphique)

Les rapports sont accessibles depuis le client, l'interface web ou bien depuis l'API.

.. note:: Les rapports peuvent être exportés au format html, csv, xml et pdf.

Rapport avancé
~~~~~~~~~~~~~~

Le rapport avancé affiche un certain nombre de paramètres:
 - la durée d'exécution de chaque cas de test
 - la description complète des étapes de test.
 - des statistiques sur l'exécution.
 - des paramètres de tests.
 
.. image:: /_static/images/testlibrary/advanced_report.png


Il est possible d'afficher des variables dans le rapport de test en préfixant les variables:

- ``SUT_``		Variables décrivant la version du système à tester ou piloter
- ``DATA_``		Variables décrivant des données spécifiques
- ``USER_``		Variables utilisateurs

Cette fonctionnalité peut être utile pour augmenter le niveau de traçabilité dans les rapports.

.. image:: /_static/images/testlibrary/inputs_sut.png
  
.. image:: /_static/images/testlibrary/report_inputs.png

Rapport basique
~~~~~~~~~~~~~~~

Le rapport basique résume le résultat de l'ensemble des cas de tests et des états.

.. image:: /_static/images/testlibrary/basic_report.png


Code couleur:

+-----------------+------------------------------------------------------------------+
|Vert             |   Le cas de test est valide                                      |
+-----------------+------------------------------------------------------------------+
|Rouge            |   Le cas de test est en erreur                                   |
+-----------------+------------------------------------------------------------------+
|Orange           |   Le résultat du cas de test n'est pas déterminé                 |
+-----------------+------------------------------------------------------------------+
|Gris             |   Le cas de test n'a pas été exécuté                             |
+-----------------+------------------------------------------------------------------+


.. tip:: Il faut cliquer sur les cas de tests pour afficher les étapes.

.. note:: 
  Les messages affichés par le test avec la fonction ``Trace(self).info()`` sont disponibles dans le 
  rapport en cliquant sur le lien ``[logs details]``.
  
  Les erreurs sont aussi affichées en cliquant sur le lien ``[errors details]``.


Les logs
----

Le framework permet d'enregistrer des logs durants l'exécution d'un test
et de les mettre à disposition rapidement auprès de l'utilisations. L'ensemble des logs supplémentaires sont zippés et accessibles depuis le client lourd ou bien l'API.

.. image:: /_static/images/testlibrary/private_storage.png

.. note:: Pour plus de détaills, il faut lire le chapitre `Les fondamentaux >> Données`.
