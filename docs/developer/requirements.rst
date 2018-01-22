Prérequis systèmes
=================

Serveur
------

+-----------------+------------+
|Caractéristiques |   Minimum  |
+-----------------+------------+
| OS              | CentOS 6.5 |
+-----------------+------------+
| Python          |    2.6     | 
+-----------------+------------+
| Arch            |    x86_64  |
+-----------------+------------+
| Mémoire         |    4Go     |
+-----------------+------------+
| CPU             |   2 Coeurs |
+-----------------+------------+
| Disque          |    ~50Go   |
+-----------------+------------+
| Réseau          |   1Gbit/s  |
+-----------------+------------+

..
	Pour Python, c'est bien 2.6 sur le serveur? pas 3.4?
	Je sais (vérifié) que 2 coeurs est bien assez, mais avais-tu une raison pour 4?  
	Même chose pour le 1Gbit du réseau et le 8Go de mémoire (serveur, client, outils).
	C'est important à savoir, puisque bon nombre vont rouler le serveur et les clients dans des machines virtuelles.

Client
------

+-----------------+---------------------------+
|Caractéristiques |   Minimum                 |
+-----------------+---------------------------+
| OS              | Windows 7 et plus, Linux  |
+-----------------+---------------------------+
| Arch            |    x86_64                 |
+-----------------+---------------------------+
| Mémoire         |    4Go                    |
+-----------------+---------------------------+
| Disque          |    ~1Go                   |
+-----------------+---------------------------+

.. note::

 L'architecture 32-bit n'est plus supportée depuis la version 17.0.0.  
 Cependant il est toujours possible de compiler les sources sur un environnement 32bits. 

Boite à outils
------------

+-----------------+----------------------------+
|Caractéristiques |   Minimum                  |
+-----------------+----------------------------+
| OS              | Windows 7 et plus, Linux   |
+-----------------+----------------------------+
| Arch            |    x86_64                  |
+-----------------+----------------------------+
| Mémoire         |    4Go                     |
+-----------------+----------------------------+
| Disque          |    ~1Go                    |
+-----------------+----------------------------+

.. note::

 L'architecture 32-bit n'est plus supportée depuis la version 17.0.0. 
 Cependant il est toujours possible de compiler les sources sur un environnement 32bits. 
