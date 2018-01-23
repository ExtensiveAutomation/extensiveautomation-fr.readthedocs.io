Boite à outils
==============

La boite à outils permet de démarrer des agents ou des sondes sur des postes dédiés.

 - Les agents sont indispensables pour exécuter des tests avec Selenium sur des postes dédiés ou bien pour déporter l'exécution d'un test.
 - Les sondes peuvent être utilisées pour récupérer des logs automatiquement durant l'exécution d'un test.

.. image:: /_static/images/toolbox/toolbox.png
   
Fenêtre de déploiement
---------------

Cette fenêtre permet de choisir l'agent ou la sonde à démarrer. Le type d'agent ou sonde à démarrer peut être choisi dans la liste déroulante. 
Enfin un agent ou sonde nécessite d'être enregistré auprès du serveur de test pour pouvoir l'utiliser.

.. note:: Le nom de l'agent ou la sonde doit être unique pour réussir l'enregistrement.

EXPLIQUER LA LOGIQUE DANS LES NOMS DONNÉS AUX AGENTS ET SONDES
 
EXPLIQUER POURQUOI ET COMMENT UTILISER CHAQUE AGENT ET SONDE, AVEC EXEMPLES, REQUIS, WARNINGS, ETC.

Agents:

 - dummy
	pour tester le déroulement basique d'un test, ne retourne rien

 - socket

 - ftp

 - sikulix-server

 - selenium3-server

 - selenium2-server

 - soapui

 - command

 - file

 - adb

 - gateway-sms

 - database

 - ssh

Sondes:

 - dummy
 
 - textual
 
 - network
 
 - file
 
 
EXPLIQUER COMMENT FAIRE DES TESTS SUR PLUSIEURS MACHINES EN PARALLÈLE ROULANT LE MEME TYPE D'AGENT
 - MEME TEST SUR PLUSIEURS MACHINES (comment configurer un test pour ça)
 - MEME SETUP DE COLLECTION DE DONNÉES ET AGENT SUR PLUSIEURS MACHINES, À PARTIR DE TEMPLATE AUTO-INCRÉMENTÉ
 - DÉFINITION DE POOLS DE MACHINES CONTENANT DES AGENTS IDENTIQUES, POUR TESTS DE ROBUSTESSE/STRESS (comment définir et utiliser dans un test)
 - COMMENT ROULER LE MÊME TEST SELENIUM SUR PLUSIEURS BROWSERS DIFFÉRENTS (expliquer le setup des agents/adaptateurs, et la config du test)


Compléments
-----------

Il est possible d'ajouter des plugins, ils sont à ajouter dans le répertoire "Plugins".