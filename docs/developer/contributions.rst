Contributions
=============

Développement solution
----------------------

Client graphique
~~~~~~~~~~~~~~

**Environnement x64 win py3.6 qt5**

.. tip:: Environnement recommandé.

Pour préparer son environnement de développement, il est nécessaire de récupérer et d'installer les logiciels suivants:
 - Python 3.6.3 64bits
 - Git-2.15.0-64-bit.exe
 - TortoiseGit-2.5.0.0-64bit.msi
 - InnoSetup 5.5.9 – http://www.jrsoftware.org/isdl.php

D'ajouter les paquets Python supplémentaires avec la commande ``pip``

.. code-block:: bash

	> py -m pip install pyinstaller pylint
	> py -m pip install pyqt5
	> py -m pip install qscintilla
	
Et de récupérer les sources du client depuis le dépôt sur github.
	
.. code-block:: bash

	python Main.py
    
.. warning:: Windows XP n'est pas supporté dans ce mode.

**Environnement x64 win py3.4 qt4**

.. warning:: Cet environnement de développement n'est plus recommandé.

Pour préparer son environnement de développement, il est nécessaire de récupérer et installer les logiciels suivants:
 - Python 3.4.4 64bits
 - PyQt 4.11.4
 - Git-2.15.0-64-bit.exe
 - TortoiseGit-2.5.0.0-64bit.msi
 - InnoSetup 5.5.9 – http://www.jrsoftware.org/isdl.php

D'installer les paquets Python supplémentaires avec la commande ``pip``

.. code-block:: bash

	> C:\Windows\system32>py -3.4 -m pip install py2exe Cx_Freeze pyinstaller pylint
    

.. warning::
    Une modification est à effectuer dans la librairie py2exe.
    Editer le fichier `C:\Python34\Lib\site-packages\py2exe\icons.py`
    Rechercher la ligne `if iconheader.idCount` et modifier la valeur 10 par 14.

**Environnement x64 centos py2.7 qt4**

Préparation de son environnement de développement sur un système Linux CentOS 6 ou 7.

.. code-block:: bash

	yum install epel-release PyQt4 python-test
	yum install PyQt4-webkit qscintilla-python
	yum install python-pip
	yum install PyQt4-devel
	

.. code-block:: bash

	pip install dpkt
	pip install cx_freeze
	
Récupération des sources du client depuis le dépôt sur github.

.. code-block:: bash

	cd Scripts/qt4/
	bash MakeResources.sh
	Building files resources...
	bash MakeTranslations.sh
	Building translations resources...
	cd ../..
	

.. code-block:: bash

	python Main.py
    

**Environnement x64 ubuntu py3.5 qt5**

Préparation de son environnement de développement sur un système Linux Ubuntu 17.04

.. code-block:: bash

	sudo apt-get –y install python3-pyqt5
	sudo apt-get –y install python3-pyqt5.qsci
	sudo apt-get –y install python3-pyqt5.qtwebengine
	sudo apt-get –y install pyqt5-dev-tools
    

.. code-block:: bash

	sudo pip install dpkt
    
Récupérer les sources du client depuis le dépôt sur github.

.. code-block:: bash

	cd Scripts/qt5/
	chmod +x MakeResources.sh MakeTranslations.sh
	bash MakeResources.sh
	Building files resources...
	bash MakeTranslations.sh
	Building translations resources...
	cd ../..
	

.. code-block:: bash

	python3 Main.py
    

Boite à outils 
~~~~~~~~~~~~~~

**Environnement x64 win py3.6 qt5 (recommandé)**

Pour préparer son environnement de développement, il est nécessaire de récupérer et installer les logiciels suivants:
 - Python 3.6.3 64bits
 - Git-2.15.0-64-bit.exe
 - TortoiseGit-2.5.0.0-64bit.msi
 - InnoSetup 5.5.9 – http://www.jrsoftware.org/isdl.php

.. code-block:: bash

	> py -m pip install pyinstaller pylint
	> py -m pip install pyqt5
	> py -m pip install qscintilla
    
Installer les librairies utilisées par les différents agents:

.. code-block:: bash

	> py -3.6 -m pip install Cx_Freeze py2exe pyinstaller pylint
	> py -3.6 -m pip install requests PyMySQL psycopg2 paramiko 
	> py -3.6 -m pip install pymssql-2.1.3-cp36-cp36m-win_amd64.whl
    

Installer la librairie selenium dédié pour la solution:

.. code-block:: bash

	> c:\Python36\python.exe setup.py install
    
**Environnement x64 win py3.4 qt4**

Pour préparer son environnement de développement, il est nécessaire de récupérer et installer les logiciels suivants:
 - Python 3.4.4 64bits
 - PyQt 4.11.4
 - Git-2.15.0-64-bit.exe
 - TortoiseGit-2.5.0.0-64bit.msi
 - InnoSetup 5.5.9 – http://www.jrsoftware.org/isdl.php
    
Installer les librairies utilisées par les différents agents:

.. code-block:: bash

    > py -3.4 -m pip install Cx_Freeze py2exe pylint
	> py -3.4 -m pip install requests PyMySQL psycopg2 pymssql paramiko 
    

Installer la librairie selenium dédiée pour la solution:

.. code-block:: bash

	> c:\Python34\python.exe setup.py install
    
**Environnement x64 centos py3.5 qt5**

Préparation de son environnement de développement sur un système Linux CentOS 6 ou 7.

Installer la librairie Qt5 (binding python)

.. code-block:: bash

	sudo apt-get –y install python3-pyqt5
	sudo apt-get –y install pyqt5-dev-tools
	cd Scripts/qt5/
	chmod +x MakeResources.sh MakeTranslations.sh
	bash MakeResources.sh
	Building files resources...
	bash MakeTranslations.sh
	Building translations resources...
	cd ../..
	

Installer les librairies additionnelles 

.. code-block:: bash

	sudo apt install python3-pip
	pip3 install pyinstaller py2exe pylint
	pip3 install paramiko requests
	pip3 install PyMySQL psycopg2
	pip3 install pymssql
	unzip selenium-3.7.0-extensivetesting.zip
	cd selenium-3.7.0/
	sudo python3 setup.py install
	
Récupérer les sources du client depuis le dépôt sur github.
	
Exécution de la boite à outils en mode graphique

.. code-block:: bash

	python3 Systray.py
    

**Environnement x64 centos py2.7 qt4**

Préparation de son environnement de développement sur un système Linux CentOS 6 ou 7.

Installer les librairies additionnelles 

.. code-block:: bash

	yum install python-test
	yum install python-pip
	pip install pyinstaller py2exe pylint
	pip install paramiko requests
	pip install PyMySQL psycopg2
	pip install pymssql
	unzip selenium-3.7.0-extensivetesting.zip
	cd selenium-3.7.0/
	python setup.py install
	

Installer la librairie Qt4 (binding python)

.. code-block:: bash

	yum install epel-release PyQt4
	yum install PyQt4-devel
	cd Scripts/qt4/
	chmod +x MakeResources.sh MakeTranslations.sh
	bash MakeResources.sh
	Building files resources...
	bash MakeTranslations.sh
	Building translations resources...
	cd ../..
	
Récupérer les sources du client depuis le dépôt sur github.
	
Exécution de la boite à outil en mode graphique

.. code-block:: bash

	python Systray.py
	

Serveur 
~~~~~~~

**Environnement x64 centos py2.7**

Préparation de son environnement de développement sur un système Linux CentOS 6.5 et plus.

Installation des paquets systèmes

.. code-block:: bash
  
  vim 
  net-snmp-utils
  unzip
  zip
  gmp
  wget
  curl
  ntp
  nmap
  bind-utils
  postfix
  dos2unix
  openssl
  openssl-devel
  tcpdump
  mlocate
  mariadb-server
  mariadb
  mariadb-devel
  httpd
  mod_ssl
  php
  php-mysql
  php-gd
  php-pear
  python-lxml
  MySQL-python
  policycoreutils-python
  python-setuptools
  python-ldap
  gcc
  python-devel
  Cython
  java
  git
  libffi-devel
  libpng-devel
  libjpeg-devel
  zlib-devel
  freetype-devel
  lcms-devel
  tk-devel
  tkinter
  postgresql
  postgresql-libs
  postgresql-devel
  

Installation des librairies python

.. code-block:: bash
  
  six
  appdirs
  pyparsing
  packaging
  setuptools
  httplib2
  uuidlib
  pycrypto
  pyasn
  ply
  pysmi
  pysnmp
  freetds
  setuptools_git
  pymssql
  ecdsa
  pil
  selenium
  suds
  requests
  ntlm
  kerberos
  postgresql
  xlrd
  etxmlfile
  jdcal
  openxl
  libpqxx
  scandir
  pycnic
  xlwt
  isodate
  xml2dict
  setuptools_scm
  pytest
  wcwidth
  pyte
  pysphere
  pychef
  idna
  enum34
  ipaddress
  pycparser
  cffi
  orderddict
  ntlm_auth
  requests_ntlm
  py_ntlm3
  pywinrm
  asn1crypto
  cryptography
  paramiko
  jsonpath
  wrapt
  pbr
  pytz
  pyjenkins
  snmap2
  gitdb2
  pygit
  

Développement plugins
----------------------

Adaptateur
~~~~~~~~~~

L'ajout d'une adaptateur s'effectue en utilisant le client graphique.
Il faut aller dans le dépôt ``Modules Listing > Adapters`` et faire un clic droit sur l'arborescence pour ajouter un adaptateur.

.. image:: /_static/images/client/client_adapters.png

Pour mettre à disposition l'adaptateur pour les tests, il faut éditer le fichier ``__init__.py`` et ajouter les lignes 
suivantes:

.. code-block:: python
  
  import Example
  __HELPER__.append("Example") 
  
Pour faire apparaitre l'adaptateur dans la documentation accessible depuis le client graphique, il faut 
utiliser le décorateur ``@doc_public`` devant les fonctions que l'on souhaite documenter.

.. code-block:: python
  
  class Example(TestAdapterLib.Adapter):
    @doc_public
	def __init__(self, parent)
    
    @doc_public
    def connect(self, timeout=5.0):
  

.. tip:: L'adaptateur ``Dummy`` est à utiliser comme base de développement.

Librairie
~~~~~~~~~

L'ajout d'une librairie s'effectue en utilisant le client graphique.
Il faut aller dans le dépôt `Modules Listing > Libraries` et faire un clic droit sur l'arborescence pour ajouter une librairie.

.. image:: /_static/images/client/client_libraries.png

Pour mettre à disposition la librairie pour les tests, il faut éditer le fichier ``__init__.py`` et ajouter les lignes 
suivantes:

.. code-block:: python
  
  import Example
  __HELPER__.append("Example") 
  
Pour faire apparaitre la librairie dans la documentation accessible depuis le client graphique, il faut 
utiliser le décorateur ``@doc_public`` devant les fonctions que l'on souhaite documenter.

.. code-block:: python
  
  class Example(TestLibraryLib.Library):
    @doc_public
	def __init__(self, parent)
    
    @doc_public
    def connect(self, timeout=5.0):
  

.. tip:: La librairie ``Dummy`` est à utiliser comme base de développement.

SDK Boite à outils
~~~~~~~~~~~~~~

**Environnement Linux**

.. tip:: Il est conseillé d'utiliser le plugin ``dummy`` comme base de développement de votre agent ou sonde.

En utilisant comme base l'agent ou la sonde ``dummy``, il faut ensuite :
 - mettre à jour la variable ``__TYPE__`` pour indiquer le nom de l'agent ou la sonde
 - changer le nom de la classe avec le nom de votre agent ou sonde. 
 - mettre à jour le fichier ``__init__`` pour importer votre agent ou sonde.

**Environnement Windows**

Le SDK pour la création de plugin se récupère depuis github.
Il est possible de copier le plugin ``Dummy`` et de l'utiliser comme base.

Le type et le nom du plugin est à configurer dans le fichier `config.json`

.. code-block:: json
  
  {
    "plugin": {
                "name": "MyExample", 
                "version": "1.0.0" 
                }
  }
  
L'auteur se définit dans le fichier ``MyPlugin.py``.

.. code-block:: python
  
  # name of the main developer
  __AUTHOR__ = 'Denis Machard'
  # email of the main developer
  __EMAIL__ = 'd.machard@gmail.com'
  
La construction du plugin en binaire s'effectue en appelant le script ``MakeExe3.bat``.

.. tip: 
  Il est possible d'exécuter le plugin sans le client en activant le mode debug.
  
  .. code-block: bash
      
    # debug mode
    DEBUGMODE=True

SDK Client
~~~~~~~~~~~~

Le client supporte l'ajout de plugins. La création d'un plugin nécessite:
 - d'utiliser le SDK
 - de définir son type 
 
Liste des types de plugins possibles:

+-------------------+------------------------------------------------------------+
|Type               |   Description                                              |
+-------------------+------------------------------------------------------------+
|basic              |   Plugin pour ajouter un raccourci sur la page d'accueil   |
+-------------------+------------------------------------------------------------+
|recorder-app       |   Export/import de données dans l'assistant de conception  |
+-------------------+------------------------------------------------------------+
|recorder-web       |   Export/import de données dans l'assistant de conception  |
+-------------------+------------------------------------------------------------+
|recorder-framework |   Export/import de données dans l'assistant de conception  |
+-------------------+------------------------------------------------------------+
|recorder-android   |   Export/import de données dans l'assistant de conception  |
+-------------------+------------------------------------------------------------+
|recorder-system    |   Export/import de données dans l'assistant de conception  |
+-------------------+------------------------------------------------------------+
|remote-tests       |   Export/import de données dans les tests distants         |
+-------------------+------------------------------------------------------------+
|test-results       |   Export des résultats de tests et rapports                |
+-------------------+------------------------------------------------------------+

Le SDK pour la création de plugin se récupère depuis github.
Il est possible de copier le plugin ``Dummy`` et de l'utiliser comme base de développement.

Le type et le nom du plugin est à configurer dans le fichier ``config.json``

.. code-block:: json
  
  {
    "plugin": {
                "name": "MyExample", 
                "type": "recorder-app", 
                "version": "1.0.0" 
                }
  }
  
L'auteur se définit dans le fichier ``MyPlugin.py``.

.. code-block:: python
  
  # name of the main developer
  __AUTHOR__ = 'Denis Machard'
  # email of the main developer
  __EMAIL__ = 'd.machard@gmail.com'
  
La construction du plugin en binaire s'effectue en appelant le script ``MakeExe3.bat``.

L'échange de donnée entre le plugin et le client s'effectue avec des messages de type ``JSON``.

  1. Envoie de donnée au client:

     .. code-block:: python
        
        self.core().sendMessage( cmd='import', data = {"my message": "hello"} )
  
  2. Réception des données depuis le client:

     .. code-block:: python
        
        class MainPage(QWidget):
           def insertData(self, data):
           
Pour faciliter le troubleshooting, il est possible d'ajouter des traces depuis le plugin.

 1. Ajouter des traces dans la fenêtre graphique dédiée:

  .. code-block:: python
    
    self.core().debug().addLogWarning("my warning message")
    self.core().debug().addLogError( "my error message")
    self.core().debug().addLogSuccess("my success message" )
    

 2. Ajouter des traces dans les fichiers de logs:

  .. code-block:: python

    Logger.instance().debug("my debug message")
    Logger.instance().error("my error message")
    Logger.instance().info("my info message")
  

.. tip::
  Il est possible d'exécuter le plugin sans le client en activant le mode debug.
  
  .. code-block: bash
      
    # debug mode
    DEBUGMODE=True

Documentations
--------------

La documentation est stockée sur github dans le `dépôt <https://github.com/ExtensiveTesting/extensivetesting-fr.readthedocs.io>`_.
Il est possible de contribuer en faisant une demande de participation au dépôt.

La documentation est générée par le service `readthedocs <https://readthedocs.org/>`_.