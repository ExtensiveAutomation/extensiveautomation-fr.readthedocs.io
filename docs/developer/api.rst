API
===

Authentification
----------------

Il y a 2 méthodes pour s'authentifier sur l'API REST:
 - En utilisant un cookie de session
 - En réalisant une authentification basic
 
Basique
~~~~~~~~

L'authentification basique nécessite d'utiliser une clé API.
Cette clé API peut être générée depuis le serveur de test en appelant le script ``/opt/xtc/current/Scripts/generate-apikey.py``

.. code-block:: bash
  
  ./generate-apikey.py --user=admin
  API Key ID: admin
  API Key Secret: c025e7a501f144a2e1b40f9f3a91c10a47c8b1d3
  API Key: YWRtaW46YzAyNWU3YTUwMWYxNDRhMmUxYjQwZjlmM2E5MWMxMGE0N2M4YjFkMw==

Il faut ensuite ajouter l'header `Authorization` dans l'ensemble des requêtes.

.. code-block:: bash

  Authorization: Basic <mon_api_key>

.. note:: Avec le mode Basic Auth, il n'est pas nécessaire d'appeler la fonction login.

Cookie de session
~~~~~~~~~~~~~~~~~

L'authentification par cookie nécessite d'appeler en prérequis la fonction `login` pour générer un cookie de session.
Ce cookie doit être ensuite fournit à l'ensemble des requêtes dans l'header `Cookie`.

.. code-block:: bash

  Cookie: session_id=NjQyOTVmOWNlMDgyNGQ2MjlkNzAzNDdjNTQ3ODU5MmU5M
  
Exemple d'utilisation
----------------

Exemple avec postman ??

Ressources
----------

Description des fonctions les plus importantes:

**Authentification**

+-------------------------+----------------------------------------------------------------------------------------------------+
|/rest/session/login      | `Détails <https://demo.extensivetesting.org/web/common-api-rest/index.html#api-Session-sessionLogin>`_          |
+-------------------------+----------------------------------------------------------------------------------------------------+
|/rest/session/logout     | `Détails <https://demo.extensivetesting.org/web/common-api-rest/index.html#api-Session-sessionLogout>`_         |
+-------------------------+----------------------------------------------------------------------------------------------------+

.. note:: la fonction ``login`` ne nécessite aucune authentification.

**Exécution d'un test**

+-------------------------+----------------------------------------------------------------------------------------------------+
|/rest/tests/schedule     | `Détails <https://demo.extensivetesting.org/web/tester-api-rest/index.html#api-Tests-testsSchedule>`_           |
+-------------------------+----------------------------------------------------------------------------------------------------+
|/rest/tests/schedule/tpg | `Détails <https://demo.extensivetesting.org/web/tester-api-rest/index.html#api-Tests-testsScheduleTpg>`_        |
+-------------------------+----------------------------------------------------------------------------------------------------+

**Récupération des résultats**

+-------------------------+----------------------------------------------------------------------------------------------------+
|/rest/results/reports    | `Détails <https://demo.extensivetesting.org/web/tester-api-rest/index.html#api-Reports-resultsReports>`_        |
+-------------------------+----------------------------------------------------------------------------------------------------+
|/rest/results/status     | `Détails <https://demo.extensivetesting.org/web/tester-api-rest/index.html#api-Results-resultsStatus>`_         |
+-------------------------+----------------------------------------------------------------------------------------------------+
|/rest/results/verdict    | `Détails <https://demo.extensivetesting.org/web/tester-api-rest/index.html#api-Results-resultsVerdict>`_        |
+-------------------------+----------------------------------------------------------------------------------------------------+



















