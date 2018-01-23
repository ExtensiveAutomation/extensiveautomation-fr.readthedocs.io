Spécifications
=============

Gestion des mots de passes
-------------------

Aucun mot de passe en clair n'est stockée dans la base de donnée seul un hash.
Le hash du mot de passe est stocké dansl a table `xtc-users`.

L'algorithme utilisé:

.. code-block::

    hash_password = SHA1 ( SALT + SHA1(user_password) )
    

.. image:: /_static/images/server/server_table_pwd.png

Format des fichiers
-------------------

Les tests sont au format `XML` zippés. Il existe plusieurs formats de tests:
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

Les résultats de tests sont stockés sur le serveur dans le répertoire `/opt/xtc/current/Var/TestsResult`.

Organisation des résultats:

.. code-block::
    
    Répertoire: <project_id>
        - Répertoire: <yyyy-mm-dd>
            - Répertoire: <yyyy-mm-dd_hh:mm:ss.testid.testname.username>
                - Fichier: TESTPATH                                        # the real path of the test
                - Fichier: test.out                                        # internal logs
                - Fichier: test.ini                                        # internal settings for the test
                - Fichier: <testname>_<replayid>.hdr                       # header of the result
                - Fichier: <testname>_<replayid>_<result>_<nbcomments>.trv # all events occured during the test
                - Fichier: <testname>_<replayid>.tbrp                      # basic report in html
                - Fichier: <testname>_<replayid>.tdsx
                - Fichier: <testname>_<replayid>.trd
                - Fichier: <testname>_<replayid>.trp                       # report in html
                - Fichier: <testname>_<replayid>.trpx
                - Fichier: <testname>_<replayid>.trv                       # report in csv
                - Fichier: <testname>_<replayid>.trvx
    
