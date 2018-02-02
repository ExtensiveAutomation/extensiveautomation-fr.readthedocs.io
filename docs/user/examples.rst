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

Il est donc possible d'ajouter autant d'argument que nécessaire au niveau de la fonction ``execute()``
et de les ajouter à l'identiquer au niveau des 4 sections.

.. note:: Il est possible d'ajouter un préfixe au niveau du cas du test en utilisant l'argument ``prefix``.

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

Pour écrire un test d'api REST, il est conseillé:
 - d'utiliser le test réutilisable ``/Snippets/Protocols/04_Send_JSON``
 - de décrire le serveur cible en JSON (ip/port destination, support du http)


Exemple:
 
Le test appelle le service ``httpbin.org`` en https et appelle le service ``ip`` qui permet d'obtenir l'ip réel du client en json.

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
 réutilisable ``Snippets/Do/02_Terminate`` (Id=16)

 3. On envoit une requête REST et on décrit la réponse attendue en utilisant le test réutilisable ``/Snippets/Protocols/04_Send_JSON`` (Id=30). 
 Si cette étape ne fonctionne pas alors on annule le test (Id=31)
 
 La réponse reçue est vérifiée par le framework et ce qui a été décrit par le testeur dans le paramètre ``HTTP_RSP_BODY``
 
 .. code-block:: json
 
   origin		[!CAPTURE:EXTERNAL_IP:]
   
 La configuration indique qu'il faut vérifier dans la réponse que la clé `origin` est présente et 
 d'enregistrer la valeur dans le cache avec la clé ``EXTERNAL_IP``
 
 4. On affiche la valeur reçue dans la réponse avec le test réutilisable ``Snippets/Cache/02_Log_Cache`` (Id=32)
 
.. note:: L'exemple présenté ci-dessous est disponible en totalité dans les échantillons de test: ``/Samples/Web_API/001_httpbin_rest.tpx``.

Contrôles SSH
-------------

Pour écrire un test SSH, il est conseillé:
 - d'utiliser le test réutilisable ``/Snippets/Protocols/01_Send_SSH``
 - de décrire le serveur cible en JSON (ip, compte, mot de passe à minima)

.. image:: /_static/images/examples/ssh.png

Le test se décompose en plusieurs étapes:
 1. Chargement de la description (ip, compte, mot de passe) de la machine cible dans le cache
 2. Appel au test générique ``/Snippets/Protocols/01_Send_SSH`` pour récupérer la version du serveur
    La version (si trouvé à l'écran) est sauvegardée dans le cache avec la clé `SERVER_VERSION`
    Si la version n'est pas trouvée, le test part en erreur.
    
   .. code-block:: bash
  
     # checking server version
     xtctl version
     .*Server version: [!CAPTURE:SERVER_VERSION:]\n.*
     
   
 3. Affiche de la version depuis le cache.

.. note:: L'exemple complet est disponible dans les échantillons de tests ``/Self Testing/SYSTEM/000_System.tpx``.

Navigateurs Internet
--------------------

Pour écrire un test d'une application web, il faut:
 - obligatoirement déployer un agent ``selenium`` sur un poste disposant d'un navigateur firefox, chrome, internet explorer ou edge
 - avoir accès au code source de la page web depuis son navigateur
 - avoir des connaissances en xpath
 - connaitre les bases du code HTML

L'approche préconisée pour écrire les tests web est la suivante:
 - identifier le nombre de page affichée à scripter (et la réutilisation possible de ces pages)
 - identifier les différents enchainements de pages pour créer les scénarios
 - identifier les parcours utilisateurs 

Pour exécuter ce type de test, il faut absolument déclarer l'agent qui sera utilisé

.. image:: /_static/images/examples/selenium_agent.png

L'écriture des tests se réalise à travers l'assistant, il permet de décrire les différentes étapes
et de générer le test unit équivalent. Les enchainements de pages sont à décrire dans les tests plans
Le parcours utilisateur est à définir dans un test global

La solution préconise aussi de n'utiliser que des xpath pour identifier des élements HTML.

.. image:: /_static/images/examples/web_xpath.png

L'exemple ci-dessous montre comment créer un compte Google en utilisant un nom et prénom aléatoire.

.. image:: /_static/images/examples/web.png

Exemple de résultat:

.. image:: /_static/images/examples/selenium_random_data.png

.. tip:: 
  
  Il est possible d'utiliser les outils de développement des navigateurs pour valider les xpaths.
  
  .. image:: /_static/images/examples/firefox_console_xpath.png
  
.. note:: L'exemple présenté ci-dessous est disponible en totalité dans les échantillons de test ``/Samples/Tests_Gui/Selenium/``.

.. note::
  
  Selenium3  nécessite au minimum Java 8 sur le poste client.
  
  +--------------+---------------------+-----------+
  | Navigateurs  |   Version Selenium  |   Gecko   |
  +--------------+---------------------+-----------+
  | Firefox <47  |   Selenium  2       |   Non     |
  +--------------+---------------------+-----------+
  | Firefox > 47 |   Selenium  3       |   Oui     |
  +--------------+---------------------+-----------+
  | IE           |   Selenium  3       |   N/A     |
  +--------------+---------------------+-----------+
  | Chrome       |   Selenium  3       |   N/A     |
  +--------------+---------------------+-----------+


Mobile Android
--------------

Pour écrire le test d'une application mobile, il faut:
 - Avoir un téléphone mobile Android connecté en USB sur un PC
 - Déployer un agent ``adb`` sur un poste avec un mobile android connecté dessus.
 - Avoir accès à la description xml des applications depuis l'agent

L'écriture des tests se réalise avec l'assistant, il permet de décrire les différentes étapes
et de générer le test unit équivalent.

.. important:: L'activation du mode ``debogage USB`` est obligatoire sur le téléphone et accepter la connection de l'agent.