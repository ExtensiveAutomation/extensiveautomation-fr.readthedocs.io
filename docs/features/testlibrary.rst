Les fondamentaux
================

Le framework de test fournit un cadre permettant de normaliser la création des cas de tests.

Les principales fonctionnalités sont:
 - le support des cas de tests avec étapes
 - le support des extensions permettant de communiquer avec le système à tester ou piloter
 - la génération automatique des rapports de tests.

Cas de test
-----------

La création d'un cas de test dans la solution est normalisée.

Un cas de test se découpe en 4 sections:
 - ``description``: description des différentes étapes du test
 - ``prepare``: préparation des adaptateurs et librairies permettant de communiquer avec le système à tester ou piloter
 - ``definition``: déroulement du test
 - ``cleanup``: phase de nettoyage
 
Le résultat d'un cas de test est automatiquement calculé par le framework lorsque le test est terminé
en fonction des différentes étapes définies.

Il existe 3 résultats possibles:
 - ``PASS``: toutes les étapes du tests ont été exécutées avec succès
 - ``FAILED``: au moins une étape est en erreur après exécution
 - ``UNDEFINED``: au moins une étape du test n'a pas été exécutée

.. note:: La section ``cleanup`` est systématiquement appelée, même en cas d'erreur.

Etapes de test
--------------

Un cas de test se découpe en sous-étapes.

Une étape se définit par: 
 - un résumé de l'action à réaliser
 - la description détaillée de l'action à réaliser
 - la description du résultat attendu pour valider l'étape.

La définition des étapes du test doit être faite dans la section ``description``:

.. code-block:: python

  self.step1 = self.addStep(
						expected="Logged in", 
						description="Login throught the rest api", 
						summary="Login throught the rest api", 
						enabled=True
					)
  

Le résultat d'une étape est à préciser dans la section ``definition``

Exemple pour mettre le résultat à ``PASS`` ou ``FAILED``

.. code-block:: python

  self.step1.setPassed(actual="step executed as expected")
  
  self.step1.setFailed(actual="error to run the step")

.. warning:: Il ne faut pas oublier de démarrer une étape avec la fonction ``start`` sinon il n'est pas possible de mettre le résultat.

.. note:: Il ne faut pas oublier de préciser le résultat d'une étape, sinon il sera considéré comme ``UNDEFINED``.

.. important:: Une étape positionnée à ``FAILED`` ne pourra pas devenir ``PASS`` par la suite dans un test.

Annulation d'un test
-------------------

Il est possible de forcer l'exécution d'un cas de test en utilisant la fonction ``interrupt`` dans la section ``description`` de votre test.

.. code-block:: python

  Test(self).interrupt(err="aborted by tester")
  

Utiliser la fonction ``interrupt`` permet d'arrêter le test et d'appeler automatiquement la section ``cleanup`` du cas de test.
Dans ce cas précis, l'argument ``aborted`` est mis à True par le framework pour indiquer l'annulation du test.

.. code-block:: python

  def definition(self):
	Test(self).interrupt("bad response received")

  def cleanup(self, aborted):
	if aborted: self.step1.setFailed(actual="%s" % aborted)
	

Ajout de trace
--------------

Le framework met à disposition certaines fonctions pour ajouter des messages durant l'exécution d'un test.

Les niveaux suivants sont disponibles:

 - Exemple pour afficher un message de type ``info``

	.. code-block:: python
 
		Trace(self).info(txt="hello world")

 - Exemple pour afficher un message de type ``warning``
 
	.. code-block:: python

		Trace(self).warning(txt="hello world")

 - Exemple pour afficher un message de type ``error``
 
	.. code-block:: python
 
		Trace(self).error(txt="hello world")

.. note:: Si un message de niveau ``error`` est affiché alors le résultat sera automatiquement mis à ``FAILED``.

.. note:: Les messages apparaissent automatiquement dans le rapport basique.

Données
--------------------

Public
~~~~~~

Un espace public est disponible sur le serveur de test. Cet espace permet de mettre à disposition des fichiers qui sont nécessaire durant l'exécution d'un test.

   .. image:: /_static/images/testlibrary/espace_public.png

Les fichiers sont stockés dans le répertoire ``/opt/xtc/current/Var/Public/`` sur le serveur.

.. warning:: Cet espace est commun à l'ensemble des projets configurés sur le serveur.

Privé
~~~~~

L'espace de stockage privé n'existe que durant l'exécution d'un test.
Il permet de sauvegarder des logs générés ou récupérés lors de l'exécution du test.
Ces logs sont automatiquement mis à la disposition de l'utilisateur dans un fichier zip lorsque le test est terminé.
Ils sont récupables depuis le client ou bien depuis l'API du serveur.

.. image:: /_static/images/testlibrary/private_storage.png
  
Les logs sont organisés par répertoire:
 - Répertoire TC-TESTCASE-#<id_tc>: contient les logs générés par le cas de test
 - Répertoire ADP-#<id_adp>: contient les logs générés par les différents adaptateurs utilisés durant le test

.. image:: /_static/images/testlibrary/private_storage_zip.png

Exemple pour sauvegarder le texte `hello world` dans un fichier `my_logs` depuis le cas de test

.. code-block:: python
 
  Private(self).saveFile(destname="my_logs", data="hello world")
  

Exemple pour ajouter du texte dans un fichier de log déjà existant

.. code-block:: python
 
  Private(self).appendFile(destname="my_logs", data="hello world2")
  

.. note:: 
  Il est aussi possible de sauvegarder des fichiers depuis un adaptateur.
  Ils seront automatiquement stockés dans un répertoire portant le nom de l'adaptateur.
  
  .. image:: /_static/images/testlibrary/adapter_private.png
	
En cache
~~~~~

Le framework de test permet de stocker en cache des données sous la forme clé/valeur.
Cette fonction peut être nécessaire pour partager des données entre tests lors de l'écriture d'un scénario par exemple.

.. image:: /_static/images/testlibrary/client_cache.png

Exemple pour sauvegarder une valeur dans le cache

.. code-block:: python
 
  Cache().set(name="my_data", data="hello")
  

Lire une valeur depuis le cache

.. code-block:: python
 
  my_data= Cache().get(name="my_data")
  Trace(self).warning(my_data)
  

Exemple pour capturer une donnée avec une expression régulière et avec enregistrement dans le cache

.. code-block:: python
 
  my_data="March, 25 2017 07:38:58 AM"
  
  Cache().capture(data=my_data, regexp=".* (?P<TIME>\d{2}:\d{2}:\d{2}) .*")
  
  Trace(self).info( txt=Cache().get(name="TIME") )
  
.. image:: /_static/images/testlibrary/client_cache_capture.png

Il est aussi possible de s'appuyer sur un paramètre de type ``custom`` pour fournir l'expression régulière.

.. code-block:: python
  
  .*session_id=[!CAPTURE:SESSIONID:];expires.*
  

ou en mode ``greedy``

.. code-block:: python
  
  .*session_id=[!CAPTURE:SESSIONID:.*?];.*
  
  
.. important:: Le cache n'existe que durant l'exécution d'un test.

Mettre en attente
-----------------

Cette fonction permet de faire une pause durant l'exécution d'un test.

Exemple de mise en attente pendant 10 secondes: 

.. code-block:: python
 
  Time(self).wait(timeout=10)
	

Exemple de mise en attente tant que la date et heure courante ne correspondent pas à la date indiquée:

.. code-block:: python
 
  Time(self).waitUntil(dt='2016-09-12 02:00:00', fmt='%Y-%m-%d %H:%M:%S', delta=0)
	

Interaction avec le testeur
---------------------------

Le framework permet d'écrire des tests semi-automatiques, c'est à dire en mode interaction.
Cette fonction peut être intéressante pour faire un test en mode question/réponse (ex: configuration d'un équipement)

Exemple demandant le nom de la personne:

.. code-block:: python

  user_rsp = Interact(self).interact(ask="Your name?", timeout=30.0, default=None)
	
Depuis le client, l'onglet ``Interact`` apparait automatiquement pour répondre à la question posée durant
l'exécution du test.
Cette fenêtre est disponible depuis le fenêtre d'analyse.

.. image:: /_static/images/testlibrary/client_interact.png

.. note::  Si aucune réponse n'est fournie dans le temps imparti, il est possible de fournir une valeur par défaut avec l'argument ``default``.

Paramètres d'un test
-----------------------

Les entrants
~~~~~~~~~~~~~~~~~~

Les paramètres entrants (inputs) sont à utiliser pour ajouter des variables sur un test.
Ils sont configurables depuis le client.

Il existe plusieurs types de paramètres:

+----------------+----------------------------------------------------------+
| Type           |  Description usage                                       |
+----------------+----------------------------------------------------------+
| str/pwd        | chaîne de caractères                                     |
+----------------+----------------------------------------------------------+
| text           | chaîne de caractères multiligne                          |
+----------------+----------------------------------------------------------+
| custom         | paramètre avancé                                         |
+----------------+----------------------------------------------------------+
| list           | liste de chaînes de caractères                           |
+----------------+----------------------------------------------------------+
| bool           | valeur booléen                                           |
+----------------+----------------------------------------------------------+
| hex            | valeur hexadécimale                                      |
+----------------+----------------------------------------------------------+
| none           | valeur nulle                                             |
+----------------+----------------------------------------------------------+
| alias          | raccourci paramètre                                      |
+----------------+----------------------------------------------------------+
| shared         | valeur depuis les variables projets                      |
+----------------+----------------------------------------------------------+
| list-shared    | liste de valeurs de variables projets                    |
+----------------+----------------------------------------------------------+
| cache          | clé d'une valeur présente dans le cache                  |
+----------------+----------------------------------------------------------+
| int            | entier                                                   |
+----------------+----------------------------------------------------------+
| float          | décimal                                                  |
+----------------+----------------------------------------------------------+
| dataset        | intègre un fichier de type dataset                       |
+----------------+----------------------------------------------------------+
| remote-image   | intègre une image présente dans le dépôts de tests       |
+----------------+----------------------------------------------------------+
| local-image    | intègre une image présente en local sur un le poste      |
+----------------+----------------------------------------------------------+
| snapshot-image | intègre une capture d'écran                              |
+----------------+----------------------------------------------------------+
| local-file     | intègre un fichier présent en local sur le poste         |
+----------------+----------------------------------------------------------+
| date           | date                                                     |
+----------------+----------------------------------------------------------+
| time           | heure                                                    |
+----------------+----------------------------------------------------------+
| date-time      | date et heure                                            |
+----------------+----------------------------------------------------------+
| self-ip        | liste des adresses IP du serveur                         |
+----------------+----------------------------------------------------------+
| self-mac       | liste des adresses MAC du serveur                        |
+----------------+----------------------------------------------------------+
| sef-eth        | liste des interfaces réseau du serveur                   |
+----------------+----------------------------------------------------------+
| json           | returne une valeur au format JSON                        |
+----------------+----------------------------------------------------------+

Les variables sont accessibles depuis un test avec la fonction ``input(...)``

.. code-block:: python

  input('DEBUG')
  
**Le paramètre custom**

Le type ``custom`` permet de construire des paramètres utilisants d'autre paramètre ou le cache.
Ils est donc possible d'utiliser des mots clés qui seront interprétés par le framework de test 
au moment de l'exécution.

Liste des mots clés disponibles:

+-------------------+--------------------------------------------------------------------+
| Mots clés         |   Description                                                      |
+-------------------+--------------------------------------------------------------------+
| ``[!INPUT:  :]``  |  Permet de récupérer la valeur d'un paramètre présent dans le test |
+-------------------+--------------------------------------------------------------------+
| ``[!CACHE:   :]`` |  Permet de récupérer une valeur présente dans le cache             |
+-------------------+--------------------------------------------------------------------+

.. note:: Le nom d'un paramètre est unique et obligatoirement en majuscule.


Les agents
~~~~~~~~~~~~~~


.. image:: /_static/images/examples/client_properties_agent.png

.. image:: /_static/images/examples/client_agent_support.png


Il est possible d'accéder à la liste des agents depuis un test en utilisant le mode clé ``agent()``.

.. code-block:: python

  self.ADP_REST= SutAdapters.REST.Client(
                                            parent=self,
                                            destinationIp=input('HOST'),
                                            destinationPort=input('PORT'),
                                            debug=input('DEBUG'),
                                            sslSupport=input('USE_SSL'),
                                            agentSupport=input('SUPPORT_AGENT'), 
                                            agent=agent('AGENT_SOCKET')
                                           )
  
Les probes
~~~~~~~~~~


.. image:: /_static/images/examples/probe_tab.png


Import/export des paramètres
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Les paramètres de tests peuvent être exportés dans un type de fichier dédié ``testconfig`` (tcx).
Il est donc possible de travailler/préparer les paramètres sans avoir le test.

.. image:: /_static/images/client/client_testconfig_export.png

A l'inverse il est possible d'importer un fichier de configuration dans un test.
L'import écrasera l'ensemble des paramètres si le nom est identique.

.. image:: /_static/images/client/client_testconfig_import.png

