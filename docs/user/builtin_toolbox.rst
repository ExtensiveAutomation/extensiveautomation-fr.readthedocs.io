Boite à outils
==============

La boite à outils permet de démarrer des agents ou des sondes sur des postes dédiés.

 - Les agents sont indispensables pour exécuter des tests avec Selenium sur des postes dédiés ou bien pour déporter l'exécution d'un test.
 - Les sondes peuvent être utilisées pour récupérer des logs automatiquement durant l'exécution d'un test.

.. image:: /_static/images/toolbox/toolbox.png
   
Déploiement
-----------

Cette fenêtre permet de choisir l'agent ou la sonde à démarrer. Le type d'agent ou sonde à démarrer peut être choisi 
dans la liste déroulante. Enfin un agent ou sonde nécessite d'être enregistré auprès du serveur de test pour pouvoir l'utiliser.

Un agent va permettre de faire une exécution distribuée de vos tests. 
Par exemple, un agent déployé sur plusieurs machines va permettent d'exécuter le même test sur différent environnement à tester ou piloter.

La liste complète des agents et sondes disponibles sont décrits dans le chapitre `Compléments Serveur > Agents ou Sondes`.

.. note:: Le nom de l'agent ou la sonde doit être unique pour réussir l'enregistrement.

.. tip:: 
  Pour une meilleur visibilité des agents ou sondes disponibles, il est conseillé de respecter le formalisme suivant
  pour les noms:
    [agent|sonde].[environnement].[prénom_testeur].[nom][numéro_instance]
    
    Exemple:
        agent.win.denis.socket01

Exemple d'un agent déployé et en cours d'exécution:

.. image:: /_static/images/toolbox/agent_deployed.png

Compléments
-----------

La boite à outils peut être enrichie avec de nouveaux plugins.

Pour ce faire il faut suivre la procédure décrite dans le chapitre :doc:`developer\contributions` `Contributions > Développement plugins > Boites à outils`.
Les plugins sont à déposer dans le répertoire ``Plugins``.

.. image:: /_static/images/toolbox/toolbox_plugins_install.png

Après redémarrage de la boite à outils, le complément apparait dans la liste des agents ``external``

.. image:: /_static/images/toolbox/toolbox_plugins.png