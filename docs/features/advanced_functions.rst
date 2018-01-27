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

Ils est possible d'exécuter plusieurs tests en parallèle en utilisant la fonction ``Grouped``
Cette fonction est disponible à partir du client lourd ou bien depuis l'API.

Il est possible de sélectionner les tests et de choisir s'ils seront 
 - exécutés l'un après l'autre (sans lien)
 - ou exécutés en parallèle
 
.. image:: /_static/images/client/group_run.png

Depuis l'API, il faut utiliser la fonction ``/rest/tests/schedule/group``.

.. code-block::
  
  {
     "test": [
                "Common:/Samples/Tests_Unit/02_A.tux",
                "Common:/Samples/Tests_Unit/03_B.tux"
             ],
     "postpone-at": [],
     "parallel-mode": False,
     "postpone-mode": False
  }
  

.. important: Il n'y a aucune garantie que les tests vont démarrer en même temps.

Exécutions synchronisées
-----------------------

Partage des adaptateurs
~~~~~~~~~~~~~~~~~~~~~~~~

La fonction ``mode partagé`` permet de réutiliser le même adaptateur dans plusieurs cas de test.
Ce mode est à utiliser dans un scénario (test plan) ou un test suite avec plusieurs cas de tests.

Voici un exemple d'utilisation possible:
 - le test vérifie une application 
 - en arrière plan le test vérifie aussi en temps réel les logs générés par l'application
 - Il est donc possible d'influer sur le résultat du test en fonction de ce qui est trouvé dans les logs.

Pour activer le mode partagé, il faut mettre à True le paramètre ``shared``:

.. code-block:: python
  
  self.ADP_EXAMPLE = SutAdapters.Dummy.Adapter(
                                                parent=self, 
                                                debug=False, 
                                                name="MY_ADAPTER", 
                                                shared=True
                                            )


.. note:: Il est important de donner un nom à son adaptateur.

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

Automate
~~~~~~~~

Exécutions distribuées
----------------------


todo