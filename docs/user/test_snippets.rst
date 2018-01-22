Tests réutilisables
===================

L'intérêt des tests réutilisables 
 - factoriser la base de tests
 - réutiliser les tests
 - limiter l'écriture de scripts pour concevoir les scénarios

Ces types de tests sont à utiliser en mode test "plan". 

Données partagées
-----------------

Mise en cache d'une valeur
~~~~~~~~~~~~~~~~~~~~~~~~~~
   
.. important:: Chemin d'accès du test réutilisable /Snippets/Cache/01_Set_Cache.tux

Ce test réutilisable consiste à sauvegarder une valeur dans le cache de données disponible durant l'exécution d'un test.

Paramètre(s) à configurer:

+-----------------+-----------------------------------------------------------+
|Paramètres       |   Description                                             |
+-----------------+-----------------------------------------------------------+
| DATAS           |   Contient la liste des valeurs à sauvegarder             |
+-----------------+-----------------------------------------------------------+

Le paramètre `DATAS` contient la liste des valeurs à sauvegarder avec le format:

.. code-block::

   # mon commentaire
   [!TO:CACHE:<MA_CLE>:];ma valeur
    

Exemple

.. code-block::

    # Save misc data
    [!TO:CACHE:EXAMPLE:];hello world

    # Save server information in the cache
    [!TO:CACHE:SERVER_DESCRIPTION:];[!FROM:INPUT:TEST_PURPOSE:]
    
.. note:: Il est possible de sauvegarder plusieurs valeurs avec ce test.


Affichage d'une valeur
~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Cache/02_Log_Cache.tux

Ce test réutilisable permet d'afficher la valeur d'une clé présente dans le cache durant l'exécution du test.

Paramètre(s) à configurer:

+-----------------+-----------------------------------------------------------------------+
|Paramètres       |   Description                                                         |
+-----------------+-----------------------------------------------------------------------+
| MESSAGES        |   Contient la liste des paramètres à logguer dans le test             |
+-----------------+-----------------------------------------------------------------------+
 
.. code-block::

    # display cache 
    [!FROM:CACHE:EXAMPLE:]

    # log timeout input
    [!FROM:INPUT:TIMEOUT:]
    

.. note:: Il est possible d'afficher plusieurs valeurs en une seule fois

Reset du cache
~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Cache/02_Reset_Cache.tux

Ce test réutilisable permet de vider totalement le cache.
Aucun paramètre à configurer.

.. note:: Ce test peut être utilise lorsque plusieurs scénarios sont enchainés dans un test global.

Vérification d'une valeur dans le cache
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Cache/02_Checking_Cache.tux

Ce test réutilisable permet de vérifier la valeur dans une clé présente dans le cache.

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| CHECKING        |                |
+-----------------+----------------+

Les opérateurs disponibles:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| contains        |                |
+-----------------+----------------+
| matches         |                |
+-----------------+----------------+
| ==              |                |
+-----------------+----------------+
| !=              |                |
+-----------------+----------------+
| >               |                |
+-----------------+----------------+
| <               |                |
+-----------------+----------------+
| >=              |                |
+-----------------+----------------+
| <=              |                |
+-----------------+----------------+

<image à insérer>

.. note:: Il est possible de vérifier plusieurs valeurs en une seule fois

Suppression d'une entrée dans le cache
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Cache/02_Delete_Cache.tux

Ce test réutilisable permet de supprimer une clé et sa valeur associée dans le cache.

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| MESSAGES        |                |
+-----------------+----------------+
 
<image à insérer>

.. note:: Il est possible de supprimer plusieurs clés en une seule fois

Actions basiques
----------------

Mise en attente
~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Do/01_Wait.tux

Ce test réutilisable permet d'attendre xx secondes durant l'exécution du test.

Paramètre(s) à configurer:

+-----------------+-------------------+
|Paramètres       |   Description     |
+-----------------+-------------------+
| DURATION        | durée en secondes |
+-----------------+-------------------+

Arrêt d'un test
~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Do/02_Terminate.tux

Ce test réutilisable permet de forcer l'arrêt d'un scénario en cas d'erreur.
Un message expliquant l'arrêt peut être spécifié avec le paramètre STOP_TEST_MSG

.. note:: Il est possible de personaliser le message d'arrêt en configurant la variable `STOP_TEST_MSG`.

Chargement de l'environnement de test
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Do/03_Initilize.tux

Ce test réutilisable permet de charger dans le cache les données de son environnement de tests.
Par contre les adresses, compte d'accès des serveurs, etc.

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| ENVIRONMENT     |                |
+-----------------+----------------+

L'environnement doit être spécifié en sélectionnant d'une variable réutilisable.

.. note:: 
 L'environnement peut être directement précisé au format JSON.
 Un exemple: 
 
 .. code-block:: python
 
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

Générateurs
-----------

Hash SHA
~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Generators/01_Gen_Sha.tux

Ce test réutilisable permet de générer un hash d'une valeur et de la stocker dans le cache.

Paramètre(s) à configurer:

+-----------------+------------------------------------+
|Paramètres       |   Description                      |
+-----------------+------------------------------------+
| DATA_IN         |                                    |
+-----------------+------------------------------------+
| CACHE_KEY       | Nom de la clé                      |
+-----------------+------------------------------------+
| SHA             | Type de hash réaliser              |
+-----------------+------------------------------------+

Hash MD5
~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Generators/01_Gen_Md5.tux

Ce test réutilisable permet de générer un hash md5 d'une valeur et de la stocker dans le cache.

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| DATA_IN         |                |
+-----------------+----------------+
| CACHE_KEY       | Nom de la clé  |
+-----------------+----------------+


UUID
~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Generators/01_Gen_Uuid.tux

Ce test réutilisable permet de générer un id uuid et de la stocker dans le cache.

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| CACHE_KEY       | Nom de la clé  |
+-----------------+----------------+

 
BASE64
~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Generators/01_Gen_Base64.tux

Ce test réutilisable permet d'encoder ou décoder une chaine de caractère et de stocker le résultat dans le cache.

Paramètre(s) à configurer:

+-----------------+-----------------------------------------------------+
|Paramètres       |   Description                                       |
+-----------------+-----------------------------------------------------+
| CACHE_KEY       | Nom de la clé                                       |
+-----------------+-----------------------------------------------------+
| DECODE          |                                                     |
+-----------------+-----------------------------------------------------+
| ENCODE          |                                                     |
+-----------------+-----------------------------------------------------+
| URLSAFE         |                                                     |
+-----------------+-----------------------------------------------------+
| STR_BASE64      | Chaine de caractère à encoder/décoder               |
+-----------------+-----------------------------------------------------+


GZIP
~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Generators/01_Gen_Gzip.tux

Ce test réutilisable permet de compresser ou décompresser une chaine de caractère et de stocker le résultat dans le cache.

Paramètre(s) à configurer:

+-----------------+-------------------------------------------------------------+
|Paramètres       |   Description                                               |
+-----------------+-------------------------------------------------------------+
| CACHE_KEY       | Nom de la clé                                               |
+-----------------+-------------------------------------------------------------+
| COMPRESS        |                                                             |
+-----------------+-------------------------------------------------------------+
| UNCOMPRESS      |                                                             |
+-----------------+-------------------------------------------------------------+
| STR_GZIP        | Chaine de caractère à compresser/décompresser               |
+-----------------+-------------------------------------------------------------+

Protocoles réseaux
------------------

SSH
~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Protocols/01_Send_SSH.tsx

Ce test réutilisable permet d'envoyer un enchainement de commandes ssh.

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| SERVERS         |                |
+-----------------+----------------+

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.

HTTP
~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Protocols/01_Send_HTTP.tsx

Ce test réutilisable permet d'envoyer une requête HTTP en vérifiant la réponse reçue.

Paramètre(s) à configurer:

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.

XML
~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Protocols/01_Send_XML.tsx

Ce test réutilisable permet d'envoyer une requête HTTP avec du XML en vérifiant la réponse reçue.

Paramètre(s) à configurer:

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.


JSON
~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Protocols/01_Send_JSON.tsx

Ce test réutilisable permet d'envoyer une requête HTTP avec du JSON en vérifiant la réponse reçue.

Paramètre(s) à configurer:

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.

Interface utilisateur
---------------------

Ouverture application Windows
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/UI/01_Win_OpenApp.tux

Tests réutilisables permettant d'ouvrir ou de fermer une application sur un poste Windows ou Linux.

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| APP_PATH        |                |
+-----------------+----------------+

.. warning: un agent de type `sikulix-server` est obligatoire.

Fermeture application Windows
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/UI/02_Win_CloseApp.tux

Tests réutilisables permettant d'ouvrir ou de fermer une application sur un poste Windows ou Linux.

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| APP_NAME        |                |
+-----------------+----------------+

.. warning: un agent de type `sikulix-server` est obligatoire.


Ouverture navigateur
~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/UI/03_OpenBrowser.tux

Tests réutilisables permettant d'ouvrir ou de fermer une navigateur sur un poste Windows ou Linux.

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| LOADING_URL     |                |
+-----------------+----------------+

.. warning: un agent de type `selenium-server` est obligatoire.


Fermeture navigateur
~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/UI/03_CloseBrowser.tux

Tests réutilisables permettant d'ouvrir ou de fermer une navigateur sur un poste Windows ou Linux.
Aucun paramètre à configurer.

.. warning: un agent de type `selenium-server` est obligatoire.


Vérifications
-------------

Contenu de type XML
~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Verify/01_Check_XML.tux

Ce test réutilisable permet de vérifier du contenu de type XML avec  l'outil xpath.

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| XML_STR         |                |
+-----------------+----------------+
| XML_XPATH       |                |
+-----------------+----------------+
| XML_NAMESPACES  |                |
+-----------------+----------------+

Contenu de type JSON
~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable /Snippets/Verify/01_Check_JSON.tux

Ce test réutilisable permet de vérifier du contenu de type JSON avec l'outil jsonpath

Paramètre(s) à configurer:

+-----------------+----------------+
|Paramètres       |   Description  |
+-----------------+----------------+
| JSON_STR        |                |
+-----------------+----------------+
| JSON_XPATH      |                |
+-----------------+----------------+