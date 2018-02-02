Tests réutilisables
===================

L'intérêt des tests réutilisables 
 - factoriser la base de tests
 - réutiliser les tests
 - limiter l'écriture de scripts pour concevoir les scénarios

Ces types de tests sont à utiliser en mode test ``plan``. 

Données partagées
-----------------

Mise en cache d'une valeur
~~~~~~~~~~~~~~~~~~~~~~~~~~
   
.. important:: Chemin d'accès du test réutilisable ``/Snippets/Cache/01_Set_Cache.tux``

Ce test réutilisable consiste à sauvegarder une valeur dans le cache de données disponible durant l'exécution d'un test.

Paramètre(s) à configurer:

+-----------------+-----------------------------------------------------------+
|Paramètres       |   Description                                             |
+-----------------+-----------------------------------------------------------+
| DATAS           |   Contient la liste des valeurs à sauvegarder             |
+-----------------+-----------------------------------------------------------+

Le paramètre ``DATAS`` contient la liste des valeurs à sauvegarder avec le format:

.. code-block:: bash
  
  # mon commentaire
  [!TO:CACHE:<MA_CLE>:];ma valeur
  

Exemple

.. code-block:: bash
  
  # Save misc data
  [!TO:CACHE:EXAMPLE:];hello world

  # Save server information in the cache
  [!TO:CACHE:SERVER_DESCRIPTION:];[!FROM:INPUT:TEST_PURPOSE:]
  
  
.. note:: Il est possible de sauvegarder plusieurs valeurs avec ce test.


Affichage d'une valeur
~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Cache/02_Log_Cache.tux``

Ce test réutilisable permet d'afficher la valeur d'une clé présente dans le cache durant l'exécution du test.

Paramètre(s) à configurer:

+-----------------+-----------------------------------------------------------------------+
|Paramètres       |   Description                                                         |
+-----------------+-----------------------------------------------------------------------+
| MESSAGES        |   Contient la liste des paramètres à logguer dans le test             |
+-----------------+-----------------------------------------------------------------------+
 
.. code-block:: bash
  
  # display cache 
  [!FROM:CACHE:EXAMPLE:]
  
  # log timeout input
  [!FROM:INPUT:TIMEOUT:]
  

.. note:: Il est possible d'afficher plusieurs valeurs en une seule fois

Reset du cache
~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Cache/02_Reset_Cache.tux``

Ce test réutilisable permet de vider totalement le cache.
Aucun paramètre à configurer.

.. note:: Ce test peut être utilise lorsque plusieurs scénarios sont enchainés dans un test global.

Vérification d'une valeur dans le cache
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Cache/02_Checking_Cache.tux``

Ce test réutilisable permet de vérifier la valeur dans une clé présente dans le cache.

Paramètre(s) à configurer:

+-----------------+------------------------------------------------+
|Paramètres       |   Description                                  |
+-----------------+------------------------------------------------+
| CHECKING        |  Liste des valeurs à vérifier dans le cache    |
+-----------------+------------------------------------------------+

Les opérateurs disponibles:

+-----------------+-----------------------------------------------------------------------+
|Paramètres       |   Description                                                         |
+-----------------+-----------------------------------------------------------------------+
| contains        | Permet de vérifier si la valeur contient une chaîne de caractère      |
+-----------------+-----------------------------------------------------------------------+
| matches         | Permet de vérifier si la valeur correspond à l'expression régulière   |
+-----------------+-----------------------------------------------------------------------+
| ==              | Permet de vérifier si la valeur est égal à                            |
+-----------------+-----------------------------------------------------------------------+
| !=              | Permet de vérifier si la valeur est différent de                      |
+-----------------+-----------------------------------------------------------------------+
| >               | Permet de vérifier si la valeur est supérieur à                       |
+-----------------+-----------------------------------------------------------------------+
| <               | Permet de vérifier si la valeur est inférieur à                       |
+-----------------+-----------------------------------------------------------------------+
| >=              | Permet de vérifier si la valeur est supérieur égal à                  |
+-----------------+-----------------------------------------------------------------------+
| <=              | Permet de vérifier si la valeur est inférieur égal à                  |
+-----------------+-----------------------------------------------------------------------+

.. code-block:: bash
  
  # Vérifie si valeur contient la chaine de caractère etst
  [!FROM:CACHE:EXAMPLE:] contains test
  

.. note:: Il est possible de vérifier plusieurs valeurs en une seule fois

Suppression d'une entrée dans le cache
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Cache/02_Delete_Cache.tux``

Ce test réutilisable permet de supprimer une clé et sa valeur associée dans le cache.

Paramètre(s) à configurer:

+-----------------+------------------------------------------+
|Paramètres       |   Description                            |
+-----------------+------------------------------------------+
| MESSAGES        |  Liste des clés à supprimer              |
+-----------------+------------------------------------------+
 
.. code-block:: bash
  
  # supprime la clé EXEMPLE du cache
  [!FROM:CACHE:EXEMPLE:]
   

.. note:: Il est possible de supprimer plusieurs clés en une seule fois

Actions basiques
----------------

Mise en attente
~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Do/01_Wait.tux``

Ce test réutilisable permet d'attendre xx secondes durant l'exécution du test.

Paramètre(s) à configurer:

+-----------------+-------------------+
|Paramètres       |   Description     |
+-----------------+-------------------+
| DURATION        | durée en secondes |
+-----------------+-------------------+

Arrêt d'un test
~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Do/02_Terminate.tux``

Ce test réutilisable permet de forcer l'arrêt d'un scénario en cas d'erreur.
Un message expliquant l'arrêt peut être spécifié avec le paramètre ``STOP_TEST_MSG``.

.. note:: Il est possible de personaliser le message d'arrêt en configurant la variable ``STOP_TEST_MSG``.

Chargement d'un environnement de test
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Do/03_Initilize.tux``

Ce test réutilisable permet de charger dans le cache les données de son environnement de tests 
(les adresses ip, compte d'accès des serveurs, etc.).

Un environnement se décrit avec 4 niveaux:
 - ``environnement``
 - ``clusteur``
 - ``noeud``
 - ``instance``
 
Un ``environnement`` peut être constitué de un ou plusieurs clusteurs.

.. code-block:: json
  
  {
    "PLATFORM": {
                   "NOM_CLUSTER_1": [ .. ],
                   "NOM_CLUSTER_2": [ .. ]
        }
  }
  

Un ``clusteur`` est constitué d'une liste de noeuds.

.. code-block:: json
  
  {
    "NOM_CLUSTER_1": [
                  { "NOM_NOEUD_1": { .. },
                  { "NOM_NOEUD_2": { .. }
        ]
  }
  

Un ``noeud`` est constitué de une ou plusieurs instances.

.. code-block:: json
  
  {
    "NOM_NOEUD_1": {
                  "COMMON": { ... },
                  "INSTANCES": {....}
        }
  }
  

Une ``instance`` se constitue de plusieurs clés/valeurs.


.. code-block:: json
  
  {
    "INSTANCES": {
                  "TYPE_INSTANCE_1": {
                                        "NOM_INSTANCE_1": { ...},
                                        "NOM_INSTANCE_2": { ...}
                                    },
                  "TYPE_INSTANCE_2": { ... }
        }
  }
  

Paramètre(s) à configurer:

+-----------------+-----------------------------------------------------------------------------------------+
|Paramètres       |   Description                                                                           |
+-----------------+-----------------------------------------------------------------------------------------+
| ENVIRONMENT     |  Lien vers une variable partagée ou bien contient directement du ``JSON``.              |
+-----------------+-----------------------------------------------------------------------------------------+
       
Exemple d'un environnement de test contenant un serveur http avec une instance de type rest.
Après chargement dans le cache, l'instance REST est accessible en utilisant la clé ``NODE_HTTP_REST``.
L'ensemble des clés présentes dans ``COMMON`` sont automatiquement copiés dans chaques instances.

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
 
La clé ``DATASET`` peut contenir des jeux de données.

Générateurs
-----------

Hash SHA
~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Generators/01_Gen_Sha.tux``

Ce test réutilisable permet de générer un hash d'une valeur et de la stocker dans le cache.

Paramètre(s) à configurer:

+-----------------+----------------------------------------------------------+
|Paramètres       |   Description                                            |
+-----------------+----------------------------------------------------------+
| DATA_IN         | Chaine de caractère à hasher                             |
+-----------------+----------------------------------------------------------+
| CACHE_KEY       | Nom de la clé                                            |
+-----------------+----------------------------------------------------------+
| SHA             | Type de hash réaliser (sha1, sha256, sha512)             |
+-----------------+----------------------------------------------------------+

Hash MD5
~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Generators/01_Gen_Md5.tux``

Ce test réutilisable permet de générer un hash md5 d'une valeur et de la stocker dans le cache.

Paramètre(s) à configurer:

+-----------------+--------------------------------------------------------------+
|Paramètres       |   Description                                                |
+-----------------+--------------------------------------------------------------+
| DATA_IN         | Chaine de caractère à hasher                                 |
+-----------------+--------------------------------------------------------------+
| CACHE_KEY       | Nom de la clé ou le résultat sera sauvegarder dans le cache  |
+-----------------+--------------------------------------------------------------+


UUID
~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Generators/01_Gen_Uuid.tux``

Ce test réutilisable permet de générer un id uuid et de la stocker dans le cache.

Paramètre(s) à configurer:

+-----------------+-----------------------------------------------------------+
|Paramètres       |   Description                                             |
+-----------------+-----------------------------------------------------------+
| CACHE_KEY       | Nom de la clé pour sauvegarder le résultat dans le cache  |
+-----------------+-----------------------------------------------------------+

 
BASE64
~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Generators/01_Gen_Base64.tux``

Ce test réutilisable permet d'encoder ou décoder une chaine de caractère et de stocker le résultat dans le cache.

Paramètre(s) à configurer:

+-----------------+------------------------------------------------------------------------------------+
|Paramètres       |   Description                                                                      |
+-----------------+------------------------------------------------------------------------------------+
| CACHE_KEY       | Nom de la clé pour sauvegarder le résultat dans le cache                           |
+-----------------+------------------------------------------------------------------------------------+
| DECODE          | A positionner à True pour encoder                                                  |
+-----------------+------------------------------------------------------------------------------------+
| ENCODE          | A positionner à True pour décoder                                                  |
+-----------------+------------------------------------------------------------------------------------+
| URLSAFE         | A positionner à True si le résulat après encodage doit être utilisé dans une url   |
+-----------------+------------------------------------------------------------------------------------+
| STR_BASE64      | Chaine de caractère à encoder/décoder                                              |
+-----------------+------------------------------------------------------------------------------------+


GZIP
~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Generators/01_Gen_Gzip.tux``

Ce test réutilisable permet de compresser ou décompresser une chaine de caractère et de stocker le résultat dans le cache.

Paramètre(s) à configurer:

+-----------------+-------------------------------------------------------------+
|Paramètres       |   Description                                               |
+-----------------+-------------------------------------------------------------+
| CACHE_KEY       | Nom de la clé                                               |
+-----------------+-------------------------------------------------------------+
| COMPRESS        | A positionner à True pour compresser                        |
+-----------------+-------------------------------------------------------------+
| UNCOMPRESS      | A positionner à True pour décompresser                      |
+-----------------+-------------------------------------------------------------+
| STR_GZIP        | Chaine de caractère à compresser/décompresser               |
+-----------------+-------------------------------------------------------------+

Protocoles réseaux
------------------

SSH
~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Protocols/01_Send_SSH.tsx``

Ce test réutilisable permet d'envoyer un enchainement de commandes ssh.
Il est à utiliser conjointement avec le test réutilisable ``/Snippets/Do/03_Initilize.tux`` permet de charger un environnement dans le cache.

Paramètre(s) à configurer:

+-----------------+----------------------------------------------------------+
|Paramètres       |   Description                                            |
+-----------------+----------------------------------------------------------+
| SERVERS         |  Liste des serveurs à contacter                          |
+-----------------+----------------------------------------------------------+
| COMMANDS        |  Listes des commandes à exécuter sur la machine distante |
+-----------------+----------------------------------------------------------+

Le paramètre `COMMANDS` attends un ou plusieurs blocs de 4 lignes.
Chaque bloc doit respecter le formalisme suivant:
 1. Commentaire expliquant l'action, cette information est utilisé pour initialiser l'étape de test
 2. La commande a exécuter
 3. La chaine de caractère attendue à l'écran, si la valeur attendue n'est pas trouvée alors l'étape par en erreur. (ligne optionnel)
 4. vide
 
.. warning:: Chaque bloc sera exécuté même si le précèdent est en erreur. 
    
L'exemple suivant effectue les actions suivantes:
 1. envoie de 3 ping sur la machine distante dont l'ip est stockée dans le cache ``DEST_HOST``
 2. Vérification d'avoir le message à l'écran indiquant que les 3 paquets ont été envoyés.
 Ensuite la valeur mddev est stockée dans le cache avec la clé ``STATS` 
 3. Le deuxième bloc efface l'écran en envoyant la commande clear.
 4. Enfin te test attend de trouver le prompt à l'écran
 
.. code-block:: bash
  
  # send a ping 
  ping -c 3 [!CACHE:SVR:DEST_HOST:]
  .*3 packets transmitted, 3 received, 0% packet loss.*mdev = [!CAPTURE:STATS:] ms.*
  
  # clear the screen
  clear
  .*root@.*
  

.. note:: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.

.. note:: 
  Par défaut, le test attend 20 secondes au maximum pour trouver la chaine de caractère attendue.
  Il est possible de configurer cette valeur avec le paramètre ``TIMEOUT``.
  
.. note:: 
  Par défaut, le test attend 10 secondes pour effectuer la connexion au serveur distant.
  Il est possible de configurer cette valeur avec le paramètre ``TIMEOUT_CONNECT``.

HTTP
~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Protocols/01_Send_HTTP.tsx``

Ce test réutilisable permet d'envoyer une requête HTTP en vérifiant la réponse reçue.
Il est à utiliser conjointement avec le test réutilisable ``/Snippets/Do/03_Initilize.tux`` permet de charger un environnement dans le cache.

Paramètre(s) à configurer pour définir la destination:

+-----------------+---------------------------------+
|Paramètres       |   Description                   |
+-----------------+---------------------------------+
| SERVERS         |  Liste des serveurs à contacter |
+-----------------+---------------------------------+

Paramètre(s) pour configurer la requête HTTP à envoyer:

+-----------------+---------------------------------+
|Paramètres       |   Description                   |
+-----------------+---------------------------------+
| HTTP_REQ_BODY   | Corps de la requête             |
+-----------------+---------------------------------+
| HTTP_REQ_HEADERS| Liste des headers à ajouter     |
+-----------------+---------------------------------+
| HTTP_REQ_METHOD | Methode HTTP (GET, POST, etc..) |
+-----------------+---------------------------------+
| HTTP_REQ_URI    | URI appeler                     |
+-----------------+---------------------------------+

.. image:: /_static/images/examples/snippets_http_req.png

Paramètre(s) pour configurer la réponse HTTP attendue (et qui permettra de considérer le test comme valide):

+-------------------+----------------------------------------------------+
|Paramètres         |   Description                                      |
+-------------------+----------------------------------------------------+
| HTTP_RSP_BODY     | Corps de la réponse attendue.                      |
+-------------------+----------------------------------------------------+
| HTTP_RSP_CODE     | Le code HTTP attendue. 200 par défaut              |
+-------------------+----------------------------------------------------+
| HTTP_RSP_HEADERS  | Liste des entêtes attendues                        |
+-------------------+----------------------------------------------------+
| HTTP_RSP_PHRASE   | La phrase HTTP attendue. OK par défaut             |
+-------------------+----------------------------------------------------+
| HTTP_RSP_VERSION  | La version HTTP attendue. HTTP/1.[0|1] par défaut  |
+-------------------+----------------------------------------------------+

.. image:: /_static/images/examples/snippets_http_rsp.png

.. note:: 
  L'utilisation des expressions régulières est possible pour vérifier ou enregistrer une valeur dans le corps de la réponse ou bien dans les entêtes.
  
  .. image:: /_static/images/examples/snippets_http_capture.png

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.

XML
~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Protocols/01_Send_XML.tsx``

Ce test réutilisable permet d'envoyer une requête HTTP avec du ``XML`` en vérifiant la réponse reçue.
Il est à utiliser conjointement avec le test réutilisable ``/Snippets/Do/03_Initilize.tux`` permet de charger un environnement dans le cache.

Paramètre(s) à configurer pour définir la destination:

+-----------------+---------------------------------+
|Paramètres       |   Description                   |
+-----------------+---------------------------------+
| SERVERS         |  Liste des serveurs à contacter |
+-----------------+---------------------------------+

Paramètre(s) pour configurer la requête HTTP à envoyer:

+-----------------+---------------------------------+
|Paramètres       |   Description                   |
+-----------------+---------------------------------+
| HTTP_REQ_BODY   | Corps de la requête             |
+-----------------+---------------------------------+
| HTTP_REQ_HEADERS| Liste des headers à ajouter     |
+-----------------+---------------------------------+
| HTTP_REQ_METHOD | Methode HTTP (GET, POST, etc..) |
+-----------------+---------------------------------+
| HTTP_REQ_URI    | URI appeler                     |
+-----------------+---------------------------------+

Paramètre(s) pour configurer la réponse HTTP attendue (et qui permettra de considérer le test comme valide):

+--------------------+----------------------------------------------------+
|Paramètres          |   Description                                      |
+--------------------+----------------------------------------------------+
| HTTP_RSP_BODY      | Liste des xpaths à vérifier.                       |
+--------------------+----------------------------------------------------+
| HTTP_RSP_CODE      | Le code HTTP attendue. 200 par défaut              |
+--------------------+----------------------------------------------------+
| HTTP_RSP_HEADERS   | Liste des entêtes attendues                        |
+--------------------+----------------------------------------------------+
| HTTP_RSP_NAMESPACES| Liste des namespaces à prendre en compte           |
+--------------------+----------------------------------------------------+
| HTTP_RSP_PHRASE    | La phrase HTTP attendue. OK par défaut             |
+--------------------+----------------------------------------------------+
| HTTP_RSP_VERSION   | La version HTTP attendue. HTTP/1.[0|1] par défaut  |
+--------------------+----------------------------------------------------+

.. warning:: Le test sera en erreur si la réponse ne contient pas de XML.

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.


JSON
~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Protocols/01_Send_JSON.tsx``

Ce test réutilisable permet d'envoyer une requête HTTP avec du JSON en vérifiant la réponse reçue.
Il est à utiliser conjointement avec le test réutilisable ``/Snippets/Do/03_Initilize.tux`` permet de charger un environnement dans le cache.

Paramètre(s) à configurer pour définir la destination:

+-----------------+---------------------------------+
|Paramètres       |   Description                   |
+-----------------+---------------------------------+
| SERVERS         |  Liste des serveurs à contacter |
+-----------------+---------------------------------+

Paramètre(s) pour configurer la requête HTTP à envoyer:

+-----------------+---------------------------------+
|Paramètres       |   Description                   |
+-----------------+---------------------------------+
| HTTP_REQ_BODY   | Corps de la requête             |
+-----------------+---------------------------------+
| HTTP_REQ_HEADERS| Liste des headers à ajouter     |
+-----------------+---------------------------------+
| HTTP_REQ_METHOD | Methode HTTP (GET, POST, etc..) |
+-----------------+---------------------------------+
| HTTP_REQ_URI    | URI appeler                     |
+-----------------+---------------------------------+


Paramètre(s) pour configurer la réponse HTTP attendue (et qui permettra de considérer le test comme valide):

+-------------------+----------------------------------------------------+
|Paramètres         |   Description                                      |
+-------------------+----------------------------------------------------+
| HTTP_RSP_BODY     | Liste des json xpaths à vérifier.                  |
+-------------------+----------------------------------------------------+
| HTTP_RSP_CODE     | Le code HTTP attendue. 200 par défaut              |
+-------------------+----------------------------------------------------+
| HTTP_RSP_HEADERS  | Liste des entêtes attendues                        |
+-------------------+----------------------------------------------------+
| HTTP_RSP_PHRASE   | La phrase HTTP attendue. OK par défaut             |
+-------------------+----------------------------------------------------+
| HTTP_RSP_VERSION  | La version HTTP attendue. HTTP/1.[0|1] par défaut  |
+-------------------+----------------------------------------------------+

.. warning:: Le test sera en erreur si la réponse ne contient pas de JSON.

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.

Interface utilisateur
---------------------

Ouverture application Windows
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/UI/01_Win_OpenApp.tux``

Tests réutilisables permettant d'ouvrir ou de fermer une application sur un poste Windows ou Linux.
Ce test nécessite de définir quel agent sera utilisé avec la clé ``AGENT_GUI``.

Paramètre(s) à configurer:

+-----------------+--------------------------------------------------------+
|Paramètres       |   Description                                          |
+-----------------+--------------------------------------------------------+
| APP_PATH        |  Chemin d'accès de l'application à ouvrir              |
+-----------------+--------------------------------------------------------+

.. warning: un agent de type `sikulix-server` est obligatoire.

Fermeture application Windows
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/UI/02_Win_CloseApp.tux``

Tests réutilisables permettant d'ouvrir ou de fermer une application sur un poste Windows ou Linux.
Ce test nécessite de définir quel agent sera utilisé avec la clé ``AGENT_GUI``.

Paramètre(s) à configurer:

+-----------------+---------------------------------------------+
|Paramètres       |   Description                               |
+-----------------+---------------------------------------------+
| APP_NAME        |  Nom de l'application à fermer              |
+-----------------+---------------------------------------------+

.. warning: un agent de type ``sikulix-server`` est obligatoire.


Ouverture navigateur
~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/UI/03_OpenBrowser.tux``

Tests réutilisables permettant d'ouvrir ou de fermer une navigateur sur un poste Windows ou Linux.
Ce test nécessite de définir quel agent sera utilisé avec la clé ``AGENT_GUI_BROWSER``.

Paramètre(s) à configurer:

+-----------------+--------------------------------------+
|Paramètres       |   Description                        |
+-----------------+--------------------------------------+
| LOADING_URL     |  Url du site à charger               |
+-----------------+--------------------------------------+

Il est possible de sélectionner le navigateur à ouvrir, les navigateurs suivants sont supportés:
 - Firefox
 - Chrome
 - Internet Explorer
 - Opera
 - Edge

.. image:: /_static/images/examples/selenium_browser.png
 
.. note:: L'url doit obligatoirement commencer par ``http://`` ou ``https://``

.. warning: un agent de type ``selenium(2|3)-server`` est obligatoire.


Fermeture navigateur
~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/UI/03_CloseBrowser.tux``

Tests réutilisables permettant d'ouvrir ou de fermer une navigateur sur un poste Windows ou Linux.
Ce test nécessite de définir quel agent sera utilisé avec la clé ``AGENT_GUI_BROWSER``.

.. warning: un agent de type ``selenium-server`` est obligatoire.


Vérifications
-------------

Contenu de type XML
~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Verify/01_Check_XML.tux``

Ce test réutilisable permet de vérifier du contenu de type XML avec l'outil xpath.

Paramètre(s) à configurer:

+-----------------+------------------------------------+
|Paramètres       |   Description                      |
+-----------------+------------------------------------+
| XML_STR         | XML brut à inspecter               |
+-----------------+------------------------------------+
| XML_XPATH       | xpath qui sera vérifier le test    |
+-----------------+------------------------------------+
| XML_NAMESPACES  | Définitions des namespaces         |
+-----------------+------------------------------------+

Exemple de valeur pour le paramètre ``XML_STR``:

.. code-block:: xml
  
  <NewDataSet>
  <Table>
    <Country>France</Country>
    <City>Le Touquet</City>
  </Table>
  <Table>
    <Country>France</Country>
    <City>Agen</City>
  </Table>
  <Table>
    <Country>France</Country>
    <City>Cazaux</City>
  </Table>
  <Table>
    <Country>France</Country>
    <City>Bordeaux / Merignac</City>
  </Table>
  <Table>
    <Country>France</Country>
    <City>Bergerac</City>
  </Table>
  </NewDataSet>
  
Exemple de valeur pour le paramètre ``XML_XPATH`` permettant d'enregistrer dans le cache 
le nom de la ville à la 2ième position dans la liste.

.. code-block:: json
  
  (//NewDataSet/Table)[1]/City	[!CAPTURE:CITY:]
  
La valeur sera accessible dans le cache avec la clé ``CITY``.

Contenu de type JSON
~~~~~~~~~~~~~~~~~~~~

.. important:: Chemin d'accès du test réutilisable ``/Snippets/Verify/01_Check_JSON.tux``

Ce test réutilisable permet de vérifier du contenu de type JSON avec l'outil jsonpath

Paramètre(s) à configurer:

+-----------------+---------------------------------------+
|Paramètres       |   Description                         |
+-----------------+---------------------------------------+
| JSON_STR        | Json à inspecter                      |
+-----------------+---------------------------------------+
| JSON_XPATH      | jsonpath qui sera vérifié par le test |
+-----------------+---------------------------------------+

Exemple de valeur pour le paramètre ``JSON_STR``:

.. code-block:: json
  
  {
   "args": {}, 
   "headers": {
   "Connection": "close", 
   "Host": "httpbin.org", 
   "User-Agent": "ExtensiveTesting"
  }, 
   "origin": "190.117.217.129", 
   "url": "https://httpbin.org/get"
  }
  
Exemple de valeur pour le paramètre ``JSON_XPATH`` permettant d'enregistrer dans le cache 
la valeur de la clé `Connection` dans le dictionnaire `headers`. 

.. code-block:: json
  
  headers.Connection	[!CAPTURE:CX:]
  
La valeur sera accessible dans le cache avec la clé ``CX``.
