Exemples avancés
===================

Adaptateur Telnet
--------------

This sample show how to use the TELNET client adapter. This adapter enables to connect to server through the TELNET protocol.

The following explanations are based on the sample available on /Samples/Tests_Adapters/12_Telnet.tsx
Adapter configuration

    Configure your adapter in the prepare section of your test

    self.ADP_TELNET = SutAdapters.Telnet.Client(
                                                parent=self, 
                                                destIp=input('TELNET_IP'), 
                                                destPort=input('TELNET_PORT'),
                                                debug=input('DEBUG'),
                                                agentSupport=input('SUPPORT_AGENT')
                                                )

    with the following parameters
    Input 	Type 	Value
    DEBUG 	boolean 	False
    TELNET_IP 	string 	192.168.1.1
    TELNET_PORT 	integer 	22
    SUPPORT_AGENT 	boolean 	False

Make connection and disconnection

    In the definition part, copy/paste the following lines to make connection

    self.ADP_TELNET.connect()
    connected = self.ADP_TELNET.isConnected( timeout=input('TIMEOUT') )
    if not connected: Test(self).interrupt( 'unable to connect' )

    Copy/paste the following line to make a disconnection from your machine

    self.ADP_TELNET.disconnect()
    disconnected = self.ADP_TELNET.isDisconnected( timeout=input('TIMEOUT') )
    if not disconnected: Test(self).interrupt( 'unable to disconnect' )

Use operators to detect specific data

    Copy/paste the following line to wait specific data

    rsp = self.ADP_TELNET.hasReceivedData( 
                                            timeout=input('TIMEOUT'), 
                                            dataExpected=TestOperators.Contains(needle='Password:') )
                                        )
    if rsp is None: Test(self).interrupt( 'Password prompt not found' )

Notes:

    Telnet responses can be splitted in severals events, so you new to retrieve properly all events to create the complete response.
    Please to use the make your own adapter with a codec if this behaviour is problematic for you.

    
Adaptateur MySQL
--------------

This sample show how to use the MySQL client adapter. The following explanations are based on the sample available on /Samples/Tests_Adapters/15_Database.tsx
Adapter configuration

    Configure your adapter in the prepare section of your test

    self.ADP_MYSQL = SutAdapters.Database.MySQL(
                                            parent=self, 
                                            host=input('HOST_DST'), 
                                            user=input('MYSQL_LOGIN'),
                                            password=input('MYSQL_PWD'), 
                                            debug=input('DEBUG'), 
                                            verbose=input('VERBOSE'),
                                            agent=agent('AGENT_DB'), 
                                            agentSupport=input('SUPPORT_AGENT')
                                        )

    with the following parameters
    Input 	Type 	Value
    DEBUG 	boolean 	False
    VERBOSE 	boolean 	False
    MYSQL_LOGIN 	string 	admin
    MYSQL_PWD 	string 	admin
    HOST_DST 	string 	192.168.1.1
    SUPPORT_AGENT 	boolean 	False

Make connection and disconnection

    In the definition part, copy/paste the following lines to make connection. You need to provide the database

    self.ADP_MYSQL.connect(dbName=input('MYSQL_DB'), timeout=input('TIMEOUT'))

    Copy/paste the following line to make a disconnection from your machine

    self.ADP_MYSQL.disconnect()

Execute sql query

    Copy/paste the following lines to execute a sql query in the table.

    query = 'SELECT id FROM `%s-users` WHERE login="admin"' % input('TABLE_PREFIX')
    self.ADP_MYSQL.query(query=query)
    rsp = self.ADP_MYSQL.hasReceivedRow(timeout=input('TIMEOUT'))


    
Adaptateur SNMP
--------------

This sample show how to use the SNMP client adapter. This adapter enables to receive SNMP trap v1 or v2:

The following explanations are based on the sample available on /Samples/Tests_Adapters/18_SNMP.tsx
Adapter configuration

    Configure your adapter in the prepare section of your test

    self.ADP_SNMP = SutAdapters.SNMP.TrapReceiver(
                                                    parent=self, 
                                                    bindIp=get('SRC_IP'), 
                                                    bindPort=get('SRC_PORT'), 
                                                    debug=get('DEBUG'),
                                                    agent=agent('AGENT_SOCKET'), 
                                                    agentSupport=input('SUPPORT_AGENT')
                                                )

    with the following parameters
    Input 	Type 	Value
    DEBUG 	boolean 	False
    SRC_IP 	string 	0.0.0.0
    SRC_PORT 	integer 	162
    SUPPORT_AGENT 	boolean 	False

Checking snmp trap

    In the definition part, copy/paste the following lines to start to listen

    self.ADP_SNMP.startListening()
    listening = self.ADP_SNMP.udp().isListening( timeout=get('TIMEOUT') )
    if not listening: Test(self).interrupt( 'UDP not listening' )

    Copy/paste the following line to check the reception of one specific trap

    trap = self.UDP_ADP.hasReceivedTrap(
                                            timeout=input('TIMEOUT'), 
                                            version=SutAdapters.SNMP.TRAP_V1, 
                                            community=None, 
                                            agentAddr=None, 
                                            enterprise=None,
                                            genericTrap=None, 
                                            specificTrap="17", 
                                            uptime=None, 
                                            requestId=None, 
                                            errorStatus=None, 
                                            errorIndex=None
                                        )
    if trap is None:  Test(self).interrupt("trap expected not received")


    
Adaptateur FTP(s)
--------------

This sample show how to use the FTP client adapter. This adapter enables to connect to server through the FTP protocol with support of:

    Secure channel with TLS
    Download/upload files or folders
    Add/rename/delete files or folders
    List the content of a folder
    Detect file or folder with regular expression support

The following explanations are based on the sample available on /Samples/Tests_Adapters/21_Ftp.tsx
Adapter configuration

    Configure your adapter in the prepare section of your test

    self.ADP_FTP = SutAdapters.FTP.Client(
                                            parent=self,
                                            debug=input('DEBUG'),
                                            destinationIp=input('FTP_HOST'),
                                            user=input('FTP_USER'), 
                                            password=input('FTP_PWD') ,
                                            agentSupport=input('SUPPORT_AGENT')
                                            )

    with the following parameters
    Input 	Type 	Value
    DEBUG 	boolean 	False
    FTP_USER 	string 	admin
    FTP_PWD 	string 	admin
    FTP_HOST 	string 	192.168.1.1
    SUPPORT_AGENT 	boolean 	False

Make connection and disconnection

    In the definition part, copy/paste the following lines to make connection with authentification.

    self.ADP_FTP.connect(passiveMode=True)
    if self.ADP_FTP.isConnected(timeout=input('TIMEOUT')) is None:
        Test(self).interrupt("unable to connect")


    self.ADP_FTP.login()
    if self.ADP_FTP.isLogged(timeout=input('TIMEOUT')) is None:
        Test(self).interrupt("unable to login")


    Trace(self).info("SFTP connection OK" )

    Copy/paste the following line to make a disconnection from your machine

    self.ADP_FTP.disconnect()
    if self.ADP_FTP.isDisconnected(timeout=input('TIMEOUT')) is not None:
        Test(self).interrupt("disconnect failed")


    Trace(self).info("FTP disconnection OK" )

List the content of a specific folder

    In the definition part, copy/paste the following lines

    self.ADP_FTP.listingFolder()
    if self.ADP_FTP.hasFolderListing(timeout=input('TIMEOUT')) is not None:
        Trace(self).error("unable to get listing folder")

Detect a file in a specific folder with regular expression

    In the definition part, copy/paste the following lines

    self.ADP_FTP.waitForFile(
                            path='/var/log/', 
                            filename='^messages-.*$', 
                            timeout=input('TIMEOUT')
                        )


    found = self.ADP_FTP.hasDetectedFile(
                                        path=None, 
                                        filename=None, 
                                        timeout=input('TIMEOUT')
                                    )
    if found is None: Trace(self).error("file not found")



Adaptateur SFTP
---------------

This sample show how to use the SFTP client adapter.
 This adapter enables to manipulate files system in a remote system throught the SFTP procotol 
 (Secure File Transfer Protocol). Features supported:

    Download/upload files or folders
    Add/rename/delete files or folders
    List the content of a folder
    Detect file or folder with regular expression support

The following explanations are based on the sample available on /Samples/Tests_Adapters/22_Sftp.tsx
Adapter configuration

    Configure your adapter in the prepare section of your test

    self.ADP_SFTP = SutAdapters.SFTP.Client(
                                            parent=self, 
                                            login=input('LOGIN'), 
                                            password=input('PWD'),
                                            destIp=input('DEST_IP'), 
                                            destPort=input('DEST_PORT'), 
                                            debug=input('DEBUG'),
                                            agentSupport=input('SUPPORT_AGENT')
                                        )

    with the following parameters
    Input 	Type 	Value
    DEBUG 	boolean 	False
    LOGIN 	string 	admin
    PWD 	string 	admin
    DEST_IP 	string 	192.168.1.1
    DEST_PORT 	integer 	22
    SUPPORT_AGENT 	boolean 	False

Make connection and disconnection

    In the definition part, copy/paste the following lines to make connection with authentification.

    connected = self.ADP_SFTP.doConnect(timeout=input('TIMEOUT'))
    if not connected: Test(self).interrupt("sftp connect failed")


    self.info("SFTP connection OK" )

    Copy/paste the following line to make a disconnection from your machine

    disconnected = self.ADP_SFTP.doDisconnect(timeout=input('TIMEOUT'))
    if not disconnected: Test(self).interrupt("disconnect failed")


    self.info("SFTP disconnection OK" )

List the content of a specific folder

    In the definition part, copy/paste the following lines

    self.ADP_SFTP.listingFolder(
                            path="/var/log/", 
                            extended=False
                            )


    rsp = self.ADP_SFTP.hasFolderListing(timeout=input('TIMEOUT'))
    if rsp is None: Trace(self).error("unable to get listing folder")


    self.warning( rsp.get("SFTP", "result") )

Detect a file in a specific folder with regular expression

    In the definition part, copy/paste the following lines

    self.ADP_SFTP.waitForFile(
                            path='/var/log/', 
                            filename='^messages-.*$', 
                            timeout=input('TIMEOUT')
                        )


    found = self.ADP_SFTP.hasDetectedFile(
                                        path=None, 
                                        filename=None, 
                                        timeout=input('TIMEOUT')
                                    )
    if found is None: Trace(self).error("file not found")



Librairie Graphique
-------------------

This feature enables to add charts in test report. Collects some data during the run of your test and display them in the test report with charts.

Adding a chart in test report

Click on the button to create a new test

Initialize the ChartJS library in the prepare section of your test

self.LIB_CHART = SutLibraries.Media.ChartJS(parent=self, name=None, debug=False)

Generate some fake data

labelsAxes = ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"]
dataA = [12, 19, 3, 5, 2, 3]
dataB = [22, 49, 3, 5, 23, 3]
legendDatas = ["tets", "test"]
backgroundColor = '#4BC0C0'
borderColor = '#36A2EB'

Generate the chart and put-it to the step

myChart = self.LIB_CHART.barChart(
                                    labelsAxes=labelsAxes, 
                                    datas=[dataA, dataB], 
                                    legendDatas=legendDatas, 
                                    width=400, 
                                    height=300,
                                    backgroundColors=[borderColor, backgroundColor], 
                                    borderColors=[borderColor, backgroundColor],
                                    chartTitle="test"
                                )
self.step1.setPassed(actual="chart", chart=myChart)

Go the test archives and load the test report, the chart will appears on the report.

.. image:: /_static/images/examples/report_chart.png

