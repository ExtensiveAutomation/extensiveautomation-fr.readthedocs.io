L'interopérabilité
===================

Adaptateurs
-----------

Les adaptateurs permettent de communiquer avec le système à tester ou piloter. La solution embarque plusieurs adaptateurs par défaut dans différents domaines:
 - support de protocoles réseaux
 - support de protocoles niveau application
 - communication avec les bases de données
 - interaction systèmes
 - interaction avec les interfaces graphiques
 - support de protocoles télécom

Les adaptateurs ont deux modes d'utilisation:
 - un mode direct: la communication se fait directement depuis le serveur de test vers le système à contrôler.
 - un mode agent: la communication avec le système à contrôler se fait par l'intermédiaire d'un agent communiquant avec le serveur de test.

.. note:: Le mode ``Verbose`` est activé par défaut sur tous les adapateurs. Ce mode peut être désactivé pour réduire le nombre d'évènements durant un test.

.. note:: Le mode ``Debug`` n'est pas activé par défaut. Il peut être activé en cas de problème.

.. note:: 
  Des exemples sont disponibles dans les échantillons de tests ``Samples/Tests_Adapters``
  
Liste des adaptateurs disponibles par défaut:

Protocoles réseaux
~~~~~~~~~~~~~~~~~~~~

+--------------+--------------+-----------------------------------------------------------------------------+
| Adaptateurs  | Agents       | Descriptions                                                                |
+--------------+--------------+-----------------------------------------------------------------------------+	
| ARP          | socket       | Sniffer permettant d'envoyer et recevoir des packets ARP                    |
+--------------+--------------+-----------------------------------------------------------------------------+
| ICMP         | socket       | Sniffer permettant d'envoyer et recevoir des packets ICMP                   |
+--------------+--------------+-----------------------------------------------------------------------------+
| Ethernet     | socket       | Sniffer permettant d'envoyer et recevoir des frames Ethernet                |
+--------------+--------------+-----------------------------------------------------------------------------+
| IP           | socket       | Sniffer permettant d'envoyer et recevoir des packets IPv4                   |
+--------------+--------------+-----------------------------------------------------------------------------+
| Pinger       | non supporté | Tests de vie de machines via ICMP, TCP ou une URL                           |
+--------------+--------------+-----------------------------------------------------------------------------+
| UDP/TCP      | socket       | Sniffer et client UDP et TCP                                                |
+--------------+--------------+-----------------------------------------------------------------------------+
| NTP          | socket       | Client permetttant de requêter un serveur NTP                               |
+--------------+--------------+-----------------------------------------------------------------------------+
| DNS          | non supporté | Client résolveur                                                            |
+--------------+--------------+-----------------------------------------------------------------------------+	
| SNMP         | socket       | Réception d'alarmes SNMPv2                                                  |
+--------------+--------------+-----------------------------------------------------------------------------+						

Protocoles réseaux applications
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+--------------+--------------+-----------------------------------------------------------------------------+
| Adaptateurs  | Agents       | Descriptions                                                                |
+--------------+--------------+-----------------------------------------------------------------------------+
| HTTP         | socket       | Serveur et client avec le support TLS et proxy                              |
+--------------+--------------+-----------------------------------------------------------------------------+
| SOAP         | socket       | Client avec le support TLS et proxy                                         |
+--------------+--------------+-----------------------------------------------------------------------------+
| REST         | socket       | Client avec le support TLS et proxy                                         |
+--------------+--------------+-----------------------------------------------------------------------------+
| WebSocket    | socket       | Client websocket                                                            |
+--------------+--------------+-----------------------------------------------------------------------------+
| SoapUI       | soapui       | Client permettant d'exécuter des campagnes SoapUI                           |
+--------------+--------------+-----------------------------------------------------------------------------+				

Interfaces utilisateurs
~~~~~~~~~~~~~~~~~~~~~~~~

+--------------+--------------------------------------+-------------------------------------------+
| Adaptateurs  | Agents                               | Descriptions                              |
+--------------+--------------------------------------+-------------------------------------------+
| Adb          | adb                                  | Intégration avec la passerelle Android    |
+--------------+--------------------------------------+-------------------------------------------+
| Selenium     | selenium2-server ou selenium3-server | Intégration avec le projet Selenium       |
+--------------+--------------------------------------+-------------------------------------------+	
| Sikuli       | sikulix-server                       | Intégration avec le projet SikuliX        |
+--------------+--------------------------------------+-------------------------------------------+					

Bases de données
~~~~~~~~~~~~~~~~

+---------------+--------------+-----------------------------------------------------------------------------+
| Adaptateurs   | Agents       | Descriptions                                                                |
+---------------+--------------+-----------------------------------------------------------------------------+
| Microsoft SQL | database     | Communication avec une base de type Microsoft SQL                           |
+---------------+--------------+-----------------------------------------------------------------------------+
| MySQL         | database     | Communication avec une base de type MySQL/MariaDB                           |
+---------------+--------------+-----------------------------------------------------------------------------+	
| PostgreSQL    | database     | Communication avec une base de type PostgreSQL                              |
+---------------+--------------+-----------------------------------------------------------------------------+			

Contrôles systèmes	
~~~~~~~~~~~~~~~~~~~
+----------------+--------------+-----------------------------------------------------------------------------+
| Adaptateurs    | Agents       | Descriptions                                                                |
+----------------+--------------+-----------------------------------------------------------------------------+
| SSH/SFTP       | ssh          | Console SSH                                                                 |
+----------------+--------------+-----------------------------------------------------------------------------+
| TELNET         | socket       | Client permettant d'envoyer et recevoir du texte                            |
+----------------+--------------+-----------------------------------------------------------------------------+	
| FTP            | ftp          | Client avec support TLS                                                     |
+----------------+--------------+-----------------------------------------------------------------------------+	
| System File    | file         | Permet l'interaction avec les fichiers systèmes Linux ou Windows            |
+----------------+--------------+-----------------------------------------------------------------------------+	
| System Win/Unix| command      | Permet de contrôler les systèmes Linux et Windows (wmic)                    |
+----------------+--------------+-----------------------------------------------------------------------------+	
| Cisco Catalyst | ssh          | Client de configuration, basé sur l'adaptateur Telnet                       |
+----------------+--------------+-----------------------------------------------------------------------------+	

Protocoles Télécoms
~~~~~~~~~~~~~~~~~~~~~

+--------------+--------------+-----------------------------------------------------------------------------+
| Adaptateurs  | Agents       | Descriptions                                                                |
+--------------+--------------+-----------------------------------------------------------------------------+
| SMS Gateway  | gateway-sms  |  Permet de recevoir ou d'envoyer des SMS en utilisant un smartphone Android |
+--------------+--------------+-----------------------------------------------------------------------------+	
| SIP          | socket       |  Téléphone SIP                                                              |
+--------------+--------------+-----------------------------------------------------------------------------+
| RTP          | socket       |  Module permettant d'envoyer et recevoir des flux audios et vidéos          |
+--------------+--------------+-----------------------------------------------------------------------------+		

Librairies
----------

Une librairie permet de mettre à disposition rapidement des fonctions pour 
 - supporter les méthodes de chiffrement de données
 - supporter les formats de compression existants
 - supporter les fonctions d'authentification
 - manipuler les différents format de date, heure et unités
 - supporter les codecs (XML, JSON, etc...)
 - supporter les fonctions de hash de données

Une librairie ne communique pas en direct avec le système à tester ou piloter. Elle est utilisée:
 - directement depuis les tests
 - depuis les adaptateurs.

.. tip:: Si plusieurs adaptateurs ont besoin des mêmes fonctions, il est conseillé de les factoriser dans une librairie.

Liste des librairies disponibles par défauts:

Chiffrement
~~~~~~~~~~

+-----------+---------------------------------------+
|  AES      | Support chiffrement ou déchiffrement  |
+-----------+---------------------------------------+
|  Blowfish |  Support chiffrement ou déchiffrement |
+-----------+---------------------------------------+
|  OpenSSL  |  Permet d'exécuter la commande SSL    |
+-----------+---------------------------------------+
|  RC4      |  Support chiffrement ou déchiffrement |
+-----------+---------------------------------------+
|  XOR      |  Support chiffrement ou déchiffrement |
+-----------+---------------------------------------+
|  RSA      |  Générateur clé RSA                   |
+-----------+---------------------------------------+

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Libraries/02_Ciphers``

Codecs
~~~~~~

+--------------+-----------------------------------------------+
| Base64       |  Encode ou décode au format base64            |
+--------------+-----------------------------------------------+	
| Excel        |  Lecture de fichier excel                     |
+--------------+-----------------------------------------------+
| G711A        |  Encode ou décode le codec audio              |
+--------------+-----------------------------------------------+
| G711U        |  Encode ou décode le codec audio              |
+--------------+-----------------------------------------------+
| JSON         |  Encode ou décode du texte au format JSON     |
+--------------+-----------------------------------------------+
| XML          |  Encode ou décode du texte au format XML      |
+--------------+-----------------------------------------------+

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Libraries/03_Codecs``

Compression
~~~~~~~~~~

+--------+-------------------------------------------------+
| GZIP   | Compression ou décompression au format GZIP     |
+--------+-------------------------------------------------+	

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Libraries/09_Compression``
  
Hashing	
~~~~~~~~~~

+----------+------------------------------------------+
| Checksum | Générateur de checksum                   |
+----------+------------------------------------------+
| HMAC     | Création d'un hash md5, sha1 et sha256   |
+----------+------------------------------------------+
| MD5      | Création d'un hash md5                   |
+----------+------------------------------------------+
| SHA      | Création d'un hash sha1, sha256 et sha512|
+----------+------------------------------------------+
| CRC32    | Générateur de checksum                   |
+----------+------------------------------------------+

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Libraries/05_Hashing``
  
Identifiant
~~~~~~~~~~

+------------------+-------------------------------------------------------+
| SessionID        |  Générateur de session ID                             |
+------------------+-------------------------------------------------------+
| UUIDS            |  Générateur de UUID (Universally Unique IDentifier)   |
+------------------+-------------------------------------------------------+

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Libraries/07_Identifiers``
  
Média
~~~~~

+--------------+---------------------------------------------------------------+
| ChartsJS     |  Générateur de graphique visible dans les rapports de test    |
+--------------+---------------------------------------------------------------+
| DialTones    |  Générateur de tonalité                                       |
+--------------+---------------------------------------------------------------+
| Image        |  Manipulation des images                                      |
+--------------+---------------------------------------------------------------+
| Noise        |  Générateur de bruit                                          |
+--------------+---------------------------------------------------------------+
| SDP          |  Décode ou encode des messages SDP                            |
+--------------+---------------------------------------------------------------+
| WavContainer |  Création de fichier audio de type WAV                        |
+--------------+---------------------------------------------------------------+
| Waves        |  Générateur d'ondes simples                                   |
+--------------+---------------------------------------------------------------+

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Libraries/04_Media``

Date
~~~~

+------------------+---------------------------------------+
| Today            |   Permet de récupérer la date du jour |
+------------------+---------------------------------------+

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Libraries/11_Date``
  
Sécurité
~~~~~~~~~~

+-------------+------------------------------------------------------+
| Basic       |  Décode ou encode l'autorisation                     |
+-------------+------------------------------------------------------+
| Digest      |  Décode ou encode l'autorisation                     |
+-------------+------------------------------------------------------+
| Hmac        |  Décode ou encode l'autorisation                     |
+-------------+------------------------------------------------------+
| Oauth       |  Décode ou encode l'autorisation                     |
+-------------+------------------------------------------------------+
| Wsse        |  Décode ou encode l'autorisation                     |
+-------------+------------------------------------------------------+
| Certificate |  Décode les certificats dans un format lisible       |
+-------------+------------------------------------------------------+
| JWT         |  Décode ou encode des tokens                         |
+-------------+------------------------------------------------------+

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Libraries/01_Security``
  
Temps
~~~~~

+------------------+-------------------------------------------------------------------------+
| Timestamp        |  Permet de générer un timestamp ou de convertir en valeur lisible       |
+------------------+-------------------------------------------------------------------------+

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Libraries/06_Time``
  
Unités	
~~~~~~

+------------------+------------------------------------------------------------+
| Bytes            |  Permet de convertir des bytes en valeur lisibles          |
+------------------+------------------------------------------------------------+

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Libraries/08_Units``
  
Outils tiers
---------------

Le produit vient à la base avec un certain nombre de plugins pour s'interfacer avec 
d'autre d'outils existants (suivi de défauts, managements de tests, etc..).

Ces plugins peuvent être utilisés directement depuis un test.

Liste des outils supportés:

+------------------+------------------------------------------------------------+
| Git              |  Clone/commit de fichier sur un dépôt distant              |
+------------------+------------------------------------------------------------+
| Jira             |  Création de ticket                                        |
+------------------+------------------------------------------------------------+
| HP ALM QC        |  Exécution de test, création de ticket. Version 12 minimum |
+------------------+------------------------------------------------------------+
| ExtensiveTesting |  Exécution de test, création de variable                   |
+------------------+------------------------------------------------------------+
| Jenkins          |  Exécution de tests avant ou après un build                |
+------------------+------------------------------------------------------------+
| VSphere          | Création ou supression de machine virtuelle sur VMware     |
+------------------+------------------------------------------------------------+


.. note:: 
    La solution dispose d'une API REST, elle peut être pilotée aussi par ces outils.
     - Plugin ``Jenkins``: https://wiki.jenkins.io/display/JENKINS/ExtensiveTesting+Plugin

HP ALM
~~~~~~

Ce plugin permet d'exporter des résultats de tests dans l'outil HP ALM.
Il peut etre utilisé depuis un etst pour exporter des résultats sans intervention utilisateur.

Exemple d'utilisation:

::

    HP ALM ------> Appel REST API -----> ET 
    ^                                    |
    |                                    v
    |                             Exécution du test demandé
    |                                    v
    +<-------- Push du résultat ---------+
    
    
.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Interop/02_HP_QC``
  
Jenkins
~~~~~~

Ce plugin permet de lancer un build depuis la solution Extensive.

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Interop/06_Jenkins``
  
VSphere
~~~~~~

Ce plugin permet de piloter un environnement virtuel VMware. Il peut être utilisé pour:
 - créer des machines virtuelles en mode automatiquement
 - supprimer des machines

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Interop/05_VSphere``

ExtensiveTesting
~~~~~~~~~~~~~~~~

Ce plugin permet de faire un lien entre plusieurs environnement (dev, intégration, qualification) en permettant 
d'exécuter des tests d'un environnement à l'autre.

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Interop/03_ExtensiveTesting``

Jira
~~~~

Ce plugin permet de créer des tickets suite à l'exécution d'un test dans l'outil Jira.

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Interop/01_Jira``

Git
~~~~

Ce plugin permet de récupérer ou pousser des fichiers depuis un dépôt de sources.
Il peut être utilisé en prérequis d'un test.

.. note:: 
  Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Interop/04_Git``

Agents
------

Les agents sont disponibles depuis la boîte à outils. Il sont à utiliser conjointement avec les adaptateurs 
 - pour communiquer avec le système à tester ou piloter lorsque qu'il n'est pas accessible en direct par le serveur de test (ex: une page web)
 - exécuter un test sur plusieurs environnements différents.
 
.. note:: L'agent ``dummy`` est à utiliser comme base pour le développement d'un nouvel agent.

.. tip: Il est conseillé de limiter l'usage des agents car la mise en place des tests se retrouve plus complexe.


Protocoles réseaux
~~~~~~~~~~~~~~~~~~

+------------------+--------------------------------------------------------------------------------------+
| socket           |  Permet de démarrer des sockets TCP/UDP                                              |
+------------------+--------------------------------------------------------------------------------------+
| ftp              |  Permet de se connecter sur un serveur FTP(S)                                        |
+------------------+--------------------------------------------------------------------------------------+
| database         |  Permet de requêter les bases de données (MySQL, Microsoft SQL et PostgreSQL)        |
+------------------+--------------------------------------------------------------------------------------+
| ssh              |  Permet de se connecter sur des machines via SSH ou SFTP                             |
+------------------+--------------------------------------------------------------------------------------+

Systèmes
~~~~~~~

+------------------+--------------------------------------------------------------------------------------+
| command          |  Permet d'exécuter des commandes systèmes sur Windows ou Linux                       |
+------------------+--------------------------------------------------------------------------------------+
| file             |  Permet de récupérer des fichiers sur les systèmes Windows ou Linux                  |
+------------------+--------------------------------------------------------------------------------------+


Outils tiers
~~~~~~~~~~~~

+------------------+--------------------------------------------------------------------------------------+
| sikulix-server   |  Intéractions avec les applications lourdes                                          |
+------------------+--------------------------------------------------------------------------------------+
| selenium3-server |  Permet de piloter les navigateurs web dernières générations                         |
+------------------+--------------------------------------------------------------------------------------+
| selenium2-server |  Permet de piloter les navigateurs web                                               |
+------------------+--------------------------------------------------------------------------------------+
| soapui           |  Permet d'exécuter des tests SoapUI                                                  |
+------------------+--------------------------------------------------------------------------------------+
| adb              |  Permet de piloter les smartphones Android                                           |
+------------------+--------------------------------------------------------------------------------------+
| gateway-sms      |  Permet d'envoyer ou recevoir des SMS                                                |
+------------------+--------------------------------------------------------------------------------------+

.. note:: L'utilisation de l'agent ``Selenium3-Server`` nécessiste au minimum d'avoir ``Java 8`` sur le poste.


Sondes
------

Les sondes sont disponibles dans la boîte à outils. Le but principal est de récupérer 
automatiquement des logs (trace réseaux, fichiers) durant l'exécution d'un test.

+----------------+------------------------------------------------------------------------------------------+
| textual        |  Permet de faire suivre des fichiers de logs sur Windows ou Linux (tailf)                |
+----------------+------------------------------------------------------------------------------------------+
| network        |  Prise de traces réseaux, sonde basée sur tcpdump sur linux, ou tshark sur Windows       |
+----------------+------------------------------------------------------------------------------------------+
| file           |  Récupération de fichiers de configuration sur Windows ou Linux                          |
+----------------+------------------------------------------------------------------------------------------+

L'utilisation d'une sonde dans un test est à définir dans les propriétés.

 
.. note:: L'agent ``dummy`` est à utiliser comme base pour le développement d'un nouvel agent.
