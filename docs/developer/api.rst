API
===

Authentification
----------------

Il y a 2 méthodes pour s'authentifier sur l'API REST:
 - En utilisant un cookie de session
 - En réalisant une authentification basique
 
Basique
~~~~~~~~

L'authentification basique nécessite d'utiliser une clé API disponible depuis l'interface web.
La re-génération de la clé se fait pour l'instant en ligne de commande sur le serveur.

.. code-block:: bash
  
  ./extensiveautomation --apikey admin
    API Key ID: admin
    API Key Secret: d30278d49e4845e45daa748873e2171b14a0c55a

Il faut ensuite ajouter l'header ``Authorization`` dans l'ensemble des requêtes avec la clé et le secret encodé en base 64

.. code-block:: bash

  Authorization: Basic base64(key_id:key_secret)

.. note:: Avec l'authentification basique, il n'est pas nécessaire d'appeler la fonction login.

Cookie de session
~~~~~~~~~~~~~~~~~

L'authentification par cookie nécessite d'appeler en prérequis la fonction ``login`` pour générer un cookie de session.
Ce cookie doit être ensuite fournit à l'ensemble des requêtes dans l'entête ``Cookie``.

.. code-block:: bash

  Cookie: session_id=NjQyOTVmOWNlMDgyNGQ2MjlkNzAzNDdjNTQ3ODU5MmU5M
  
Exemple d'utilisation
----------------

L'api est accessible à travers le ``port 443`` (https) du serveur de test via l'uri ``/rest``.

L'exemple ci-dessous montre comment exécuter un test avec une authentification basique.

.. code-block:: json
  
  POST /rest/tests/schedule HTTP/1.1
  [...]
  Authorization: Basic YWRtaW46N2UwMDExY2I3Y2ZhMGQ1MjM4NGQ1YWYyM2QyODBiMjUyM2EzMTA3ZA==
  Content-Type: application/json; charset=utf-8 
  [...]
  
  {
    "project-id": 1,
    "test-extension": "tux",
    "test-name": "01_Wait",
    "test-path": "/Snippets/Do/",
    "test-inputs": [ {"name": "DURATION", "type": "int", "value": 5} ]
  }
  

La réponse reçue:

.. code-block:: json
  
  {
    "cmd": "/tests/schedule",
    "message": "background"
    "test-id": "a3f19398-b463-41e8-9e43-af86aac44a59",
    "task-id": 17,
    "tab-id": 0
    "test-name": "01_Wait"
  }
  


Ressources
----------

Description des fonctions les plus importantes:

**Authentification**

+-------------------------+--------------------------------------------------------+
|/rest/session/login      |      |
+-------------------------+--------------------------------------------------------+
|/rest/session/logout     |     |
+-------------------------+--------------------------------------------------------+

.. note:: La fonction ``login`` ne nécessite aucune authentification.

**Exécution d'un test**

+-------------------------+--------------------------------------------------------------+
|/rest/tests/schedule     |       |
+-------------------------+--------------------------------------------------------------+
|/rest/tests/schedule/tpg |   |
+-------------------------+--------------------------------------------------------------+

**Récupération des résultats**

+-------------------------+------------------------------------------------------------------------------+
|/rest/results/reports    |   |
+-------------------------+------------------------------------------------------------------------------+
|/rest/results/status     |   |
+-------------------------+------------------------------------------------------------------------------+
|/rest/results/verdict    |  |
+-------------------------+------------------------------------------------------------------------------+



















