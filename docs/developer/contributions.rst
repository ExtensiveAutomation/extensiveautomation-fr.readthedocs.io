Contributions
=============

Développement solution
----------------------

Client x64 Windows - Python 3.6 et Qt5
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Pour préparer son environnement de développement, il est nécessaire de récupérer et installer les logiciels suivants:
 - Python 3.6.3 64bits
 - Git-2.15.0-64-bit.exe
 - TortoiseGit-2.5.0.0-64bit.msi
 - InnoSetup 5.5.9 – http://www.jrsoftware.org/isdl.php

Il est nécessaire d'installer les paquets Python supplémentaire avec la commande `pip`

.. code-block::

    > py -m pip install pyinstaller pylint
    > py -m pip install pyqt5
    > py -m pip install qscintilla
    
.. note:: Windows XP n'est pas supporté dans ce mode.

Client x64 Windows - Python 3.4 et Qt4
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Pour préparer son environnement de développement, il est nécessaire de récupérer et installer les logiciels suivants:
 - Python 3.4.4 64bits
 - PyQt 4.11.4
 - Git-2.15.0-64-bit.exe
 - TortoiseGit-2.5.0.0-64bit.msi
 - InnoSetup 5.5.9 – http://www.jrsoftware.org/isdl.php

Il est nécessaire d'installer les paquets Python supplémentaire avec la commande `pip`

.. code-block::

    > C:\Windows\system32>py -3.4 -m pip install py2exe Cx_Freeze pyinstaller pylint
    
.. warning::
    Une modification est à effectuer dans la librairie py2exe.
    Editer le fichier `C:\Python34\Lib\site-packages\py2exe\icons.py`
    Rechercher la ligne `if iconheader.idCount` et modifier la valeur 10 par 14.

Client x64 Linux Centos - Python 2.7 et Qt4
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Préparation de son environnement de développement sur un système Linux CentOS 6 ou 7.

.. code-block::
    yum install epel-release PyQt4 python-test
    yum install PyQt4-webkit qscintilla-python
    yum install python-pip
    yum install PyQt4-devel
    
.. code-block::

    pip install dpkt
    pip install cx_freeze
    

.. code-block::

    cd Scripts/qt4/
    bash MakeResources.sh
    Building files resources...
    bash MakeTranslations.sh
    Building translations resources...
    cd ../..
    

.. code-block::

    python Main.py
    

Client x64 Linux Ubuntu - Python 3.5 et Qt5
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Préparation de son environnement de développement sur un système Linux Ubuntu 17.04

.. code-block::

    sudo apt-get –y install python3-pyqt5
    sudo apt-get –y install python3-pyqt5.qsci
    sudo apt-get –y install python3-pyqt5.qtwebengine
    sudo apt-get –y install pyqt5-dev-tools
    

.. code-block::

    Install additionnals libraries
    sudo pip install dpkt
    

.. code-block::

    cd Scripts/qt5/
    chmod +x MakeResources.sh MakeTranslations.sh
    bash MakeResources.sh
    Building files resources...
    bash MakeTranslations.sh
    Building translations resources...
    cd ../..
    

.. code-block::

    python3 Main.py
    

Boite à outils
~~~~~~~~~~~~~~

Toolbox development x64 for Windows (python 3.6 64bits and PyQt5)
Python - https://www.python.org/ftp/python/3.6.3/ – version 3.6.3 – 64 bits

PyQT – https://www.riverbankcomputing.com/software/pyqt/download5 – version 5.9.1 – 64 bits

Install external python libraries

> py -3.6 -m pip install Cx_Freeze py2exe pyinstaller pylint
> py -3.6 -m pip install requests PyMySQL psycopg2 paramiko 
> py -3.6 -m pip install pymssql-2.1.3-cp36-cp36m-win_amd64.whl
Install selenium-3.7.0-extensivetesting python library

> c:\Python36\python.exe setup.py install
Toolbox development x64 for Windows (python 3.4 64bits and PyQt4)
If you want to run the toolbox directly from the source code, please to install the following prerequesites:

Python - https://www.python.org/downloads/release/python-344/ – version 3.4.4 – 64 bits

Install external python libraries

> py -3.4 -m pip install Cx_Freeze py2exe pylint
py -3.4 -m pip install requests PyMySQL psycopg2 pymssql paramiko 
Install selenium-3.7.0-extensivetesting python library

> c:\Python34\python.exe setup.py install
Toolbox development x64 on Centos 6 or 7 (python2.7 and PyQt4)
If you want to run the toolbox directly from the source code, please to install the following prerequesites: The toolbox must be executed with python > 2.5 and PyQt4.

Install PyQt4
yum install epel-release PyQt4
yum install PyQt4-devel
Install python libraries
yum install python-test
yum install python-pip
pip install pyinstaller py2exe pylint
pip install paramiko requests
pip install PyMySQL psycopg2
pip install pymssql
unzip selenium-3.7.0-extensivetesting.zip
cd selenium-3.7.0/
python setup.py install
Make resources for PyQt4
cd Scripts/qt4/
chmod +x MakeResources.sh MakeTranslations.sh
bash MakeResources.sh
Building files resources...
bash MakeTranslations.sh
Building translations resources...
cd ../..
Run the toolbox
python Systray.py
Toolbox development x64 on Ubuntu (python3.5 and PyQt5)
If you want to run the toolbox directly from the source code, please to install the following prerequesites: The toolbox must be executed with python > 3.x and PyQt5.

Install PyQt5
sudo apt-get –y install python3-pyqt5
sudo apt-get –y install pyqt5-dev-tools
Install python libraries
sudo apt install python3-pip
pip3 install pyinstaller py2exe pylint
pip3 install paramiko requests
pip3 install PyMySQL psycopg2
pip3 install pymssql
unzip selenium-3.7.0-extensivetesting.zip
cd selenium-3.7.0/
sudo python3 setup.py install
Make resources for PyQt5
cd Scripts/qt5/
chmod +x MakeResources.sh MakeTranslations.sh
bash MakeResources.sh
Building files resources...
bash MakeTranslations.sh
Building translations resources...
cd ../..
Run the toolbox
python3 Systray.py

Serveur
~~~~~~

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