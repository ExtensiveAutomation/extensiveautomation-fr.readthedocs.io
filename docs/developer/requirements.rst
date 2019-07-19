Prérequis systèmes
=================

Serveur
------

Pour l'instant le serveur ne peut être exécuté que sur un environnement Linux.
Il est possible de l'exécuter sur un environnement virtuel ou physique.

+---------------------+------------+------------+
|Caractéristiques     |   Minimum  | Recommandé |
+---------------------+------------+------------+
| OS                  | Linux                   |
+---------------------+------------+------------+
| Python              |     2.7                 |
+---------------------+------------+------------+
| Arch                |         x86_64          |
+---------------------+------------+------------+
| Mémoire             |    4Go     |  8 Go      |
+---------------------+------------+------------+
| CPU                 |   2 Coeurs |  4 coeurs  |
+---------------------+------------+------------+
| Disque              |    ~10Go   |   ~50Go    |
+---------------------+------------+------------+
| Réseau              |   100Mb/s  |  1 Gbit/s  |
+---------------------+------------+------------+
| Nombre Utilisateur  |     2      |     5      |
+---------------------+------------+------------+

.. note:: Le support de Python 3.x est cours de développement.

.. note: Le serveur peut être faite sur n'importe quel système linux mais l'intégration est à faire manuellement.

Client
------

Le client peut être exécuté sur un environnement Windows ou Linux.

+-----------------+---------------------------+---------------------------+
|Caractéristiques |   Minimum                 | Recommandé                |
+-----------------+---------------------------+---------------------------+
| OS              | Windows 7+                | Windows 10+               |
|                 | Linux                     | Linux                     |
+-----------------+---------------------------+---------------------------+
| Arch            |                     x86_64                            |
+-----------------+---------------------------+---------------------------+
| Mémoire         |      4Go                  |     8Go                   |
+-----------------+---------------------------+---------------------------+
| Disque          |        ~1Go               |         ~2Go              |
+-----------------+---------------------------+---------------------------+

.. note::

 L'architecture 32-bit n'est plus supportée depuis la version 17.0.0.  
 Cependant il est toujours possible de compiler les sources sur un environnement 32bits. 

.. important:: Les plugins pour le client ne sont disponibles que pour l'environnement Windows.
 
Boite à outils
------------

La boite à outils peut être exécutée sur un environnement Windows ou Linux.

+-----------------+---------------------------+---------------------------+
|Caractéristiques |   Minimum                 | Recommandé                |
+-----------------+---------------------------+---------------------------+
| OS              | Windows 7+                | Windows 10+               |
|                 | Linux                     | Linux                     |
+-----------------+---------------------------+---------------------------+
| Arch            |                     x86_64                            |
+-----------------+---------------------------+---------------------------+
| Mémoire         |      4Go                  |     8Go                   |
+-----------------+---------------------------+---------------------------+
| Disque          |                    ~1Go                               |
+-----------------+---------------------------+---------------------------+

.. note::

 L'architecture 32-bit n'est plus supportée depuis la version 17.0.0. 
 Cependant il est toujours possible de compiler les sources sur un environnement 32bits. 

.. important:: Les plugins pour le client ne sont disponibles que pour l'environnement Windows.
