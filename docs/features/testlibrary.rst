Framework de test
================

Le framework de test fournit un cadre permettant de normaliser la création des cas de tests.
Les principales fonctionnalitées:
 - le support des cas de tests avec étapes
 - le support des extensions permettant de communiquer avec le système à tester ou piloter
 - la génération automatique des rapports de tests.

Cas de test
-----------

La création d'un cas de test dans la solution est normalisée.
Un cas de test de découpe en 4 sections:
 - description des différentes étapes du test (description)
 - préparation des extensions permettant de communiquer avec le système à tester ou piloter (prepare)
 - description du test (definition)
 - phase de nettoyage (cleanup)
 
Le résultat d'un cas de test est automatiquement calculé par le framework lorsque le test est terminé
en fonction des différentes étapes définits.
Il existe 3 résultats possibles:
 - PASS: toutes les étapes du tests ont été exécutés avec succès
 - FAILED: au moins une étape est en erreur après exécution
 - UNDEFINED: au moins une étape du test n'a pas été exécuté

.. notes: La section `cleanup` est systèmatiquement appéle, même en cas d'erreur.

Etapes de test
--------------

Un cas de test se découpe en sous étapes.
Une étape se définie par: 
 - un résumé de l'action à réaliser
 - la description détaillé de l'action à réaliser
 - la description du résultat attendus pour valider l'étape.

La définition des étapes du test sont à faire dans la section `description`:

.. code-block:: python

  self.step1 = self.addStep(
						expected="Logged in", 
						description="Login throught the rest api", 
						summary="Login throught the rest api", 
						enabled=True
					)
  

Le résultat d'une étape est à préciser dans la section `description`

Mettre le résultat à PASS

.. code-block:: python

  self.step1.setPassed(actual="step executed as expected")
  

Mettre le résultat à FAILED

.. code-block:: python

  self.step1.setFailed(actual="error to run the step")
  

.. notes: Il ne faut pas oublier de préciser le résultat d'une étape, sinon il sera considéré comme UNDEFINED.

Annulation d'un test
-------------------

Il est possible de forcer l'exécution d'un cas de test en utilisation la fonction `interrupt` dans la section description de votre test.

.. code-block:: python

  Test(self).interrupt(err="aborted by tester")
  

Utiliser la fonction interrupt permet d'arrêter le test et d'appeler automatiquement la section `cleanup` du cas de test.
Dans ce cas précis, l'argument `aborted` est positioné à True par le framework pour indiquer l'annulation du test.

.. code-block:: python

  def definition(self):
	Test(self).interrupt("bad response received")

  def cleanup(self, aborted):
	if aborted: self.step1.setFailed(actual="%s" % aborted)
	

Ajout de trace
--------------

Le framework mets à disposition des fonctions pour ajouter des messages durant l'exécution d'un test.
Les niveaux suivants sont disponibles:

 - info

	.. code-block:: python
 
		Trace(self).info(txt="hello world")

 - warning
 
	.. code-block:: python

		Trace(self).warning(txt="hello world")

 - error
 
	.. code-block:: python
 
		Trace(self).error(txt="hello world")

.. notes: si un message de niveau est `error` est affiché alors le résultat sera automatiquement positionné à FAILED

Stockage des données
--------------------

Publique
~~~~~~~~

Un espace publique est disponible sur le serveur de test. Cet espace permet de mettre à jour disposition des fichiers qui sont nécessaire durant l'exécution d'un test.
 
<ajouter_image>

   .. image:: /_static/images/testlibrary/espace_public.png

Les fichiers sont stockés dans le répertoire `/opt/xtc/current/Var/Public/` sur le serveur.

.. warning:: Cet espace est commun à l'ensemble des projets configurés sur le serveur.

Privé
~~~~~

L'espace de stockage privé n'existe que durant l'exécution d'un test.
Il permet de sauvegarder des logs générés ou récupérer lors de l'exécution du test.
Ces logs sont automatiquement mis à disposition de l'utilisateur lorsque le test est terminé dans un fichier zip
Ils sont récupables depuis le client ou bien depuis l'API du serveur.

.. image:: /_static/images/testlibrary/private_storage.png
  
Les logs sont organisés par répertoire:
 - Répertoire TC-TESTCASE-#<id_tc>: contient les logs générés par le cas de test
 - Répertoire ADP-#<id_adp>: contient les logs générés par les différents adaptateurs utilisés durant le test

.. image:: /_static/images/testlibrary/private_storage_zip.png

Exemple pour sauvegarder du texte `hello world` dans un fichier `my_logs` depuis le cas de test

.. code-block:: python
 
  Private(self).saveFile(destname="my_logs", data="hello world")
  

Exemple pour ajouter du texte dans un fichier de log déjà existant

.. code-block:: python
 
  Private(self).appendFile(destname="my_logs", data="hello world2")
  

.. notes: Il est possible de sauvegarder des fichiers depuis un adaptateur
	
En cache
~~~~~

Le framework de test permet de partager des données entre les cas de tests.
Cette fonction peut être nécessaire lors de l'écriture d'un scénario de test avec un test plan.

Le cache est de type clé/valeur.

.. image:: /_static/images/testlibrary/client_cache.png

Exemple pour sauvegarder une valeur dans le cache

.. code-block:: python
 
  Cache().set(name="my_data", data="hello")
  

Lire une valeur depuis le cache

.. code-block:: python
 
  my_data= Cache().get(name="my_data")
  Trace(self).warning(my_data)
  

Exemple pour capturer une donnée avec une expression régulière et l'enregistrer dans le cache

.. code-block:: python
 
  my_data="March, 25 2017 07:38:58 AM"
  
  Cache().capture(data=my_data, regexp=".* (?P<TIME>\d{2}:\d{2}:\d{2}) .*")
  
  Trace(self).info( txt=Cache().get(name="TIME") )
  

Mettre en attente
-----------------

Cette fonction permet de faire une pause durant l'exécution d'un test.

Exemple de mise en attente pendant 10 secondes: 

.. code-block:: python
 
  Time(self).wait(timeout=10)
	

Exemple de mise en attente tant qu'on est pas le 12 septembre 2016 à 2h: 

.. code-block:: python
 
  Time(self).waitUntil(dt='2016-09-12 02:00:00', fmt='%Y-%m-%d %H:%M:%S', delta=0)
	

Interaction avec le testeur
---------------------------

Le framework permet d'écrire des tests semi-automatiques, c'est à dire en mode automatique.
Cette fonction peut être intéressant pour faire un test en mode question/réponse (ex: configuration d'un équipement)

Exemple demandant le nom de la personne:

.. code-block:: python

  user_rsp = Interact(self).interact(ask="Your name?", timeout=30.0, default=None)
	

.. notes: si aucune réponse n'est fournie dans le temps imparti, il est possible de fournir une valeur par défaut avec l'argument `default`

Les variables d'un test
-----------------------

Variables entrantes
~~~~~~~~~~~~~~~~~~

Les paramètres entrants (inputs) sont à utiliser pour ajouter des variables sur un test.

<inserer image>

Il existent plusieurs types de paramètres:

+----------------+----------------------------------------------------------+
| Type           |  Description usage                                       |
+----------------+----------------------------------------------------------+
| str/pwd        | chaine de caractère                                      |
+----------------+----------------------------------------------------------+
| text           | chaine de caractère multiligne                           |
+----------------+----------------------------------------------------------+
| custom         | paramètre avancé                                         |
+----------------+----------------------------------------------------------+
| list           | liste de chaine de caractère                             |
+----------------+----------------------------------------------------------+
| bool           | valeur boolean                                           |
+----------------+----------------------------------------------------------+
| hex            | valeur hexadécimal                                       |
+----------------+----------------------------------------------------------+
| none           | valeur nulle                                             |
+----------------+----------------------------------------------------------+
| alias          | raccourci paramètre                                      |
+----------------+----------------------------------------------------------+
| shared         | valeur depuis les variables projets                      |
+----------------+----------------------------------------------------------+
| list-shared    | liste de valeurs de variables projets                    |
+----------------+----------------------------------------------------------+
| cache          | clé d'une valeur présence dans le cache                  |
+----------------+----------------------------------------------------------+
| int            | entier                                                   |
+----------------+----------------------------------------------------------+
| float          | décimal                                                  |
+----------------+----------------------------------------------------------+
| dataset        | intégre un fichier de type dataset                       |
+----------------+----------------------------------------------------------+
| remote-image   | intégre une image présent dans le dépôts de tests        |
+----------------+----------------------------------------------------------+
| local-image    | intégre une image présente en local sur un le poste      |
+----------------+----------------------------------------------------------+
| snapshot-image | intégre une capture d'écran                              |
+----------------+----------------------------------------------------------+
| local-file     | intégre un fichier présent en local sur le poste         |
+----------------+----------------------------------------------------------+
| date           | date                                                     |
+----------------+----------------------------------------------------------+
| time           | heure                                                    |
+----------------+----------------------------------------------------------+
| date-time      | date et heure                                            |
+----------------+----------------------------------------------------------+
| self-ip        | liste des adresses ip du serveur                         |
+----------------+----------------------------------------------------------+
| self-mac       | liste des adresses mac du serveur                        |
+----------------+----------------------------------------------------------+
| sef-eth        | liste des interfaces réseau du serveur                   |
+----------------+----------------------------------------------------------+
| json           | returne une valeur au format json                        |
+----------------+----------------------------------------------------------+

Les variables sont accessibles depuis un test avec la fonction `input(...)`

.. code-block:: python

  input('DEBUG')
  

.. notes:

  Le nom d'un paramètre est unique et obligatoirement en majuscule.

  Il est possible d'afficher des variables dans le rapport de test en préfixant les variables:
   - SUT_		Variables décrivant la version du système à tester ou piloter
   - DATA_		Variables décrivant des données spécifiques
   - USER_		Variables utilisateurs
  
  Cette fonctionnalité peut être utile pour augmenter le niveau de tracabilité dans les rapports.
  
  <insérer image exemple>
  
Variable personnalisable
~~~~~~~~~~~~~~~

Ce type de paramètre est intéressant car il permet de constuire des valeurs appelant d'autres variables.

Prenons l'exemple d'un test contenant les 2 variables suivantes:
 - DEST_IP avec la valeur 192.168.1.1
 - DEST_PORT avec la valeur 8080

Le type `custom` va nous permettre de constuire une 3ième variable 
 - DEST_URL avec la valeur https://[!INPUT:DEST_IP:]:[!INPUT:DEST_PORT]/welcome

Le mot clé `[!INPUT:<NOM_VARIABLE_ENTRANTE:]` permet d'appeler une autre variable entrante.
Le framework remplacera au moment de l'exécution du test les différents mots clés avec la valeur associée.
On obtiendra comme valeur https://192.168.1.1:8080/welcome pour la variable DEST_URL.

Variable alias
~~~~~~~~~~~~~~

Un alias de paramètre peut être utilise durant la définition d'un test plan.
La création d'un alias permet de changer le nom d'un paramètre sans changer le nom initial.

Variable agents
~~~~~~~~~~~~~~

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
  
