Le moteur d'exécutions
======================

Ordonnanceur
--------------

Programmation des exécutions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

L'ordonnanceur présent dans le serveur permet de programmer l'exécution des tests de plusieurs manières.
 - Exécuter le test une seule fois dans ``x_secondes`` ou à ``date_heure``
 - Exécuter le test plusieurs fois à ``date_heure``.
 - Exécuter le test à chaque ``interval`` de ``heure_début`` à ``heure_fin``
 - Exécuter le test toutes les heures à une ``heure`` précise
 - Exécuter le test tous les jours à une ``heure`` précise
 - Exécuter le test une fois par semaine le ``jour de la semaine`` à une ``heure`` précise

.. image:: /_static/images/testlibrary/test_scheduling.png
   
Gestion des tâches
~~~~~~~~~~~~~~~~~~

Les actions suivantes sont disponibles pour gérer les tâches programmées par les utilisateurs:
 - annuler une ou plusieurs tâches
 - forcer l'arrêt d'une ou plusieurs tâches
 - reprogrammer une ou plusieurs tâches
 - visualiser l'historique des exécutions.
 
L'ensemble de ses actions est réalisable depuis le client lourd ou bien depuis l'API.

.. image:: /_static/images/client/task_manager.png

Exécutions parallélisées
----------------------

Ils est possible d'exécuter plusieurs tests en parallèle en utilisant la fonction ``Grouped``
Cette fonction est disponible à partir du client lourd ou bien depuis l'API.

Il est possible de sélectionner les tests et de choisir s'ils seront 
 - exécutés l'un après l'autre (sans lien)
 - ou exécutés en parallèle
 
.. image:: /_static/images/client/group_run.png

.. important: Il n'y a aucune garantie que les tests vont démarrer en même temps.

Exécutions synchronisées
-----------------------

todo

Partage des adaptateurs
~~~~~~~~~~~~~~~~~~~~~~~~

The shared mode is a feature used with adapters and libraries. When this mode is enabled, you can share adapters between several tests in a test plan.

An example, you need to execute a application and inspect the behaviour of logs received on a syslog server during the execution of your test. With a test plan in shared mode:

    You can inspect in background the syslog server
    Make actions to test the application
    Modify the test in realtime according the logs read from the syslog server.
    
Activate the shared mode on a adapter

The shared mode is supported on all adapters, to activate this mode, you must change the shared argument to True When this mode is activated, the adapter continue to run in background.

    Click on the button to create a new test

    Initialize the adapter on the prepare section of your test. Activate the shared mode, define also the name as below:

    self.ADP_EXAMPLE = SutAdapters.Dummy.Adapter(
                                                    parent=self, 
                                                    debug=False, 
                                                    name="MY_ADAPTER", 
                                                    shared=True
                                                )

    Save this test in the remote repository

    Create a test plan and import the previous test.

Retrieve a adapter from a testcase

    Click on the button to create a new test

    Add the following lines in the prepare section

    self.ADP_EXAMPLE = self.findAdapter(name="MY_ADAPTER")
    if self.ADP_EXAMPLE is None: Test(self).interrupt("unable to find the adapter")

    Import this test in the test plan created before.

    Execute the test, on the second testcase, you will interact with the adapter initialized from the first testcase.


Partage de donnée
~~~~~~~~~~~~~~~~~


todo

Exécutions distribuées
----------------------


todo