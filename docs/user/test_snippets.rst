Tests réutilisables
===================

Ces types de tests sont à utiliser en mode test "plan". 
L'intérêt premier est de pouvoir réutiliser des morceaux de tests dans le but de créer des scénarios.

Données partagées
-----------------

Mise en cache d'une valeur
~~~~~~~~~~~~~~~~~~~~~~~~~~

Ce test réutilisable consiste à sauvegarder une valeur dans le cache de données disponible durant l'exécution d'un test.

Les paramètres à configurer:
 - DATAS
 
<image à insérer>

.. note:: Il est possible de sauvegarder plusieurs valeurs avec ce test.


Affichage d'une valeur
~~~~~~~~~~~~~~~~~~~~~~

Ce test réutilisable permet d'afficher la valeur d'une clé présente dans le cache durant l'exécution du test.

Les paramètres à configurer:
 - MESSAGES
 
<image à insérer>

.. note:: Il est possible d'afficher plusieurs valeurs en une seule fois

Reset du cache
~~~~~~~~~~~~~~

Ce test réutilisable permet de vider totalement le cache.
Aucun paramètre à configurer.

.. note:: Ce test peut être utilise lorsque plusieurs scénarios sont enchainés dans un test global.

Vérification d'une valeur dans le cache
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ce test réutilisable permet de vérifier la valeur dans une clé présente dans le cache.
Les paramètres à configurer:
 - CHECKING

Les opérateurs disponibles:
 - contains
 - matches
 - ==
 - !=
 - >
 - <
 - >=
 - <=
 
<image à insérer>

.. note:: Il est possible de vérifier plusieurs valeurs en une seule fois

Suppression d'une entrée dans le cache
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ce test réutilisable permet de supprimer une clé et sa valeur associée dans le cache.
Les paramètres à configurer:
 - MESSAGES
 
<image à insérer>

.. note:: Il est possible de supprimer plusieurs clés en une seule fois

Actions basiques
----------------

Mise en attente
~~~~~~~~~~~~~~

Ce test réutilisable permet d'attendre xx secondes durant l'exécution du test.
Les paramètres à configurer:
 - DURATION

Arrêt d'un test
~~~~~~~~~~~~~~

Ce test réutilisable permet de forcer l'arrêt d'un scénario en cas d'erreur.
Un message expliquant l'arrêt peut être spécifié avec le paramètre STOP_TEST_MSG

Chargement de l'environnement de test
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ce test réutilisable permet de charger dans le cache les données de son environnement de tests.
Par contre les adresses, compte d'accès des serveurs, etc.

Les paramètres à configurer:
 - ENVIRONMENT

L'environnement doit être spécifié en sélectionnant d'une variable réutilisable.

.. note:: 
 l'environnement peut être directement précisé au format JSON.
 Un exemple: 
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

Ce test réutilisable permet de générer un hash d'une valeur et de la stocker dans le cache.
Les paramètres à configurer:
 - DATA_IN
 - CACHE_KEY
 - SHA

Hash MD5
~~~~~~~~~

Ce test réutilisable permet de générer un hash md5 d'une valeur et de la stocker dans le cache.
Les paramètres à configurer:
 - DATA_IN
 - CACHE_KEY

UUID
~~~~

Ce test réutilisable permet de générer un id uuid et de la stocker dans le cache.
Les paramètres à configurer:
 - CACHE_KEY
 
BASE64
~~~~~~

Ce test réutilisable permet d'encoder ou décoder une chaine de caractère et de stocker le résultat dans le cache.
Les paramètres à configurer:
 - CACHE_KEY
 - DECODE
 - ENCODE
 - URLSAFE
 - STR_BASE64
 
GZIP
~~~~

Ce test réutilisable permet de compresser ou décompresser une chaine de caractère et de stocker le résultat dans le cache.
Les paramètres à configurer:
 - CACHE_KEY
 - COMPRESS
 - UNCOMPRESS
 - STR_GZIP
 
Protocoles réseaux
------------------

SSH
~~~

Ce test réutilisable permet d'envoyer un enchainement de commandes ssh.
Les paramètres à configurer:
 - SERVERS

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.

HTTP
~~~~

Ce test réutilisable permet d'envoyer une requête HTTP en vérifiant la réponse reçue.
Les paramètres à configurer:

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.

XML
~~~

Ce test réutilisable permet d'envoyer une requête HTTP avec du XML en vérifiant la réponse reçue.
Les paramètres à configurer:

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.


JSON
~~~~

Ce test réutilisable permet d'envoyer une requête HTTP avec du JSON en vérifiant la réponse reçue.
Les paramètres à configurer:

.. note: Il est possible d'exécuter le test plusieurs fois en fournissant une liste de serveur.

Interface utilisateur
---------------------

Contrôle applications
~~~~~~~~~~~~~~~~~~~~

Tests réutilisables permettant d'ouvrir ou de fermer une application sur un poste Windows ou Linux.
Les paramètres à configurer:
 - APP_PATH
 
.. warning: un agent de type `sikulix-server` est obligatoire.

Contrôle navigateur
~~~~~~~~~~~~~~~~~~~~

Tests réutilisables permettant d'ouvrir ou de fermer une navigateur sur un poste Windows ou Linux.
Les paramètres à configurer:
 - LOADING_URL
 
.. warning: un agent de type `selenium-server` est obligatoire.

Vérifications
-------------

Contenu de type XML
~~~~~~~~~~~~~~~~~~~

Ce test réutilisable permet de vérifier du contenu de type XML avec  l'outil xpath.
Les paramètres à configurer:
 - XML_STR
 - XML_XPATH
 - XML_NAMESPACES

Contenu de type JSON
~~~~~~~~~~~~~~~~~~~~

Ce test réutilisable permet de vérifier du contenu de type JSON avec l'outil jsonpath
Les paramètres à configurer:
 - JSON_STR
 - JSON_XPATH