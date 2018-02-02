Exemples avancés
===================

Adaptateur SSH
--------------

L'adaptateur ``SSH`` permet de se connecter sur des serveurs distants en utilisant le protocole SSH.

La configuration de l'adaptateur consiste à indiquer à minima:
 - l'adresse ip du serveur distant 
 - le port du serveur distant (par défaut 22)
 - le compte utilisateur
 
L'adaptateur supporte les fonctionnalités suivantes:
 - authentification par nom d'utilisateur et mot de passe
 - authentification par échange de clé
 
Exemple de configuration de l'adaptateur dans la section ``prepare`` du test.

.. code-block:: python
  
  self.ADP_SSH = SutAdapters.SSH.Client(
                                        parent=self, 
                                        login=input('LOGIN'), 
                                        password=input('PWD'),
                                        destIp=input('DEST_IP'), 
                                        destPort=input('DEST_PORT'), 
                                        debug=input('DEBUG'),
                                        agentSupport=input('SUPPORT_AGENT')
                                    )

Exemple pour se connecter, s'authentifier sur un serveur distant et se déconnecter:

.. code-block:: python
  
  connected = self.ADP_SSH.doConnect(
                                    timeout=input('TIMEOUT'), 
                                    prompt='~]#'
                                  )
  if not connected: self.abort("ssh connect failed")
  self.info("SSH connection OK" )
  
  disconnected = self.ADP.doDisconnect(timeout=input('TIMEOUT'))
  if not disconnected: self.abort("disconnect failed")
  self.info("SSH disconnection OK" )
  
  
Exemple pour envoyer une commande sur une machine distante:

.. code-block:: python
  
  rsp = self.ADP_SSH. doSendCommand(
                                    command='date', 
                                    timeout=input('TIMEOUT'), 
                                    expectedData=None, 
                                    prompt='~]#'
                                )
  if rsp is None: self.abort("run command failed")
  self.warning( rsp )
  
.. warning:: 
  Les réponses SSH peuvent être découpées en plusieurs évènements (celà dépend du réseau). 
  Il faut donc faire attention quand on attend une réponse spécifique, l'utilisation d'un buffer peut être nécessaire dans ce cas là.

.. note:: Des exemples sont disponibles dans l'échantillon ``/Samples/Tests_Adapters/05_SSH.tsx``.

Adaptateur HTTP
--------------

L'adaptateur ``HTTP`` permet d'envoyer des requêtes et d'inspecter les réponses associés vers un serveur Web.

La configuration de l'adaptateur consiste à indiquer à minima:
 - l'adresse ip du serveur distant 
 - le port du serveur distant (par défaut 80)
 
L'adaptateur supporte les fonctionnalités suivantes:
 - le chiffrement ``tls`` de la communication
 - l'utilisation de proxy ``socks4, 5`` et http
 - l'authentification ``digest`` ou ``basic``
 - le réassemblage des réponses ``chunked`` 
 
Exemple de configuration de l'adaptateur dans la section ``prepare`` du test.

.. code-block:: python
  
  self.ADP_HTTP = SutAdapters.HTTP.Client(
                                            parent=self, 
                                            debug=input('TRACE'), 
                                            destinationIp=input('DST_IP'), 
                                            destinationPort=input('DST_PORT'),
                                            sslSupport = input('SSL_SUPPORT'), 
                                            agent=agent('AGENT_SOCKET'), 
                                            agentSupport=input('SUPPORT_AGENT')
                                        )

Exemple pour envoyer une réquête de type ``GET`` et d'une réponse avec le code ``200``.

.. code-block:: python
  
  rsp = self.ADP_HTTP.GET( 
                            uri="/", 
                            host=input('HOST'), 
                            timeout=input('TIMEOUT'),
                            codeExpected=200
                        )
  if rsp is None:
    self.step1.setFailed(actual="bad response received")    
  else:
    self.step1.setPassed(actual="http response OK") 
  
Exemple pour envoyer une réquête de type ``GET`` et attendre une réponse répondant aux critères suivants:
 - la version doit se terminer par 1.1
 - le code ne doit pas contenir la valeur 200
 - la phrase ne doit pas contenir le texte `Testing`
 - le corps de la réponse doit contenir le texte `google`
 - la réponse doit contenir une entête contenant le texte `server`, peut importe la valeur

.. code-block:: python
  
  headersExpected = { TestOperators.Contains(needle='server'): TestOperators.Any() }
  
  rsp = self.ADP_HTTP.GET( 
                        uri="/", 
                        host=input('HOST'), 
                        timeout=input('TIMEOUT'),
                        versionExpected=TestOperators.Endswith(needle='1.1') ,
                        codeExpected=TestOperators.NotContains(needle='200') ,
                        phraseExpected=TestOperators.NotContains(needle='Testing') ,
                        bodyExpected=TestOperators.Contains(needle='google') )                                    
                        headersExpected=headersExpected
                        )
  if rsp is None:
    self.step1.setFailed(actual="bad response received")    
  else:
    self.step1.setPassed(actual="http response OK") 

Adaptateur Telnet
--------------

L'adaptateur ``Telnet`` permet de se connecter sur des machines disposant une interface telnet.

La configuration de l'adaptateur consiste à indiquer à minima:
 - l'adresse ip du serveur distant 
 - le port du serveur distant (par défaut 23)
 
Exemple de configuration de l'adaptateur dans la section ``prepare`` du test.

.. code-block:: python
  
  self.ADP_TELNET = SutAdapters.Telnet.Client(
                                            parent=self, 
                                            destIp=input('TELNET_IP'), 
                                            destPort=input('TELNET_PORT'),
                                            debug=input('DEBUG'),
                                            agentSupport=input('SUPPORT_AGENT')
                                            )
   
   
Exemple pour se connecter ou se déconnecter du serveur distant

.. code-block:: python
  
  self.ADP_TELNET.connect()
  connected = self.ADP_TELNET.isConnected( timeout=input('TIMEOUT') )
  if not connected: Test(self).interrupt( 'unable to connect' )

  self.ADP_TELNET.disconnect()
  disconnected = self.ADP_TELNET.isDisconnected( timeout=input('TIMEOUT') )
  if not disconnected: Test(self).interrupt( 'unable to disconnect' )
  

Exemple montrant comment attendre la réception d'un texte en particulier.

.. code-block:: python
  
  rsp = self.ADP_TELNET.hasReceivedData( 
                                        timeout=input('TIMEOUT'), 
                                        dataExpected=TestOperators.Contains(needle='Password:') )
                                        )
  if rsp is None: Test(self).interrupt( 'Password prompt not found' )
  

Exemple pour envoyer des données au serveur distant

.. code-block:: python
  
  todo
  

<à insérer>

.. warning: les réponses telnet peuvent être splittées en plusieurs évènements, il faut donc faire attention quand on
recherche un texte en particulier. Pour se prémunir de ce problème, il faut ajouter un buffer intermédiare, il y a un
exemple complet avec l'adaptateur ``Catalyst``.

.. note:: Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Adapters/12_Telnet.tsx``.
    
Adaptateur MySQL
--------------

L'adaptateur ``MySQL`` permet de se connecter sur une base donnée distante.

La configuration de l'adaptateur consiste à indiquer à minima:
 - l'adresse ip du serveur distant 
 - le port du serveur distant (par défaut xxxx)
 - le nom d'utilisateur
 - le mot de passe associé
 
Exemple de configuration de l'adaptateur dans la section ``prepare`` du test.

.. code-block:: python
  
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
  

Exemple pour se connecter ou se déconnecter du serveur distant:

.. code-block:: python
  
  self.ADP_MYSQL.connect(dbName=input('MYSQL_DB'), timeout=input('TIMEOUT'))

  self.ADP_MYSQL.disconnect()
  

Exemple pour exécuter une requête SQL dans la base de donnée:

.. code-block:: python
  
  query = 'SELECT id FROM `%s-users` WHERE login="admin"' % input('TABLE_PREFIX')
  self.ADP_MYSQL.query(query=query)
  rsp = self.ADP_MYSQL.hasReceivedRow(timeout=input('TIMEOUT'))
  

.. note:: Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Adapters/15_Database.tsx``.
 
Adaptateur SNMP
--------------

L'adaptateur ``SNMP`` permet de recevoir des alarmes SNMP v1 ou v2.

La configuration de l'adaptateur consiste à indiquer à minima:
 - l'adresse d'écoute
 - le port d'écoute
 
Exemple de configuration de l'adaptateur dans la section ``prepare`` du test.

.. code-block:: python
  
  self.ADP_SNMP = SutAdapters.SNMP.TrapReceiver(
                                                parent=self, 
                                                bindIp=get('SRC_IP'), 
                                                bindPort=get('SRC_PORT'), 
                                                debug=get('DEBUG'),
                                                agent=agent('AGENT_SOCKET'), 
                                                agentSupport=input('SUPPORT_AGENT')
                                                )
  

Exemple pour démarrer l'écoute du serveur

.. code-block:: python
  
  self.ADP_SNMP.startListening()
  listening = self.ADP_SNMP.udp().isListening( timeout=get('TIMEOUT') )
  if not listening: Test(self).interrupt( 'UDP not listening' )
  

Exemple pour attendre la réception d'une alarme:

.. code-block:: python
  
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
  

.. note:: Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Adapters/18_SNMP.tsx``.

    
Adaptateur FTP(s)
--------------

L'adaptateur ``FTP`` permet de se connecter sur des serveurs distants et supporte les fonctions suivantes:
 - Connection en TLS
 - Téléchargement ou récupation de fichiers ou répertoires
 - Ajout/suppression et renommage de fichiers ou répertoires
 - Lister le contenu d'un répertoires
 - Détecter l'apparition d'un fichier ou répertoire avec le support des expressions régulières.

La configuration de l'adaptateur consiste à indiquer à minima:
 - l'adresse ip du serveur distant
 - le nom d'utilisateur pour se connecter
 - le mot de passe
 
Exemple de configuration de l'adaptateur dans la section ``prepare`` du test.

.. code-block:: python
  
  self.ADP_FTP = SutAdapters.FTP.Client(
                                        parent=self,
                                        debug=input('DEBUG'),
                                        destinationIp=input('FTP_HOST'),
                                        user=input('FTP_USER'), 
                                        password=input('FTP_PWD') ,
                                        agentSupport=input('SUPPORT_AGENT')
                                        )
  


Exemple pour se connecter ou déconnecter du serveur FTP:

.. code-block:: python
  
  self.ADP_FTP.connect(passiveMode=True)
  if self.ADP_FTP.isConnected(timeout=input('TIMEOUT')) is None:
      Test(self).interrupt("unable to connect")

  self.ADP_FTP.login()
  if self.ADP_FTP.isLogged(timeout=input('TIMEOUT')) is None:
      Test(self).interrupt("unable to login")
  Trace(self).info("SFTP connection OK" )
  

.. code-block:: python
  
  self.ADP_FTP.disconnect()
  if self.ADP_FTP.isDisconnected(timeout=input('TIMEOUT')) is not None:
     Test(self).interrupt("disconnect failed")
  Trace(self).info("FTP disconnection OK" )
  

Exemple pour lister le contenu d'un répertoire:

.. code-block:: python
  
  self.ADP_FTP.listingFolder()
  if self.ADP_FTP.hasFolderListing(timeout=input('TIMEOUT')) is not None:
      Trace(self).error("unable to get listing folder")
  

Exemple pour détecter un fichier dans un répertoire avec une expression régulière:

.. code-block:: python
  
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
  

.. note:: Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Adapters/21_Ftp.tsx``.

Adaptateur SFTP
---------------

L'adaptateur ``SFTP`` permet de se connecter sur des serveurs disposants d'une interface SSH.
Les fonctionnalités suivantes sont supportées:
 - Téléchargement ou récupation de fichiers ou répertoires
 - Ajout/suppression et renommage de fichiers ou répertoires
 - Lister le contenu d'un répertoires
 - Détecter l'apparition d'un fichier ou répertoire avec le support des expressions régulières.
 
La configuration de l'adaptateur consiste à indiquer à minima:
 - l'adresse ip du serveur distant
 - le nom d'utilisateur pour se connecter
 - le mot de passe
 
Exemple de configuration de l'adaptateur dans la section ``prepare`` du test.

.. code-block:: python
  
  self.ADP_SFTP = SutAdapters.SFTP.Client(
                                            parent=self, 
                                            login=input('LOGIN'), 
                                            password=input('PWD'),
                                            destIp=input('DEST_IP'), 
                                            destPort=input('DEST_PORT'), 
                                            debug=input('DEBUG'),
                                            agentSupport=input('SUPPORT_AGENT')
                                        )
  

Exemple pour se connecter et déconnecter du serveur:

.. code-block:: python
  
  connected = self.ADP_SFTP.doConnect(timeout=input('TIMEOUT'))
  if not connected: Test(self).interrupt("sftp connect failed")
  self.info("SFTP connection OK" )

  disconnected = self.ADP_SFTP.doDisconnect(timeout=input('TIMEOUT'))
  if not disconnected: Test(self).interrupt("disconnect failed")
  self.info("SFTP disconnection OK" )
  

Exemple pour lister le contenu d'un répertoire:

.. code-block:: python
  
  self.ADP_SFTP.listingFolder(
                            path="/var/log/", 
                            extended=False
                            )


  rsp = self.ADP_SFTP.hasFolderListing(timeout=input('TIMEOUT'))
  if rsp is None: Trace(self).error("unable to get listing folder")
  self.warning( rsp.get("SFTP", "result") )
  

Exemple pour détecter un fichier dans un répertoire avec une expression régulière:

.. code-block:: python
  
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
  

.. note:: Un exemple est disponible dans les échantillons de tests ``/Samples/Tests_Adapters/22_Sftp.tsx``.


Librairie ChartJS
-------------------

L'adaptateur ``ChartJs``, basé sur la librairie javascript du même nom, permet de
générer des graphiques pouvant être intégré dans une page html.
L'intérêt principal de cette librairie est de pouvoir intégrer des graphiques dans le rapport de test.

Exemple de configuration de la librairie dans la section ``prepare`` du test.

.. code-block:: python
  
  self.LIB_CHART = SutLibraries.Media.ChartJS(parent=self, name=None, debug=False)
  

Exemple pour générer un graphique de type barre et l'intégrer dans le rapport

.. code-block:: python
  
  # génération de données 
  labelsAxes = ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"]
  dataA = [12, 19, 3, 5, 2, 3]
  dataB = [22, 49, 3, 5, 23, 3]
  legendDatas = ["tets", "test"]
  backgroundColor = '#4BC0C0'
  borderColor = '#36A2EB'

  # génération du grahique
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
                                
  # ajout du graphique dans le résultat de l'étape
  self.step1.setPassed(actual="chart", chart=myChart)
  

Le graphique est inséré automatiquement dans le rapport avancé.

.. image:: /_static/images/examples/report_chart.png

  
Paramètre de tests "custom"
-------------------

Le paramètre de type ``custom`` permet de construire des valeurs appelant d'autres variables.

Prenons l'exemple d'un test contenant les 2 variables suivantes:
 - DEST_IP avec la valeur 192.168.1.1
 - DEST_PORT avec la valeur 8080

.. image:: /_static/images/examples/custom_inputs.png
 
Le type ``custom`` va nous permettre de construire une 3ième variable 
 - DEST_URL avec la valeur 
 
   .. image:: /_static/images/examples/custom_config.png

Le mot clé ``[!INPUT:<NOM_VARIABLE_ENTRANTE:]`` permet d'appeler une autre variable entrante.
Le framework remplacera au moment de l'exécution du test les différents mots clés avec la valeur associée.
On obtiendra comme valeur https://192.168.1.1:8080/welcome pour la variable DEST_URL.

.. image:: /_static/images/examples/custom_example.png

Pour aller plus loin, il est aussi possible d'ajouter une valeur disponible depuis le cache.
Partant du principe que la valeur "welcome?user=hello" est dans le cache et accessible via la clé "url_params".
Il est possible de l'intégration dans le paramètre comme ci-dessous

.. image:: /_static/images/examples/custom_config_cache.png

Exemple de résultat après exécution:

.. image:: /_static/images/examples/custom_example_cache.png


Paramètre de tests "alias"
-------------------

Le paramètre de type ``alias`` peut être utilisé pour définir un nouveau nom pour un paramètre déjà existant.
Ce mécanisme peut être utilisé dans les ``test plan`` pour éviter de surcharger tout les paramètres ayant le même nom.

Exemple d'utilisation

 1. Avant exécution
   ::
    
    Scénario (TIMEOUT_A(int)=2 secondes)
     ---> Test 1 (TIMEOUT_A(int)=10 secondes)
     ---> Test 2 (TIMEOUT_A(int)=30 secondes)
     ---> Test 3 (TIMEOUT_A(int)=20 secondes)
 
 2. Après exécution du test
   
   ::
     
     Scénario (TIMEOUT_A(int)=2 secondes)
       ---> Test 1 (TIMEOUT_A(int)=2 secondes)
       ---> Test 2 (TIMEOUT_A(int)=2 secondes)
       ---> Test 3 (TIMEOUT_A(int)=2 secondes)
     
     
Quand on exécute le scénario ci-dessus, le test 1, 2 et 3 ont automatiquement la valeur 2 secondes pour le paramètre TIMEOUT_A.
C'est le comportement apporté par le framework de test.

**Comment faire si on souhaite que le test 2 garde la valeur 30 secondes par contre le test 1 et 2 hérite de la valeur du scénario ?**

Il faut utiliser un paramètre de type ``alias``, ils ne sont pas surchargés par le framework.

 1. Avant exécution
   ::
    
    Scénario (TIMEOUT_A(int)=2 secondes et TIMEOUT_B(int)=30 secondes)
     ---> Test 1 (TIMEOUT_A(int)=10 secondes)
     ---> Test 2 (TIMEOUT_A(alias)=TIMEOUT_B et TIMEOUT_B(int) = 0 secondes)
     ---> Test 3 (TIMEOUT_A(int)=20 secondes)
 
 2. Après exécution du test
   
   ::
     
    Scénario (TIMEOUT_A(int)=2 secondes et TIMEOUT_B(int)=30 secondes)
     ---> Test 1 (TIMEOUT_A(int)=2 secondes)
     ---> Test 2 (TIMEOUT_A(alias)=TIMEOUT_B et TIMEOUT_B(int)= 30 secondes)
     ---> Test 3 (TIMEOUT_A(int)=2 secondes)
     


Paramètre de tests "dataset"
-------------------

Le paramètre de type ``dataset`` permet d'importer des fichiers ``tdx``.
Un fichier ``dataset`` est juste un fichier texte, il est possible de le créer à partir du client graphique et de le sauvegarder dans le dépôt des tests distants.

.. image:: /_static/images/client/client_new_tdx.png 

Exemple de contenu d'un fichier dataset avec le format csv

.. code-block:: python
  
  a;1;administrator
  b;2;tester
    

Ce fichier peut être utilisé dans un test l'important dans les paramètres.

.. image:: /_static/images/examples/client_testdata.png


Exemple pour lire la variable:

.. code-block:: python
  
  for d in input('DATA').splitlines():
      Trace(self).info( d ) 
  
Paramètre de tests "shared"
-------------------

Les paramètres de type ``shared`` s'ajoutent depuis l'interface web ou depuis l'api REST.
Ils sont partagés et accessibles par l'ensemble des tests d'un même projet. La valeur attendue 
pour ce paramètre est de type ``JSON``.

Une fenêtre de sélection dans le client graphique permet de sélectionner le paramètre à utiliser dans le test.

.. image:: /_static/images/examples/client_params_shared.png

Dans l'exemple ci-dessous, le paramètre de test ``MY_SERVER`` contient la valeur de la clé ``IP`` présente dans la variable 
partagée ``MY_SERVER`` qui est elle-même présente dans le projet ``Common``.

.. image:: /_static/images/examples/client_param_shared.png

.. tip:: Pour avoir un paramètre de test qui contient une liste d'éléments, il faut utiliser le type ``list-shared``.

Utilisation d'une sonde
-------------------


Pour utiliser une sonde, il faut 2 choses:
 - Déployer la boite à outils et démarrer la sonde souhaitée.
 - Déclarer la sonde dans le test.
 
Pour sélectionner la sonde dans le test, il faut l'activer et la configurer dans le test (onglet ``Miscellaneous > Probes``)

.. image:: /_static/images/examples/probe_tab.png

Lors qu'une sonde est activée sur un test, l'exécution du test intialise automatiquement la sonde.

.. image:: /_static/images/examples/probe_starting.png

Après exécution, l'ensemble des fichiers collectés par la sonde sont téléchargés dans le serveur et accessible depuis le client graphique.

.. image:: /_static/images/examples/probe_test_archives.png

.. note:: Il est possible d'utiliser plusieurs sondes dans un test.

Utilisation d'un agent
-------------------

Pour utiliser un agent, il faut deux choses:
 - Déployer la boite à outils et sélectionner l'agent souhaité.
 - Déclarer l'agent dans le test
 - Configurer l'adaptateur pour utiliser l'agent.

Les agents sont à déclarer depuis le client dans l'onglet ``Miscellaneous > Agents`` 

.. image:: /_static/images/examples/client_properties_agent.png


L'activation du mode agent sur les adaptateurs se fait avec les arguments ``agentSupport`` et ``agent``.

.. code-block:: python
  
  agentSupport=input('SUPPORT_AGENT'), 
  agent=agent('AGENT_SOCKET')
  

.. code-block:: python
  
   self.ADP_REST= SutAdapters.REST.Client(
                                        parent=self,
                                        destinationIp=input('HOST'),
                                        destinationPort=input('PORT'),
                                        debug=input('DEBUG'),
                                        sslSupport=input('USE_SSL'),
                                        agentSupport=input('SUPPORT_AGENT'), 
                                        agent=agent('AGENT_SOCKET')
                                        )
   
   

Dans la fenêtre d'analyse, il est possible de voir l'agent utilisé pour chaque évènement:

.. image:: /_static/images/examples/client_events_logger_agent.png

.. note:: 
  Il est conseillé de mettre en paramètre de test l'usage du mode agent.
  
  .. image:: /_static/images/examples/client_agent_support.png