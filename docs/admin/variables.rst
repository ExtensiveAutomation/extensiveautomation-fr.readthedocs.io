Variables r�utilisables
=======================

Les variables r�utilisables sont principalement utilis�es pour d�crire son environnement de tests.

Ajout/suppression d'une variable
-----------------

L'ajout ou la suppression d'une variable peut se faire � travers l'interface web ou bien depuis l'api.
Le format attendu est de type `JSON`.

Description environnement de test
--------------------------

La description d'un environnement de test doit respecter le formalisme d�crit ci-dessous.
Ce type de d�claration est � utiliser avec le test r�utilisable qui initialise l'environnement 
et le met � disposition dans le cache.

D�claration d'un noeud SAMPLE_NODE:

.. code-block:: python

 {
	"COMMON": {
		"HOSTNAME": "extensivetesting"
	},
	"INSTANCES": {
		"SSH": {
			"ADMIN": {
				"SSH_DEST_HOST": "127.0.0.1",
				"SSH_DEST_PORT": 22,
				"SSH_DEST_LOGIN": "root",
				"SSH_DEST_PWD": "",
				"SSH_PRIVATE_KEY": null,
				"SSH_PRIVATE_KEY_PATH": null,
				"SSH_AGENT_SUPPORT": false,
				"SSH_AGENT": {
					"type": "ssh",
					"name": "agent.ssh01"
				}
			}
		}
	}
 }
 
D�claration d'une donn�e de test SAMPLE_DATASET_AUTH:

.. code-block:: python

 {
		 "login":         "admin",
		 "password":      ""
 }

D�claration de l'environnement SAMPLE_ENVIRONMENT:

.. code-block:: python

 {
	"PLATFORM": {
		"CLUSTER": [
			{ "NODE": "Common:SAMPLE_NODE" }
		]
	},
	"DATASET": [
		{ "AUTH": "Common:SAMPLE_DATASET_AUTH" }
	]
 }

