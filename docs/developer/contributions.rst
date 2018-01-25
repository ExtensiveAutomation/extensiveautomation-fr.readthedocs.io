Contributions
=============

Développement solution
----------------------

Client
~~~~~~

**Environnement x64 win py3.6 qt5 (recommandé)**

Pour préparer son environnement de développement, il est nécessaire de récupérer et installer les logiciels suivants:
 - Python 3.6.3 64bits
 - Git-2.15.0-64-bit.exe
 - TortoiseGit-2.5.0.0-64bit.msi
 - InnoSetup 5.5.9 – http://www.jrsoftware.org/isdl.php

Il est nécessaire d'installer les paquets Python supplémentaire avec la commande `pip`

.. code-block:: bash

	> py -m pip install pyinstaller pylint
	> py -m pip install pyqt5
	> py -m pip install qscintilla
	
Récupérer les sources du client depuis le dépôt sur github.
	
.. code-block:: bash

	python Main.py
    
.. note:: Windows XP n'est pas supporté dans ce mode.

**Environnement x64 win py3.4 qt4**

Pour préparer son environnement de développement, il est nécessaire de récupérer et installer les logiciels suivants:
 - Python 3.4.4 64bits
 - PyQt 4.11.4
 - Git-2.15.0-64-bit.exe
 - TortoiseGit-2.5.0.0-64bit.msi
 - InnoSetup 5.5.9 – http://www.jrsoftware.org/isdl.php

Il est nécessaire d'installer les paquets Python supplémentaires avec la commande `pip`

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
	
Récupérer les sources du client depuis le dépôt sur github.

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
    

Installer la librairie selenium dédié pour la solution:

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


Développement plugins
----------------------

Adaptateur
~~~~~~~~~~

Create a new package of adapters
From the client, go the adapter repository Modules Listing > Adapters

Select the set to adapters where you want to add a new adapter.



Right click on it and click on the menu Add Adapter . Set the name of your adapter with the value Example.



Generate the adapter’s package by clicking on OK, the package will appears on the tree with a init default file



Edit the init file of the set of adapters.



Reach the end of the file and add the following lines. Change the name of the import with the name of your adapter. This two lines are necessary to enable the automatic generation of the online documentations.

import Example
__HELPER__.append("Example") 
Add an adapter
From the workspace, click on the button  to add a adapter. A adapter is provided by default named MyAdapter.
The Python language is used to develop adapter.

```python
class MyAdapter(TestAdapter.Adapter):
```
Got the end of the file and add the following function to your adapter:

def hello(self):
    """
    Log a hello world message
    """
    self.warning("hello world")
Save the file with the name myexample. Choose the folder created previously as destination.



Edit the file init and add the following line on the beginning, after the header.

from client import *
Save your file.

Create the online documentation
Edit the init file of your adapter’s package

Configure the variable __DESCRIPTION__ to add a description

__DESCRIPTION__ = "Description of my first adapter"
Configure the variable __HELPER__ as below, this variable enables to list functions to add on the assistant.

__HELPER__ =    [
                    ("MyAdapter", ["__init__", "hello"])
                ]
Save the change.

Finally, click on the following button

.

After the generation, your adapter will appears on the list like below



Test your adapter
Create a basic test unit  and try to import your new adapter as below:

Initialize the adapter in the prepare section

def prepare(self):
    self.ADP_EXAMPLE = SutAdapters.Example.MyAdapter(parent=self, debug=input('DEBUG'))
Call the function hello of the adapter in the definition section as below:

def definition(self):
    self.ADP_EXAMPLE.hello()
Run the test, the hello message should appears.



Librairie
~~~~~~~~~

Create a new package of libraries
From the client, go the library repository Modules Listing > Libraries

Select the set to libraries where you want to add a new library.



Right click on it and click on the menu Add Library . Set the name of your library with the value Example.



Generate the library’s package by clicking on OK, the package will appears on the tree with a init default file



Edit the init file of the set of libraries.



Reach the end of the file and add the following lines. Change the name of the import with the name of your library. This two lines are necessary to enable the automatic generation of the online documentations.

import Example
__HELPER__.append("Example")
Add an library
From the workspace, click on the button  to add a MyLibrary. A MyLibrary is provided by default named MyLibrary.
The Python language is used to develop MyLibrary.

```python
class MyLibrary(TestLibrary.Library):
```
Got the end of the file and add the following function to your MyLibrary:

def hello(self):
    """
    Log a hello world message
    """
    self.warning("hello world")
Save the file with the name myexample. Choose the folder created previously as destination.



Edit the file init and add the following line on the beginning, after the header.

from client import *
Save your file.

Create the online documentation
Edit the init file of your MyLibrary’s package

Configure the variable __DESCRIPTION__ to add a description

__DESCRIPTION__ = "Description of my first MyLibrary"
Configure the variable __HELPER__ as below, this variable enables to list functions to add on the assistant.

__HELPER__ =    [
                    ("MyLibrary", ["__init__", "hello"])
                ]
Save the change.

Finally, click on the following button

.

After the generation, your library will appears on the list like below



Test your library
Create a basic test unit  and try to import your new library as below:

Initialize the library in the prepare section

def prepare(self):
    self.LIB_EXAMPLE = SutLibraries.Example.MyLibrary(parent=self, debug=input('DEBUG'))
Call the function hello of the library in the definition section as below:

def definition(self):
    self.LIB_EXAMPLE.hello()
Run the test, the hello message should appears.



SDK Boite à outils
~~~~~~~~~~~~~~

Prepare sources
Retrieve the Toolbox for Linux and deploy-it on a dedicaded machine. Follow the installation guide

Check to start a dummy agent

./toolagent <test_server_ip> <test_server_port> True dummy "agent.test" "my first agent"
Go to the the web interface Overview > Agents to check if the agent is running properly.

Add a new embedded agent
Go to the folder ./Embedded/ and copy the dummy agent

cp DummyAgent.py MyAgent.py
Edit the new file and change the type of your agent according to your need.

__TYPE__="""myagent"""
Update the name of the class Dummy by the name of your agent and also the initialize function.

class MyAgent(GenericTool.Tool):
def initialize (controllerIp, ......):
    """
    Wrapper to initialize the object agent
    """
    return MyAgent(....
Save all changes in the file

Finally, declare this new agent in the Python __init__ file, add the following line:

from Embedded import MyAgent
After that, your agent must appear on the documentation of the ./toolagent script

Test your agent
Start your agent as below:

./toolagent <test_server_ip> <test_server_port> True myagent "agent.test" "my first agent"
Check on the web interface Overview > Agents if the agent appears on the list

For Windows
Prerequisites
Prepare sources
Configure your plugin
Build and test the plugin
Prerequisites
Prepare your environment, install the following packages:

Python 3.4 32bits or 64bits
PyQT4 or 5
cx_Freeze
Prepare sources
Retrieve plugins from the remote git

Copy the folder dummy to the folder myexample

Go to the folder Scripts in your plugin folder and execute the powershell script CodePrepare.ps1. This script retrieves automatically the generic module.

Finally, edit the file MyPlugin.py and change the key DEBUG to True,

# debug mode
DEBUGMODE=True
Activate the debug mode to run the plugin without the client.

Configure your plugin
Edit the file config.json and configure your plugin

{
    "plugin": {
                "name": "MyExample", 
                "version": "1.0.0" 
                }
}
Edit the file MyPlugin.py and update the following keys

# name of the main developer
__AUTHOR__ = 'Denis Machard'
# email of the main developer
__EMAIL__ = 'd.machard@gmail.com'
Build and test the plugin
Execute the file MakeExe3.bat in the Scripts folder. This file will automatically create a binary.

Deploy the output on the client plugins folder. Read the installation guide.

SDK Client
~~~~~~~~~~~~

Le client supporte l'ajout de plugins. La création d'un plugin nécessite de définir:
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

La récupération du SDK pour la création de plugin se récupère depuis github
Il est possible de copier le plugin `Dummy` et l'utiliser comme base.

Le type et le nom du plugin est à configurer dans le fichier `config.json`

.. code-block:: json
  
  {
    "plugin": {
                "name": "MyExample", 
                "type": "recorder-app", 
                "version": "1.0.0" 
                }
  }
  

.. tip: 
  Il est possible d'exécuter le plugin sans le client en activant le mode debug.
  
  .. code-block: bash
      
    # debug mode
    DEBUGMODE=True

Configure your plugin
Edit the file config.json and configure your plugin:

Define the type
Define the name
Define the version

Edit the file MyPlugin.py and update the following keys:

# name of the main developer
__AUTHOR__ = 'Denis Machard'
# email of the main developer
__EMAIL__ = 'd.machard@gmail.com'
Build and test the plugin
Execute the file MakeExe3.bat in the Scripts folder. This file will automatically create a binary.

Deploy the output on the client plugins folder. Read the installation guide.

Communicate with the client
To receive data from the client, overwrite the function insertData lf the Main widget. The type of the data argument is json.
class MainPage(QWidget):
    def insertData(self, data):
To send data to the client, use the sendMessage function
self.core().sendMessage( cmd='import', data = {"my message": "hello"} )
Read or write configuration
If you need to store some settings, the config.json file can be used to do that.

**Fonctions de logs**

Ajout de traces dans la fenêtre graphique dédiée

.. code-block:: python

    self.core().debug().addLogWarning("my warning message")
    self.core().debug().addLogError( "my error message")
    self.core().debug().addLogSuccess("my success message" )
    

Ajout de traces dans les logs:

.. code-block:: python

    Logger.instance().debug("my debug message")
    Logger.instance().error("my error message")
    Logger.instance().info("my info message")
    

Documentations
--------------

La documentation est stockée sur github dans le dépôt https://github.com/ExtensiveTesting/extensivetesting-fr.readthedocs.io
Il est possible de contribuer en faisant une demande de participation au dépôt.

La documentation est générée par le service `readthedocs`.