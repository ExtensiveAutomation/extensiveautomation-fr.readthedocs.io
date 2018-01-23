Contributions
=============

Développement solution
----------------------

Client - x64 win py3.6 qt5 (recommandé)
~~~~~~~~~~~~~~~~~~~~~~~~~~

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
	

.. note:: Windows XP n'est pas supporté dans ce mode.

Client - x64 win py3.4 qt4
~~~~~~~~~~~~~~~~~~~~~~~~~~

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

Client - x64 centos py2.7 qt4
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Préparation de son environnement de développement sur un système Linux CentOS 6 ou 7.

.. code-block:: bash

	yum install epel-release PyQt4 python-test
	yum install PyQt4-webkit qscintilla-python
	yum install python-pip
	yum install PyQt4-devel
	

.. code-block:: bash

	pip install dpkt
	pip install cx_freeze
	

.. code-block:: bash

	cd Scripts/qt4/
	bash MakeResources.sh
	Building files resources...
	bash MakeTranslations.sh
	Building translations resources...
	cd ../..
	

.. code-block:: bash

	python Main.py
    

Client - x64 ubuntu py3.5 qt5
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Préparation de son environnement de développement sur un système Linux Ubuntu 17.04

.. code-block:: bash

	sudo apt-get –y install python3-pyqt5
	sudo apt-get –y install python3-pyqt5.qsci
	sudo apt-get –y install python3-pyqt5.qtwebengine
	sudo apt-get –y install pyqt5-dev-tools
    

.. code-block:: bash

	sudo pip install dpkt
    

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
    

Boite à outils - x64 win py3.6 qt5 (recommandé)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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
    
Boite à outils - x64 win py3.4 qt4
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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
    
Boite à outils - x64 centos py3.5 qt5
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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
	

Exécution de la boite à outils en mode graphique

.. code-block:: bash

	python3 Systray.py
    

Boite à outils - x64 centos py2.7 qt4
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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
	

Exécution de la boite à outil en mode graphique

.. code-block:: bash

	python Systray.py
	

Serveur - x64 centos py2.7
~~~~~~~~~~~~~~~~~~~~~~~~~~

Développement plugins
----------------------

Adaptateur
~~~~~~~~~~

Librairie
~~~~~~~~~

Boite à outils
~~~~~~~~~~~~~~

Client
~~~~~~

Documentations
--------------