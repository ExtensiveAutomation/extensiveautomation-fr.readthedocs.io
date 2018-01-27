L'ordonnanceur
============

Programmation des exécutions
----------------------------

L'ordonnanceur présent dans le serveur permet de programmer l'exécution des tests de plusieurs manières.
 - Exécuter le test une seule fois dans ``x_secondes`` ou à ``date_heure``
 - Exécuter le test plusieurs fois à ``date_heure``.
 - Exécuter le test à chaque ``interval`` de ``heure_début`` à ``heure_fin``
 - Exécuter le test toutes les heures à une ``heure`` précise
 - Exécuter le test tous les jours à une ``heure`` précise
 - Exécuter le test une fois par semaine le ``jour de la semaine`` à une ``heure`` précise

.. image:: /_static/images/testlibrary/test_scheduling.png
   
Gestion des tâches
------------------

Les actions suivantes sont disponibles pour gérer les tâches programmées par les utilisateurs:
 - annuler une ou plusieurs tâches
 - forcer l'arrêt d'une ou plusieurs tâches
 - reprogrammer une ou plusieurs tâches
 - visualiser l'historique des exécutions.
 
L'ensemble de ses actions est réalisable depuis le client lourd ou bien depuis l'API.

.. image:: /_static/images/client/task_manager.png