Gestion de la traçabilité
==========================

Exécution évènementielle
-----------------------

L'exécution évènementielle permet d'avoir des tests robustes grâce à la définition des intervalles d'observations.
L'approche consiste à écrire les tests avec le formalisme suivant:
 - J'exécute une action dans mon test.
 - Pendant un interval donné, je regarde et compare tous les évènements reçues avec un attendu.
 - Je décide de l'action suivante
    * après avoir reçu l'évènement que j'attendais
    * ou bien quand l'intervalle d'observation est terminé.

Durant l'exécution d'un test, le framework capture tous les évènements générés par le système testé ou piloté.
Les évènements sont ensuite convertis et stockés dans un message.

.. image:: /_static/images/testlibrary/template_message.png
  
Des opérateurs sont disponibles pour faciliter la comparaison des messages reçus.

+-----------------+------------------------------------------------------------------+
|Nom              |   Description                                                    |
+-----------------+------------------------------------------------------------------+
| Any             | Accepte toute les valeurs                                        |
+-----------------+------------------------------------------------------------------+
| Contains        | Vérifie si la chaine de caractère contients des caractères       |
+-----------------+------------------------------------------------------------------+
| Endswith        | Vérifie si la chaine de caractère se termine par                 |
+-----------------+------------------------------------------------------------------+
| Startswith      | Vérifie si la chaine de caractère commence par                   |
+-----------------+------------------------------------------------------------------+
| GreaterThan     | Vérifie si un entier est plus grand que                          |
+-----------------+------------------------------------------------------------------+
| LowerThan       | Vérifie si un entier est plus petit que                          |
+-----------------+------------------------------------------------------------------+
| RegEx           | Vérifie si la chaine de caractère répond à l'expression régulière|
+-----------------+------------------------------------------------------------------+

.. image:: /_static/images/testlibrary/template_expected.png
 

Le client permet de visualiser graphiquement la comparaison effectuée par le framework.
Définition du code couleur:

+-----------------+------------------------------------------------------------------+
|Vert             |   Correspondance parfaite entre la valeur reçue et attendue      |
+-----------------+------------------------------------------------------------------+
|Rouge            |   La valeur reçue ne correspond pas à la valeur attendue         |
+-----------------+------------------------------------------------------------------+
|Jaune            |   La valeur attendue n'a pas été vérifié                         |
+-----------------+------------------------------------------------------------------+

.. image:: /_static/images/client/client_event_mismatch.png


Génération des rapports
-----------------------

Après chaque exécution d'un test, le framework génère automatiquement les rapports de tests associés.
Il existe 2 type rapports:
 - Rapport avancé
 - Rapport basique

Les rapports sont accessibles depuis le client, l'interface web ou bien depuis l'API.

.. notes:: Les rapports peuvent être exportés au format html, csv, xml et pdf.

Rapport avancée
~~~~~~~~~~~~~~~

.. image:: /_static/images/testlibrary/advanced_report.png

Rapport basique
~~~~~~~~~~~~~~~

.. image:: /_static/images/testlibrary/basic_report.png

Accès aux logs complémentaires
------------------------------

Le framework permet d'enregistre des logs durants l'exécution d'un test.
Ils sont ensuite accessibles depuis le client lourd ou bien l'API.

<insérer image du client>