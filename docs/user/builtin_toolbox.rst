Boite à outils
==============

La boite à outils permet de démarrer des agents sur des postes dédiés. Les agents sont indispensables pour exécuter des tests avec Selenium sur des postes dédiés ou bien pour déporter l'exécution d'un test.


.. image:: /_static/images/toolbox/toolbox.png
   
Déploiement
-----------

Cette fenêtre permet de choisir l'agent  à démarrer. Le type d'agent à démarrer peut être choisi 
dans la liste déroulante. Enfin un agent nécessite d'être enregistré auprès du serveur de test pour pouvoir l'utiliser.

Un agent va permettre de faire une exécution distribuée de vos tests. 
Par exemple, un agent déployé sur plusieurs machines va permettre d'exécuter le même test sur différent environnement à tester ou piloter.

La liste complète des agents disponibles sont décrits dans le chapitre `Compléments Serveur > Agents`.

.. note:: Le nom de l'agent doit être unique pour réussir l'enregistrement.

.. tip:: 
  Pour une meilleure visibilité des agents disponibles, il est conseillé de respecter le formalisme suivant
  pour les noms:
    [agent].[environnement].[prénom_testeur].[nom][numéro_instance]
    
    Exemple:
        agent.win.denis.socket01

Exemple d'un agent déployé et en cours d'exécution:

.. image:: /_static/images/toolbox/agent_deployed.png

Compléments
-----------

La boite à outils peut être enrichie avec de nouveaux plugins.

Pour ce faire il faut suivre la procédure décrite dans le chapitre `Contributions > Développement plugins > Boites à outils`.
Les plugins sont à déposer dans le répertoire ``Plugins``.

.. image:: /_static/images/toolbox/toolbox_plugins_install.png

Après redémarrage de la boite à outils, le complément apparait dans la liste des agents ``external``

.. image:: /_static/images/toolbox/toolbox_plugins.png