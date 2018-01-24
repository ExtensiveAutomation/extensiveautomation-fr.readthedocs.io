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

.. note:: Il est possible d'ajouter un préfixe au niveau du cas du test en utilisant l'argument `prefix`.

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
Il est possible de surcharger les paramètres de tests au niveau du scénario.

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


Exemple:
 
Le test appelle le service httpbin.org en https et appelle le service `ip` qui permet d'obtenir l'ip réel du client en json.

.. image:: /_static/images/examples/rest_api.png

Le scénario se décompose en plusieurs étapes:
 1. Préparation de l'environnement: description de l'environnement testé (adresse, port réseaux, etc...)
    L'environnement est configuré dans le paramètre `ENVIRONMENT` du test `PREPARE ENVIRONMENT` (Id=5)
   .. code-block:: json
   
       {
        "PLATFORM": {
            "CLUSTER": [
                { "NODE": {
                            "COMMON": {
                                "HOSTNAME": "httpbin"
                            },
                            "INSTANCES": {
                                "HTTP": {
                                    "REST": {
                                        "HTTP_DEST_HOST": "httpbin.org",
                                        "HTTP_DEST_PORT": 443,
                                        "HTTP_DEST_SSL": true,
                                        "HTTP_HOSTNAME": "httpbin.org",
                                        "HTTP_AGENT_SUPPORT": false,
                                        "HTTP_AGENT": null
                                    }
                                }
                            }
                         }
                    }
            ]
        },
        "DATASET": [    ]
        }
 2. Si la préparation de l'environnement ne fonction pas alors le scénario est arrété en appelant le test
 réutilisable `Snippets/Do/02_Terminate` (Id=16)

 3. On envoit une requête REST et on décrit la réponse attendue en utilisant le test réutilisable `/Snippets/Protocols/04_Send_JSON` (Id=30). 
 Si cette étape ne fonctionne pas alors on annule le test (Id=31)
 
 La réponse reçue est vérifiée par le framework et ce qui a été décrit par le testeur dans le paramètre `HTTP_RSP_BODY`
 
 .. code-block:: json
 
   origin		[!CAPTURE:EXTERNAL_IP:]
   
 La configuration indique qu'il faut vérifier dans la réponse que la clé `origin` est présente et 
 d'enregistrer la valeur dans le cache avec la clé `EXTERNAL_IP`
 
 4. On affiche la valeur reçue dans la réponse avec le test réutilisable `Snippets/Cache/02_Log_Cache` (Id=32)
 
.. note:: L'exemple présenté ci-dessous est disponible en totalité dans les échantillons de test: /Samples/Web_API/001_httpbin_rest.tpx.

Contrôles SSH
-------------

L'exemple suivant montre comment réaliser des tests d'une API REST.
Pour ce faire les tests réutisables sont utilisés.

Navigateurs Internet
--------------------

L'exemple suivant montre comment utiliser l'assistant pour écrire un test d'une application web

La solution préconise d'écrire les tests web
 - en identifiant le nombre de page affichée (et la réutilisation possible de ces pages)
 - en identifiant les différents enchainements de pages pour créer les scénarios
 - en définissant les parcours utilisateurs 

L'automatiquement des pages web se réalise à travers l'assistant et en générant des test units.
Les enchainements de pages sont à décrire dans les tests plans
Le parcours utilisateur est à définir dans un test global

.. image:: /_static/images/examples/web.png

La solution préconise aussi de n'utiliser que des xpath pour identifier des élements HTML.

.. image:: /_static/images/examples/web_xpath.png

.. note:: L'exemple présenté ci-dessous est disponible en totalité dans les échantillons de test: /Samples/Tests_Gui/Selenium/.

Mobile Android
--------------

L'exemple suivant montre comment utiliser l'assistant pour écrire un test d'une application mobile
