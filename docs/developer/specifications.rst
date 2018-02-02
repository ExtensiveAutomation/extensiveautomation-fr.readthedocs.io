Spécifications
=============

Cycle des versions
-------------------

L'ensemble des paquets logiciels de la solution respecte les rêgles suivantes pour le nommage des versions.

La version se découpe en 3 chiffres (A.B.C)
 - A: le 1er chiffre indique la version majeure. L'incrémentation de ce chiffre implique 
    - l'ajout de fonctionnalités majeures (avec pottentiellement une perte de compatibilité avec la version précédente)
    - l'ajout de fonctionnalités mineures
    - la correction de bug
 - B: Le 2ième chiffre indique une version mineure. L'incrémentation de ce chiffre indique
    - l'ajout de fonctionnalités mineures
    - la correction de bug
 - C: le 3ième chiffre indique une version de maintenance. L'incrémentation de ce chiffre indique
    - la correction de bug

Arborescence du serveur
-------------------

L'ensemble des fichiers manipulés par le serveur sont stockés dans le répertoire ``/opt/xtc/current/``.

::
  
  Core/
  Libs/
  Scripts/
  Packages/
  TestExecutorLib/
  TestInterop/
  SutAdapters/
  SutLibraries/
  Var/
    Tests/
    TestsResults/
    Logs/
    Backups/
  Web/
  

Les tests sont stockés dans le répertoire ``/opt/xtc/current/Var/Tests/``, ils sont organisés par identifiant de projet.

Modèle de données
-------------------

Une base de donnée est utilisée par le serveur pour stocker :
 - les utilisateurs de la solution
 - la liste des projets
 - les données de tests (variables projets)
 - des statistiques
 - l'historique des exécutions

+-------------------------+-----------------------------------------------+
|  Tables                 |    Description                                |
+-------------------------+-----------------------------------------------+
|  xtc-agents             | Non utilisé                                   |
+-------------------------+-----------------------------------------------+
|  xtc-agents-stats       | Non utilisé                                   |
+-------------------------+-----------------------------------------------+
|  xtc-probes             | Non utilisé                                   |
+-------------------------+-----------------------------------------------+
|  xtc-probes-stats       | Non utilisé                                   |
+-------------------------+-----------------------------------------------+
|  xtc-config             | Configuration du serveur                      |
+-------------------------+-----------------------------------------------+
|  xtc-projects           | Liste des projets                             |
+-------------------------+-----------------------------------------------+
|  xtc-relations-projects | Relation entre les projets et les utilisateurs|
+-------------------------+-----------------------------------------------+
|  xtc-users              | Liste des utilisateurs                        |
+-------------------------+-----------------------------------------------+
|  xtc-users-stats        | Statistiques de connexions                    |
+-------------------------+-----------------------------------------------+
|  xtc-test-environment   | Liste des variables au format JSON            |
+-------------------------+-----------------------------------------------+
|  xtc-tasks-history      | Historique des tâches exécutées sur le serveur|
+-------------------------+-----------------------------------------------+
|  xtc-scripts-stats      | Statistiques sur les tests exécutés           |
+-------------------------+-----------------------------------------------+
|  xtc-testabstracts-stats| Statistiques sur les tests exécutés           |
+-------------------------+-----------------------------------------------+
|  xtc-testcases-stats    | Statistiques sur les tests exécutés           |
+-------------------------+-----------------------------------------------+
|  xtc-testsuites-stats   | Statistiques sur les tests exécutés           |
+-------------------------+-----------------------------------------------+
|  xtc-testunits-stats    | Statistiques sur les tests exécutés           |
+-------------------------+-----------------------------------------------+
|  xtc-testplans-stats    | Statistiques sur les tests exécutés           |
+-------------------------+-----------------------------------------------+
|  xtc-testglobals-stats  | Statistiques sur les tests exécutés           |
+-------------------------+-----------------------------------------------+
|  xtc-writing-stats      | Statistiques sur la durée d'écriture des tests|
+-------------------------+-----------------------------------------------+


Gestion des mots de passes
-------------------

Aucun mot de passe (en clair) est stocké dans la base de donnée. L'utilisation d'un hash est par contre utilisé.
Le hash du mot de passe est stocké dans la table `xtc-users`.

L'algorithme utilisé:

.. code-block::
  
  hash_password = SHA1 ( SALT + SHA1(user_password) )
  

.. image:: /_static/images/server/server_table_pwd.png

Format des fichiers
-------------------

Les tests sont au format ``XML`` zippés. Il existe plusieurs formats de tests:
 - Test Abstract Xml
 - Test Unit Xml
 - Test Suite Xml
 - Test Plan Xml
 - Test Global Xml

**Structure XML partagée**

.. code-block:: xml

    <?xml version="1.0" encoding="utf-8" ?>
    <file>
        <properties>
            <descriptions>...</descriptions>
            <inputs-parameters>...</inputs-parameters>
            <outputs-parameters>...</ outputs -parameters>
        </properties>
    </file>

**Test Abstract Xml**

.. code-block:: xml

    <?xml version="1.0" encoding="utf-8" ?>
    <file>
        <properties>...</properties>
        <teststeps>
            <steps>
                <step>
                    <id>1</id>
                    <description>
                        <type>string</type>
                        <value>step description</value>
                    </description>
                    <summary>
                        <type>string</type>
                        <value>step sample</value>
                    </summary>
                    <expected>
                        <type>string</type>
                        <value>result expected</value>
                    </expected>
                </step>
            </steps>
        </teststeps>
        <testadapters><adapters /></testadapters>
        <testlibraries><libraries /></testlibraries>
        <testactions>
            <actions>
                <action>
                    <item-id>1</item-id>
                    <item-text>Start</item-text>
                    <item-type>2</item-type>
                    <item-data />
                    <pos-y>1750.0</pos-y>
                    <pos-x>2000.0</pos-x>
                </action>
            </actions>
        </testactions>
        <testaborted><aborted /></testaborted>
        <testdefinition><![CDATA[pass]]></testdefinition>
        <testdevelopment>1448190709.095677</testdevelopment>
    </file>
    

**Test Unit Xml**

.. code-block:: xml

    <?xml version="1.0" encoding="utf-8" ?>
    <file>
        <properties>....</properties>
        <testdefinition><![CDATA[pass]]></testdefinition>
        <testdevelopment>1448190694.813723</testdevelopment>
    </file>
    

**Test Suite Xml**

.. code-block:: xml

    <?xml version="1.0" encoding="utf-8" ?>
    <file>
        <properties>...</properties>
        <testdefinition><![CDATA[pass]]></testdefinition>
        <testexecution><![CDATA[pass]]></testexecution>
        <testdevelopment>1448190717.236711</testdevelopment>
    </file>
    

**Test Plan Xml**

.. code-block:: xml

    <?xml version="1.0" encoding="utf-8" ?>
    <file>
        <properties>...</properties>
        <testplan id="0">
            <testfile>
                <id>1</id>
                <color />
                <file>Common:Defaults/testunit.tux</file>
                <enable>2</enable>
                <extension>tux</extension>
                <alias />
                <type>remote</type>
                <parent>0</parent>
                <properties>....</properties>
                <description />
            </testfile>
        </testplan>
        <testdevelopment>1448190725.096519</testdevelopment>
    </file>
    

**Test Global Xml**

.. code-block:: xml

    <?xml version="1.0" encoding="utf-8" ?>
    <file>
        <properties>...</properties>
        <testplan id="0">
            <testfile>
                <id>1</id>
                <color />
                <file>Common:Defaults/testplan.tpx</file>
                <enable>2</enable>
                <extension>tpx</extension>
                <alias />
                <type>remote</type>
                <parent>0</parent>
                <properties>...</properties>
                <description />
            </testfile>
        </testplan>
        <testdevelopment>1448190733.690697</testdevelopment>
    </file>
    

Stockage des résultats de tests
-------------------------------

Les résultats de tests sont stockés sur le serveur dans le répertoire ``/opt/xtc/current/Var/TestsResult``.

Les résultats sont stockés:
 - par l'id des projets de test
 - par la date du jour d'exécution du test
 - et finalement par la date et heure d'exécutions des tests.
 
Organisation des résultats:

.. code-block:: bash

    Répertoire: <project_id>
        - Répertoire: <yyyy-mm-dd>
            - Répertoire: <yyyy-mm-dd_hh:mm:ss.testid.testname.username>
                - Fichier: TESTPATH 
                - Fichier: test.out
                - Fichier: test.ini
                - Fichier: <testname>_<replayid>.hdr
                - Fichier: <testname>_<replayid>_<result>_<nbcomments>.trv
                - Fichier: <testname>_<replayid>.tbrp
                - Fichier: <testname>_<replayid>.tdsx
                - Fichier: <testname>_<replayid>.trd
                - Fichier: <testname>_<replayid>.trp
                - Fichier: <testname>_<replayid>.trpx
                - Fichier: <testname>_<replayid>.trv
                - Fichier: <testname>_<replayid>.trvx
    

Description des fichiers:

 - ``TESTPATH`` contient le chemin d'accès complet pour le résultat de test
 - ``test.out`` contient les logs interne du test, à utiliser pour débugger le framework de test
 - ``test.ini`` contient des paramètres spécifiques au test
 - ``<testname>_<replayid>.hdr`` réprésente l'entête du résultat de test
 - ``<testname>_<replayid>_<result>_<nbcomments>.trv`` contient l'ensemble des évènements générés pendant l'exécution du tests
 - ``<testname>_<replayid>.tbrp`` contient le rapport basique au format html
 - ``<testname>_<replayid>.trp`` contient le rapport complet au format html
 - ``<testname>_<replayid>.trv`` contient le rapport des résultats au format csv


Contrôle Agents
---------------

Le pilotage des agents depuis un test s'effectue à travers:
 - les adaptateurs
 - et le serveur

La communication s'effectue avec l'échange de quelques messages spécifiques:
 - ``init``: permet d'initialiser un agent
 - ``notify``: permet d'envoyer un message à l'agent sans attendre de réponse
 - ``reset``: permet de faire un reset de l'agent
 - ``error``: permet à l'agent d'envoyer une erreur à l'adaptateur
 - ``data``: permet à l'agent d'envoyer des données à l'adaptateur

Sens de communications disponibles:
 - Agent -> serveur -> adaptateur -> test
 - Test -> adaptateur -> serveur -> agent
 
+---------------------------------+--------------------------------------------+
|                                 |               Agent                        |
|                                 +----------------------+---------------------+
|                                 |    Fonction          |   Callback          |
+---------------------------------+----------------------+---------------------+
| Envoie d'un message "error"     | def sendError        |                     |
|                                 |    * request         |                     |
|                                 |    * data            |                     |
+---------------------------------+----------------------+---------------------+
| Envoie d'un message "notify"    | def sendNotify       |                     |
|                                 |    * request         |                     |
|                                 |    * data            |                     |
+---------------------------------+----------------------+---------------------+
| Envoie d'un message "data"      | def sendData         |                     |
|                                 |    * request         |                     |
|                                 |    * data            |                     |
+---------------------------------+----------------------+---------------------+
| Réception d'un message "init"   |                      |  def onAgentInit    |
|                                 |                      |    * client         |
|                                 |                      |    * tid            |
|                                 |                      |    * request        |
+---------------------------------+----------------------+---------------------+
| Réception d'un message "reset"  |                      |  def onAgentNotify  |
|                                 |                      |    * client         |
|                                 |                      |    * tid            |
|                                 |                      |    * request        |
+---------------------------------+----------------------+---------------------+
| Réception d'un message "notify" |                      |  def onAgentReset   |
|                                 |                      |    * client         |
|                                 |                      |    * tid            |
|                                 |                      |    * request        |
+---------------------------------+----------------------+---------------------+


+---------------------------------+-------------------------------------------------------+
|                                 |             Adaptateur                                |
|                                 +------------------------+------------------------------+
|                                 |    Fonction            |   Callback                   |
+---------------------------------+------------------------+------------------------------+
| Réception d'un message "error"  |                        |  def receivedErrorFromAgent  |
|                                 |                        |        * data                |
+---------------------------------+------------------------+------------------------------+
| Réception d'un message "notify" |                        |  def receivedNotifyFromAgent |
|                                 |                        |        * data                |
+---------------------------------+------------------------+------------------------------+
| Réception d'un message "data"   |                        |  def receivedDataFromAgent   |
|                                 |                        |         * data               |
+---------------------------------+------------------------+------------------------------+
| Envoie d'un message "init"      |  def initAgent         |                              |
|                                 |     * data             |                              |
+---------------------------------+------------------------+------------------------------+
| Envoie d'un message "reset"     |  def resetAgent        |                              |
+---------------------------------+------------------------+------------------------------+
| Envoie d'un message "notify"    | def sendNotifyToAgent  |                              |
|                                 |     * data             |                              |
+---------------------------------+------------------------+------------------------------+

Les logs serveurs
----------------

les logs du serveurs sont localisés au même endroit sur le serveur, dans le répertoire ``/opt/xtc/current/Var/logs/``.

+--------------------+---------------------------------------------------------+
| access_rp.log      | logs apache pour l'accès reverse                        |
+--------------------+---------------------------------------------------------+
| access_ssl_rp.log  | logs apache pour l'accès reverse ssl                    |
+--------------------+---------------------------------------------------------+
| access_web.log     | logs apache pour l'accès web interface                  |
+--------------------+---------------------------------------------------------+
| error_rp.log       | logs erreurs apache pour l'accès reverse                |
+--------------------+---------------------------------------------------------+
| error_ssl_rp.log   | logs erreurs apache pour l'accès reverse ssl            |
+--------------------+---------------------------------------------------------+
| error_web.log      | logs erreurs apache pour l'accès web interface          |
+--------------------+---------------------------------------------------------+
| output.log         | logs serveurs                                           |
+--------------------+---------------------------------------------------------+
