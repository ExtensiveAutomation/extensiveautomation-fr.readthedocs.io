1ière utilisation
=================

Connexion du client au serveur
------------------------------

Après avoir ouvert le client, la première étape consiste à se connecter au serveur de test.
Pour se faire il faut avoir à disposition son compte utilisateur ainsi que l'adresse du serveur.

La fenêtre de connexion est disponible depuis le menu `Get Started > Connect` ou bien directement sur la page d'accueil.
Une fois la connexion réussie, l'utilisateur peut accéder à l'ensemble des tests automatiques existent sur le serveur.

.. image:: /_static/images/client/client_connect.png

.. note:: l'utilisateur `admin` peut être utilisé dans le cadre de la découverte de la solution.

Ecriture d'un test
------------------

La première utilisation consiste à créer un très simple premier cas de test en affichant la valeur d'un paramètre du test.

1. Créer un test de type "Unit"
   
   .. image:: /_static/images/client/client_new_tux.png

2. Ajouter le paramètre MON_PARAMETRE de type `str` avec la valeur "bonjour"
   
   .. image:: /_static/images/client/client_new_param.png

3. Modifier le test au niveau de la section `definition` pour afficher la valeur du paramètre.
   
   .. image:: /_static/images/client/client_new_trace.png

4. Enregistrer le test dans le dépôt avec le nom "Test_A" dans le répertoire `Sandbox`
   
   .. image:: /_static/images/client/client_new_save.png

Ecriture d'un scénario
----------------------

.. note:: Ce mini guide part du principe que vous avez suivi le chapitre `Ecriture d'un test`.

L'exemple suivant explique comment créer son premier scénario avec une surcharge des variables de tests.

1. Créer un test de type "Plan".
   
   .. image:: /_static/images/client/client_new_tpx.png

2. Insérer le test "Test_A" dans le scénario. Cliquer sur le bouton `Insert Child` et sélectionner le test `Test_A`.

   .. image:: /_static/images/client/client_new_insert.png

3. Après insertion, cliquer sur le test `Test_A` et insérer de nouveau le même test.

   .. image:: /_static/images/client/client_new_insert_again.png

4. Enregistrer le scénario dans le dépôt de test avec le nom "Scenario_A" dans le répertoire `Sandbox`.

5. Ajouter le paramètre MON_PARAMETRE avec la valeur "au revoir" au niveau du scénario.

.. tip:: Ne pas hésitez à définir un alias pour le nom du test pour rendre le scénario plus lisible.

Exécution d'un test
-------------------

.. note:: Ce mini guide part du principe que vous avez suivi les chapitres `Ecriture d'un test` et `Ecriture d'un scénario`.

L'exécution d'un test peut se faire en cliquant sur le bouton `Execute`.
Ouvrir les tests `Test_A` et `Scenario_A` et les exécuter.

.. image:: /_static/images/client/client_execute.png

Analyse des résultats
---------------------

.. note:: Ce mini guide part du principe que vous avez suivi les chapitres `Ecriture d'un test` et `Ecriture d'un scénario`.


La 1ière fenêtre d'analyse montre l'exécution du test "Test_A" et notamment le message "bonjour".

La 2ième fenêtre d'analyse montre l'exécution du test "Scenario_A" et notamment le message "au revoir".

Ce premier usage montre comment exécuter un test et un scénario ansi que la surcharge des variables de tests.


Conception assistée
-------------------

L'assistant permet de créer des tests sans connaissances en développement. Il peut être utilisé pour:
 - Utiliser les fonctions basiques du framework
 - Exécuter des commandes systèmes (ssh)
 - Tester des applications avec un client lourd
 - Tester des applications web
 - Exécuter des actions sur un mobile android

Basique
~~~~~~~

Liste des actions disponibles:

+--------------------+-----------------------------------------------------------------+
| LOG MESSAGE        |  Affiche un message d'information durant l'exécution du test    |
+--------------------+-----------------------------------------------------------------+
| LOG WARNING        |  Affiche un message d'attention durant l'exécution du tet       |
+--------------------+-----------------------------------------------------------------+
| SET VALUE          |  Sauvegarde une donnée dans le cache                            |
+--------------------+-----------------------------------------------------------------+
| RESET CACHE        |  Vide complètement le cache                                     |
+--------------------+-----------------------------------------------------------------+
| USERCODE           |  Permet d'ajouter du code personalisé dans le test              |
+--------------------+-----------------------------------------------------------------+
| WAIT DURING        |  Attend pendant xx secondes                                     |
+--------------------+-----------------------------------------------------------------+
| CHECK IF VALUE     |  Vérifie si la value contient un texte spécifique               |
+--------------------+-----------------------------------------------------------------+
| ASK SOMETHING      |  Demande une valeur à l'utilisateur (mode interaction)          |
+--------------------+-----------------------------------------------------------------+

.. image:: /_static/images/client_assistant/aa_basic_link.png

.. image:: /_static/images/client_assistant/aa_basic.png

.. image:: /_static/images/client_assistant/aa_basic_log.png

.. image:: /_static/images/client_assistant/aa_basic_check.png

.. image:: /_static/images/client_assistant/aa_basic_test.png

Système
~~~~~~~

Liste des actions disponibles: 

+--------------------+-----------------------------------------------------------------+
| OPEN SSH SESSION   |  Ouvre une session SSH                                          |
+--------------------+-----------------------------------------------------------------+
| CLOSE SESSION      |  Ferme la session                                               |
+--------------------+-----------------------------------------------------------------+
| CLEAR SCREEN       |  Vide l'écran                                                   |
+--------------------+-----------------------------------------------------------------+
| SEND TEXT          |  Envoi une chaine de caractère                                  |
+--------------------+-----------------------------------------------------------------+
| SEND SHORTCUT      |  Envoi un raccourci clavier (pour interrompre une action)       |
+--------------------+-----------------------------------------------------------------+
| CHECKING IF SCREEN |  Vérifie si l'écran contient un texte spécifique                |
+--------------------+-----------------------------------------------------------------+

.. image:: /_static/images/client_assistant/aa_system_open.png

.. image:: /_static/images/client_assistant/aa_system_check.png

Application
~~~~~~~~~~~~

Liste des actions disponibles:

**Contrôle de la souris** 	

+---------------------------+-----------------------------------------------------------------+
| CLICK ON POSITION         |  Clic sur la position (x,y)                                     |
+---------------------------+-----------------------------------------------------------------+
| DOUBLE CLICK ON POSITION  |  Double clic sur la position (x,y)                              |
+---------------------------+-----------------------------------------------------------------+
| RIGHT CLICK ON POSITION   |  Clic droit sur la position (x,y)                               |
+---------------------------+-----------------------------------------------------------------+
| MOUSE WHEEL DOWN          |  Mouse wheel down                                               |
+---------------------------+-----------------------------------------------------------------+
| MOUSE WHEEL UP            |  Mouse wheel up                                                 |
+---------------------------+-----------------------------------------------------------------+
| MOVE TO POSITION          |  Déplace le curseur sur la position (x,y)                       |
+---------------------------+-----------------------------------------------------------------+
 
**Contrôle du clavier** 	

+---------------------------+-----------------------------------------------------------------+
| TYPE TEXT                 |  Simulate keyboard and type text                                |
+---------------------------+-----------------------------------------------------------------+
| TYPE PATH                 |  Simulate keyboard and type text path                           |
+---------------------------+-----------------------------------------------------------------+
| TYPE PASSWORD             |  Simulate keyboard and type password                            |
+---------------------------+-----------------------------------------------------------------+
| GET TEXT FROM CLIPBOARD   |  Récupère le texte présent dans le presse papier                |
+---------------------------+-----------------------------------------------------------------+
| KEYBOARD SHORTCUT         |  Simulate keyboard interactions                                 |
+---------------------------+-----------------------------------------------------------------+

**Contrôle chaine de caractères** 	

+---------------------------+-----------------------------------------------------------------+
| CLICK ON WORD             |  Detect the word on the screen and click on it                  |
+---------------------------+-----------------------------------------------------------------+
| DOUBLE CLICK ON WORD      |  Detect the word on the screen and double click on it           |
+---------------------------+-----------------------------------------------------------------+
| RIGHT CLICK ON WORD       |  Detect the word on the screen and right click on it            |
+---------------------------+-----------------------------------------------------------------+
| WAIT WORD                 |  Search the word until it appears                               |
+---------------------------+-----------------------------------------------------------------+
| WAIT AND CLICK ON WORD    |  Search the word until it appears and click on it               |
+---------------------------+-----------------------------------------------------------------+	
 
**Contrôle d'images**

+---------------------------+----------------------------------------------------------------------------+
| CLICK ON IMAGE            |  Detect the visual pattern on the screen and click on it                   |
+---------------------------+----------------------------------------------------------------------------+
| DOUBLE CLICK ON IMAGE     |  Detect the visual pattern on the screen and double click on it            |
+---------------------------+----------------------------------------------------------------------------+
| RIGHT CLICK ON IMAGE      |  Detect the visual pattern on the screen and right click on it             |
+---------------------------+----------------------------------------------------------------------------+
| WAIT IMAGE                |  Search the visual pattern until the image appears                         |
+---------------------------+----------------------------------------------------------------------------+
| WAIT AND CLICK ON IMAGE   |  Search the visual pattern until the image appears and click on it         |
+---------------------------+----------------------------------------------------------------------------+
| HOVER MOUSE ON            |  Detect the visual pattern on the screen and mouve the cursor on it        |
+---------------------------+----------------------------------------------------------------------------+
| DRAG IMAGE AND DROP TO    |  Detect the visual pattern on the screen and drop it to the position (x,y) |
+---------------------------+----------------------------------------------------------------------------+

.. image:: /_static/images/client_assistant/aa_app_steps1.png

.. image:: /_static/images/client_assistant/aa_app_steps2.png

.. image:: /_static/images/client_assistant/aa_app_steps3.png

.. image:: /_static/images/client_assistant/aa_app_img1.png

.. image:: /_static/images/client_assistant/aa_app_img2.png

.. image:: /_static/images/client_assistant/aa_app_img3.png

.. image:: /_static/images/client_assistant/aa-app-clipboard.png

.. image:: /_static/images/client_assistant/aa_app_img4.png

.. image:: /_static/images/client_assistant/aa_app_word1.png

.. image:: /_static/images/client_assistant/aa_app_word2.png

.. image:: /_static/images/client_assistant/aa_app_mouse.png


Web
~~~

Liste des actions disponibles:

**Contrôle navigateur** 

+---------------------------+-----------------------------------------------------------------+
| OPEN BROWSER              |  Ouvre le navigateur et charge l'url spécifié                   |
+---------------------------+-----------------------------------------------------------------+
| CLOSE BROWSER             |  Ferme le navigateur                                            |
+---------------------------+-----------------------------------------------------------------+
| MAXIMIZE BROWSER          |  Aggrandis la fenêtre du navigateur                             |
+---------------------------+-----------------------------------------------------------------+		
 
**Actions de navigation**	

+---------------------------+-----------------------------------------------------------------+
| REFRESH PAGE              |  Raffraichissement de la page                                   |
+---------------------------+-----------------------------------------------------------------+
| GO BACK                   |  Retour arrière                                                 |
+---------------------------+-----------------------------------------------------------------+
| GO FORWARD                |  Go forward                                                     |
+---------------------------+-----------------------------------------------------------------+
| ACCEPT ALERT              |  Valide l'alerte javascript                                     |
+---------------------------+-----------------------------------------------------------------+
| DISMISS ALERT             |  Dismiss the javascript alert                                   |
+---------------------------+-----------------------------------------------------------------+
| CLOSE WINDOW              |  Ferme la fenêtre courante                                      |
+---------------------------+-----------------------------------------------------------------+
| SWITCH TO NEXT WINDOW     |  Bascule sur la fenêtre suivante                                |
+---------------------------+-----------------------------------------------------------------+
| SWITCH TO FRAME           |  Bascule sur la frame suivante                                  |
+---------------------------+-----------------------------------------------------------------+

**Actions sur les élements html**

+--------------------------------+----------------------------------------------------------------------+
| WAIT HTML ELEMENT              | Wait html element to appear on the page                              |
+--------------------------------+----------------------------------------------------------------------+
| WAIT AND CLICK ON HTML ELEMENT | Wait html element to appear on the page and click on it              |
+--------------------------------+----------------------------------------------------------------------+
| HOVER ON HTML ELEMENT          | Déplace le curseur de la souris sur un élement HTML précis           |
+--------------------------------+----------------------------------------------------------------------+
| CLICK ON HTML ELEMENT          | Clic sur un élément HTML précis                                      | 
+--------------------------------+----------------------------------------------------------------------+
| DOUBLE CLICK ON HTML ELEMENT   | Double clic sur un élement HTML précis                               |
+--------------------------------+----------------------------------------------------------------------+
| CLEAR TEXT ON HTML ELEMENT     | Clear the text on the html element                                   |
+--------------------------------+----------------------------------------------------------------------+
| SELECT ITEM BY TEXT            | Select item according to the text (for combolist or list)            |
+--------------------------------+----------------------------------------------------------------------+
| SELECT ITEM BY VALUE           | Select item according to the value attribute (for combolist or list) |
+--------------------------------+----------------------------------------------------------------------+

**Récupération de texte** 

+----------------------------+-----------------------------------------------------------------+
| GET TEXT ALERT             |  Récupère le texte d'un message alerte javascript               |
+----------------------------+-----------------------------------------------------------------+
| GET TEXT FROM HTML ELEMENT |  Récupère le texte un élement html précis                       |
+----------------------------+-----------------------------------------------------------------+
| GET PAGE TITLE             |  Récupère le titre de la page                                   |
+----------------------------+-----------------------------------------------------------------+
| GET PAGE URL               |  Récupère l'url de la page                                      |
+----------------------------+-----------------------------------------------------------------+
| GET PAGE CODE SOURCE       |  Récupère le code source la page                                |
+----------------------------+-----------------------------------------------------------------+			

**Simulation clavier** 	

+---------------------------+-----------------------------------------------------------------+
| TYPE KEYBOARD SHORTCUT    |  Envoi un raccourci clavier sur un élement HTML précis          |
+---------------------------+-----------------------------------------------------------------+
| TYPE TEXT ON HTML ELEMENT |  Envoi du texte sur un élement HTML précis                      |
+---------------------------+-----------------------------------------------------------------+	

.. image:: /_static/images/client_assistant/aa_web_step1.png

.. image:: /_static/images/client_assistant/aa_web_step3.png

Mobile
~~~~~~

Liste des actions disponibles:

**Contrôle du mobile**
	
+---------------------------+-----------------------------------------------------------------+
| WAKE UP AND UNLOCK        |  Réveil et débloque le mobile                                   |
+---------------------------+-----------------------------------------------------------------+
| REBOOT                    |  Redémarrage du téléphone                                       |
+---------------------------+-----------------------------------------------------------------+
| SLEEP                     |  Mise en veille                                                 |
+---------------------------+-----------------------------------------------------------------+

**Textes** 	

+---------------------------+-----------------------------------------------------------------+
| TYPE SHORTCUT             |  Simule un raccourci                                            |
+---------------------------+-----------------------------------------------------------------+
| TYPE TEXT ON XML ELEMENT  |  Envoi du texte sur un élement précis de l'interface            |
+---------------------------+-----------------------------------------------------------------+
| GET TEXT FROM XML ELEMENT |  Récupère le texte d'un élement précis de l'interface           |
+---------------------------+-----------------------------------------------------------------+
 
**Contrôles des élements XML**

+-------------------------------+--------------------------------------------------------------------------------+
| CLEAR XML ELEMENT             |  Supprime le texte d'un élement précis de l'interface                          |
+-------------------------------+--------------------------------------------------------------------------------+
| CLICK ON XML ELEMENT          |  Clic sur un élement précis de l'interface                                     |
+-------------------------------+--------------------------------------------------------------------------------+
| LONG CLICK ON XML ELEMENT     |  Clic longue durée sur un élement précis de l'interface                        |
+-------------------------------+--------------------------------------------------------------------------------+
| WAIT AND CLICK ON XML ELEMENT |  Attend l'apparition d'un élement précis de l'interface et clic dessus         |
+-------------------------------+--------------------------------------------------------------------------------+		
 
**Tap sur l'écran** 

+---------------------------+-----------------------------------------------------------------+
| CLICK TO POSITION         |  Clic sur la position x,y                                       |
+---------------------------+-----------------------------------------------------------------+
| DRAG FROM POSITION        |  Drag from position x1,y1 to x2,y2                              |
+---------------------------+-----------------------------------------------------------------+
| SWIPE FROM POSITION       |  Swipe from position x1,y1 to x2,y2                             |
+---------------------------+-----------------------------------------------------------------+

.. image:: /_static/images/client_assistant/aa_mob_preview.png

.. image:: /_static/images/client_assistant/aa_mobile_step1.png

.. image:: /_static/images/client_assistant/aa_mob_steps.png