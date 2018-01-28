Le moteur d'exécutions
======================

L'ordonnanceur
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

.. note:: Une tâche récursive sera automatiquement relancée par le serveur après un redémarrage.
 
La gestion des tâches
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

Il est possible d'exécuter plusieurs tests en parallèles en utilisant la fonction ``Grouped``
Cette fonction est disponible à partir du client lourd ou bien depuis l'API.

Il existe 2 options d'exécutions:
 - exécution des tests l'un après l'autre (sans lien)
 - ou exécution en parallèle
 
.. image:: /_static/images/client/group_run.png

.. note:: 
  Depuis l'API, il faut utiliser la fonction ``/rest/tests/schedule/group``.

  .. code-block:: json
    
    {
     "test": [
                "Common:/Samples/Tests_Unit/02_A.tux",
                "Common:/Samples/Tests_Unit/03_B.tux"
             ],
     "postpone-at": [],
     "parallel-mode": False,
     "postpone-mode": False
    }
  

.. important:: Il n'y a aucune garantie que les tests vont démarrer en même temps avec ce mode d'exécution.

Exécutions synchronisées
-----------------------

Partage des adaptateurs
~~~~~~~~~~~~~~~~~~~~~~~~

La fonction ``mode partagé`` permet de réutiliser le même adaptateur dans plusieurs cas de test.
Ce mode est à utiliser dans un scénario (test plan) ou un test suite avec plusieurs cas de tests.

Voici un exemple d'utilisation possible:
 - le scénario teste une application 
 - en arrière plan le scénario vérifie aussi les logs générés par l'application
 - Il est donc possible d'influer sur le résultat du test en fonction de ce qui est trouvé dans les logs.

Pour activer le mode partagé, il faut mettre à True le paramètre ``shared`` et donner un nom à l'adaptateur:

.. code-block:: python
  
  self.ADP_EXAMPLE = SutAdapters.Dummy.Adapter(
                                                parent=self, 
                                                debug=False, 
                                                name="MY_ADAPTER", 
                                                shared=True
                                            )


.. note:: 
 Il est important de donner un nom à son adaptateur car ça permet de le retrouver plus facilement.
 Si aucun nom n'est donné, le framework configure l'adaptateur avec un nom aléatoire.

Après initilisation de l'adaptateur il est possible de récupérer un adaptateur
depuis un autre cas de test en le recherchant par son nom.

.. code-block:: python
  
  self.ADP_EXAMPLE = self.findAdapter(name="MY_ADAPTER")
  if self.ADP_EXAMPLE is None: Test(self).interrupt("unable to find the adapter")
  

Partage de donnée
~~~~~~~~~~~~~~~~~

Le cache étant unique lorsqu'un test (peu importe le type) est exécuté, il est possible d'échanger des données
entre plusieurs cas de test.

Un premier test peut enregistrer une donnée dans le cache et un 2ième test peut récupérer la valeur 
stockée par le 1er test.

Synchronisation
~~~~~~~~~~~~~~~

Une exécution synchronisée de plusieurs cas de test est possible en utilisant un scénario (testplan).
Ce scénario doit contenir:
 - un cas de test observateur
 - un ou plusieurs cas de tests exécutant des actions en arrière plan

Le test observateur doit être utilisé pour faire le lien entre les différents adaptateurs.

.. important:: L'utilisation d'adaptateurs en mode partagé est obligatoire.

.. note:: Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Non_Sequential``.

Exécutions distribuées
----------------------

La solution permet de faire des exécutions distribuées en utilisant des agents répartis à travers le réseaux.
