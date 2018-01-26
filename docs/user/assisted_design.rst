Conception assistée
===================

Le client lourd comporte un assistant qui permet de créer des tests sans avoir de connaissances en développement. 
On peut s'en servir pour:
 - Utiliser les fonctions basiques du framework
 - Exécuter des commandes systèmes (ssh)
 - Tester des applications avec un client lourd
 - Tester des applications web
 - Exécuter des actions sur un mobile Android

Le test se compose d'un enchaînement d'actions à réaliser.
L'assistant génère automatiquement un ``test unit`` ou un ``test suite``. 
Un test (script) existant peut être mis à jour depuis l'assistant aussi.

Pour ajouter une action dans l'assitant, il faut 
 - sélectionner l'action à réaliser 
 - la configurer
 - enregistrer l'action

 
L'assistant supporte nativement l'utilisation du cache. Il est donc possible 
de sauvegarder ou récupérer des valeurs depuis le cache.

.. image:: /_static/images/client_assistant/aa_basic_log.png

.. note:: Il est possible de mélanger les différents types d'actions.

.. important:: 
  L'assistant permet de générer des tests en mode automatique mais il est aussi possible d'ajouter son propre code à l'intérieur 
  avec l'action ``USERCODE``.

Onglet Framework
------------------

L'onglet ``framework`` permet d'utiliser les fonctions de base du framework de test.

Exemple de test réalisé avec l'assistant:
 1. Affiche le message "bonjour" dans le test
 2. Demande à l'utilisateur durant l'exécution son prénom et l'enregistre dans le cache avec la clé ``prenom``
 3. Affiche le prénom dans le log du test
 4. Vérifie depuis le cache si le prénom contient une valeur spécifique.

.. image:: /_static/images/client_assistant/aa_basic_test.png

Liste des actions disponibles:

.. note:: En rouge, les actions indispensables.

+--------------------+-----------------------------------------------------------------+
| ``LOG MESSAGE``    |  Affiche un message d'information durant l'exécution du test    |
+--------------------+-----------------------------------------------------------------+
| LOG WARNING        |  Affiche un message d'attention durant l'exécution du test      |
+--------------------+-----------------------------------------------------------------+
| ``SET VALUE``      |  Sauvegarde une donnée dans le cache                            |
+--------------------+-----------------------------------------------------------------+
| RESET CACHE        |  Vide complètement le cache                                     |
+--------------------+-----------------------------------------------------------------+
| USERCODE           |  Permet d'ajouter du code personnalisé dans le test             |
+--------------------+-----------------------------------------------------------------+
| WAIT DURING        |  Attend pendant xx secondes                                     |
+--------------------+-----------------------------------------------------------------+
| ``CHECK IF VALUE`` |  Vérifie si la value contient un texte spécifique               |
+--------------------+-----------------------------------------------------------------+
| ASK SOMETHING      |  Demande une valeur à l'utilisateur (mode interaction)          |
+--------------------+-----------------------------------------------------------------+

Onglet Système
-----------------

L'onglet ``système`` permet d'exécuter des commandes sur un serveur distant disponible via SSH.

Exemple de test réalisé avec l'assistant:
 1. Ouverture de la session ssh sur la machine distante 192.186.1.251
 2. Envoi du texte `su -`
 3. Attend de détecter le texte `Password:` à l'écran
 4. Demande à l'utilisateur le mot de passe root et le stocke dans le cache avec la clé `pwd`
 5. Envoi le mot de passe root en utilisant la valeur stockée dans le cache
 6. Attend de détecter à l'écran le prompt de connexion
 7. Ferme la connexion SSH.
 
.. image:: /_static/images/client_assistant/aa_sys_example.png

Liste des actions disponibles: 

.. note:: En rouge, les actions indispensables.

+------------------------+-----------------------------------------------------------------+
| ``OPEN SSH SESSION``   |  Ouvre une session SSH                                          |
+------------------------+-----------------------------------------------------------------+
| CLOSE SESSION          |  Ferme la session                                               |
+------------------------+-----------------------------------------------------------------+
| CLEAR SCREEN           |  Vide l'écran                                                   |
+------------------------+-----------------------------------------------------------------+
| ``SEND TEXT``          |  Envoi une chaîne de caractères                                 |
+------------------------+-----------------------------------------------------------------+
| SEND SHORTCUT          |  Envoi un raccourci clavier (pour interrompre une action)       |
+------------------------+-----------------------------------------------------------------+
| ``CHECKING IF SCREEN`` |  Vérifie si l'écran contient un texte spécifique                |
+------------------------+-----------------------------------------------------------------+

.. note:: L'utilisation de l'action ``OPEN SSH SESSION`` est obligatoire avant de pouvoir utiliser les autres disponibles.

Onglet Application
------------------

L'onglet ``application`` permet d'automatiser des applications riches en permettant:
 - de simuler le clavier
 - de simuler la souris
 - de rechercher des élements graphiques à l'écran
 - de rechercher du texte

.. warning:: un agent ``sikulix-server`` est nécessaire pour utiliser les actions.

Exemple de test réalisé avec l'assistant:
 1. Envoie le raccourci clavier `Win+R` pour ouvrir la fenêtre exécuter
 2. Écrit le texte `cmd`
 3. Envoie le raccourci clavier `Enter` pour ouvrir une fenêtre cmd.
 4. Attend de détecter l'icône de la fenêtre cmd
 5. Écrit le texte `cls & ver` pour afficher la version de Windows
 6. Envoie le raccourci clavier `Enter` pour valider
 7. Envoie le raccourci clavier `Ctrl+A` pour sélectionner le texte dans la fenêtre
 8. Envoie le raccourci clavier `Ctrl+C` pour copier le texte sélectionné dans le presse-papier
 9. Récupère le texte du presse papier et l'enregistre dans le cache
 10. Affiche le texte copié depuis le cache
 11. Écrit le texte `exit` dans la fenêtre cmd
 12. Envoie le raccourci clavier `Enter` pour fermer la fenêtre.

.. image:: /_static/images/client_assistant/aa_app_example.png

Liste des actions disponibles:

.. note:: En rouge, les actions indispensables.

**Contrôle de la souris** 	

+---------------------------+-----------------------------------------------------------------+
| ``CLICK ON POSITION``     |  Clic sur la position (x,y)                                     |
+---------------------------+-----------------------------------------------------------------+
| DOUBLE CLICK ON POSITION  |  Double clic sur la position (x,y)                              |
+---------------------------+-----------------------------------------------------------------+
| RIGHT CLICK ON POSITION   |  Clic droit sur la position (x,y)                               |
+---------------------------+-----------------------------------------------------------------+
| MOUSE WHEEL DOWN          |  Tourne la molette de la souris vers le bas                     |
+---------------------------+-----------------------------------------------------------------+
| MOUSE WHEEL UP            |  Tourne la molette de la souris vers le haut                    |
+---------------------------+-----------------------------------------------------------------+
| MOVE TO POSITION          |  Déplace le curseur sur la position (x,y)                       |
+---------------------------+-----------------------------------------------------------------+
 
**Contrôle du clavier** 	

+---------------------------+-----------------------------------------------------------------+
| ``TYPE TEXT``             |  Écrit du texte                                                 |
+---------------------------+-----------------------------------------------------------------+
| TYPE PATH                 |  Écrit du texte (à utiliser pour les chemins d'accès)           |
+---------------------------+-----------------------------------------------------------------+
| TYPE PASSWORD             |  Écrit du texte (à utiliser pour taper un mot de passe)         |
+---------------------------+-----------------------------------------------------------------+
| GET TEXT FROM CLIPBOARD   |  Récupère le texte présent dans le presse-papier                |
+---------------------------+-----------------------------------------------------------------+
| ``KEYBOARD SHORTCUT``     |  Permet de taper un raccourci clavier                           |
+---------------------------+-----------------------------------------------------------------+

**Contrôle chaîne de caractères** 	

+---------------------------+-----------------------------------------------------------------+
| CLICK ON WORD             |  Recherche un mot à l'écran et clic dessus                      |
+---------------------------+-----------------------------------------------------------------+
| DOUBLE CLICK ON WORD      |  Recherche un mot à l'écran et double-clic dessus               |
+---------------------------+-----------------------------------------------------------------+
| RIGHT CLICK ON WORD       |  Recherche un mot à l'écran et effectue un clic-droit dessus    |
+---------------------------+-----------------------------------------------------------------+
| WAIT WORD                 |  Recherche un mot jusqu'à ce qu'il apparaisse                   |
+---------------------------+-----------------------------------------------------------------+
| WAIT AND CLICK ON WORD    |  Recherche un mot jusqu'à ce qu'il apparaisse et clic dessus    |
+---------------------------+-----------------------------------------------------------------+	
 
**Contrôle d'images**

+-----------------------------+----------------------------------------------------------------------------+
| CLICK ON IMAGE              |  Recherche une image et clic dessus                                        |
+-----------------------------+----------------------------------------------------------------------------+
| DOUBLE CLICK ON IMAGE       |  Recherche une image et double-clic dessus                                 |
+-----------------------------+----------------------------------------------------------------------------+
| RIGHT CLICK ON IMAGE        |  Recherche une image et effectue un clic-droit dessus                      |
+-----------------------------+----------------------------------------------------------------------------+
| WAIT IMAGE                  |  Recherche une image jusqu'à la voir apparaître à l'écran                  |
+-----------------------------+----------------------------------------------------------------------------+
| ``WAIT AND CLICK ON IMAGE`` |  Recherche une image jusqu'à la voir apparaître à l'écran et clic dessus   |
+-----------------------------+----------------------------------------------------------------------------+
| HOVER MOUSE ON              |  Recherche une image et déplace le curseur de la souris dessus             |
+-----------------------------+----------------------------------------------------------------------------+
| DRAG IMAGE AND DROP TO      |  Recherche une image et effectue un drag and drop vers la position (x,y)   |
+-----------------------------+----------------------------------------------------------------------------+

Onglet Navigateur
----------------

L'onglet ``navigateur`` permet d'automatiser des applications web en permettant:
 - de piloter les navigateurs (firefox, internet explorer, chrome, edge)
 - de simuler le clavier

.. warning:: un agent ``selenium3-server`` ou ``selenium2-server`` est nécessaire pour utiliser les actions.

.. tip:: 
 Pour cliquer sur un élement HTML, il est conseillé d'utiliser systématiquement 
 la fonction ``WAIT VISIBLE AND CLICK ON HTML ELEMENT``.

Exemple de test réalisé avec l'assistant:
 1. Récupère depuis le cache le prénom et l'envoie dans l'élément HTML trouvé par le xpath
 2. Clic sur l'élément HTML trouvé par le xpath
 3. Recherche l'élément HTML trouvé par le xpath et clic dessus dès qu'il est visible à l'écran.
 
.. image:: /_static/images/client_assistant/aa_web_example.png

.. note:: 
  Il est possible d'ouvrir plusieurs navigateur en parallèle sur le même poste à définissant une nouvelle session.
  La nom se la session se définit sur l'action ``OPEN BROWSER``.
  Il faut ensuite utiliser l'action ``SWITCH TO SESSION`` pour changer de session.

Liste des actions disponibles:

.. note:: En rouge, les actions indispensables.

**Contrôle navigateur** 

+---------------------------+-----------------------------------------------------------------+
| ``OPEN BROWSER``          |  Ouvre le navigateur et charge l'url spécifié                   |
+---------------------------+-----------------------------------------------------------------+
| ``CLOSE BROWSER``        |  Ferme le navigateur                                            |
+---------------------------+-----------------------------------------------------------------+
| MAXIMIZE BROWSER          |  Aggrandit la fenêtre du navigateur                             |
+---------------------------+-----------------------------------------------------------------+		
 
**Actions de navigation**	

+---------------------------+-----------------------------------------------------------------+
| REFRESH PAGE              |  Rafraîchissement de la page                                    |
+---------------------------+-----------------------------------------------------------------+
| GO BACK                   |  Retour arrière                                                 |
+---------------------------+-----------------------------------------------------------------+
| GO FORWARD                |  Go forward                                                     |
+---------------------------+-----------------------------------------------------------------+
| ACCEPT ALERT              |  Valide l'alerte javascript                                     |
+---------------------------+-----------------------------------------------------------------+
| DISMISS ALERT             |  Dismiss the javascript alert                                   |
+---------------------------+-----------------------------------------------------------------+
| CLOSE CURRENT WINDOW      |  Ferme la fenêtre courante                                      |
+---------------------------+-----------------------------------------------------------------+
| SWITCH TO NEXT WINDOW     |  Bascule sur la fenêtre suivante                                |
+---------------------------+-----------------------------------------------------------------+
| SWITCH TO FRAME           |  Bascule sur la frame suivante                                  |
+---------------------------+-----------------------------------------------------------------+
| SWITCH TO SESSION         |  Bascule sur une autre session selenium                         |
+---------------------------+-----------------------------------------------------------------+
| SWITCH TO WINDOW          |  Bascule sur la frame suivante                                  |
+---------------------------+-----------------------------------------------------------------+

 
**Actions javascript**	

+------------------------------------+-----------------------------------------------------------------+
| EXECUTE JAVASCRIPT ON HTML ELEMENT |  Permet d'injecter du javascript script sur un élement html     |
+------------------------------------+-----------------------------------------------------------------+

**Actions sur les éléments html**

+-------------------------------------------+----------------------------------------------------------------------+
| WAIT HTML ELEMENT                         | Attend l'apparition d'un élément HTML précis                         |
+-------------------------------------------+----------------------------------------------------------------------+
| WAIT AND CLICK ON HTML ELEMENT            | Attend l'apparition d'un élément HTML précis et clic dessus          |
+-------------------------------------------+----------------------------------------------------------------------+
| WAIT VISIBLE HTML ELEMENT                 | Attend qu'un élément HTML soit visible à l'utilisateur               |
+-------------------------------------------+----------------------------------------------------------------------+
| WAIT NOT VISIBLE HTML ELEMENT             | Attend qu'un élément HTML ne soit pas visible à l'utilisateur        |
+-------------------------------------------+----------------------------------------------------------------------+
| ``WAIT VISIBLE AND CLICK ON HTML ELEMENT``| Attend qu'un élément HTML soit visible à l'utilisateur et clic dessus|
+-------------------------------------------+----------------------------------------------------------------------+
| HOVER ON HTML ELEMENT                     | Déplace le curseur de la souris sur un élement HTML précis           |
+-------------------------------------------+----------------------------------------------------------------------+
| CLICK ON HTML ELEMENT                     | Clic sur un élément HTML précis                                      | 
+-------------------------------------------+----------------------------------------------------------------------+
| DOUBLE CLICK ON HTML ELEMENT              | Double clic sur un élément HTML précis                               |
+-------------------------------------------+----------------------------------------------------------------------+
| CLEAR TEXT ON HTML ELEMENT                | Vide le texte sur un élément HTML précis                             |
+-------------------------------------------+----------------------------------------------------------------------+
| ``SELECT ITEM BY TEXT``                   |  Select item according to the text (for combolist or list)           |
+-------------------------------------------+----------------------------------------------------------------------+
| ``SELECT ITEM BY VALUE``                  | Select item according to the value attribute (for combolist or list) |
+-------------------------------------------+----------------------------------------------------------------------+

**Récupération de texte** 

+--------------------------------+-----------------------------------------------------------------+
| GET TEXT ALERT                 |  Récupère le texte d'un message alerte javascript               |
+--------------------------------+-----------------------------------------------------------------+
| ``GET TEXT FROM HTML ELEMENT`` |  Récupère le texte un élément html précis                       |
+--------------------------------+-----------------------------------------------------------------+
| GET PAGE TITLE                 |  Récupère le titre de la page                                   |
+--------------------------------+-----------------------------------------------------------------+
| GET PAGE URL                   |  Récupère l'url de la page                                      |
+--------------------------------+-----------------------------------------------------------------+
| GET PAGE CODE SOURCE           |  Récupère le code source la page                                |
+--------------------------------+-----------------------------------------------------------------+			

**Simulation clavier** 	

+-------------------------------+-----------------------------------------------------------------+
| TYPE KEYBOARD SHORTCUT        |  Envoie un raccourci clavier sur un élément HTML précis         |
+-------------------------------+-----------------------------------------------------------------+
| ``TYPE TEXT ON HTML ELEMENT`` |  Envoie du texte sur un élément HTML précis                     |
+-------------------------------+-----------------------------------------------------------------+	

Onglet Android
--------------

L'onglet ``android`` permet d'automatiser des applications mobiles en permettant:
 - de simuler le clavier
 - de simuler l'utilisation du doigts sur l'écran
 - de piloter le système et les applications 

.. warning:: un agent ``adb`` est nécessaire pour utiliser les actions.

Aperçu de l'agent

.. image:: /_static/images/client_assistant/aa_mob_preview.png

Exemple de test réalisé avec l'assistant:
 1. Réveille l'appareil
 2. Débloque l'appareil
 3. Clic sur le bouton `HOME`
 4. Arrête l'application
 5. Clic sur l'application `Play Store` pour l'ouvrir
 6. Attend que l'application s'ouvre et recherche le menu `APPS & GAMES`
 7. Clic sur le texte `ENTERTAINMENT`
 8. Clic sur le menu `MOVIES & TV`
 9. Attend pendant 5 secondes
 10. Recherche l'image
 11. Mise en veille de l'appareil.

.. image:: /_static/images/client_assistant/aa_sys_mobile.png

Liste des actions disponibles:

.. note:: En rouge, les actions indispensables.

**Contrôle du mobile**
	
+---------------------------+-----------------------------------------------------------------+
| ``WAKE UP AND UNLOCK``    |  Réveille et débloque l'appareil                                |
+---------------------------+-----------------------------------------------------------------+
| REBOOT                    |  Redémarrage de l'appareil                                      |
+---------------------------+-----------------------------------------------------------------+
| SLEEP                     |  Mise en veille                                                 |
+---------------------------+-----------------------------------------------------------------+

**Textes** 	

+------------------------------+-----------------------------------------------------------------+
| ``TYPE SHORTCUT``            |  Simule un raccourci                                            |
+------------------------------+-----------------------------------------------------------------+
| ``TYPE TEXT ON XML ELEMENT`` |  Envoie du texte sur un élément précis de l'interface           |
+------------------------------+-----------------------------------------------------------------+
| GET TEXT FROM XML ELEMENT    |  Récupère le texte d'un élément précis de l'interface           |
+------------------------------+-----------------------------------------------------------------+
 
**Contrôles des éléments XML**

+-----------------------------------+--------------------------------------------------------------------------------+
| CLEAR XML ELEMENT                 |  Supprime le texte d'un élément précis de l'interface                          |
+-----------------------------------+--------------------------------------------------------------------------------+
| CLICK ON XML ELEMENT              |  Clic sur un élément précis de l'interface                                     |
+-----------------------------------+--------------------------------------------------------------------------------+
| LONG CLICK ON XML ELEMENT         |  Clic longue-durée sur un élément précis de l'interface                        |
+-----------------------------------+--------------------------------------------------------------------------------+
| ``WAIT AND CLICK ON XML ELEMENT`` |  Attend l'apparition d'un élément précis de l'interface et clic dessus         |
+-----------------------------------+--------------------------------------------------------------------------------+		
 
**Tap sur l'écran** 

+---------------------------+-----------------------------------------------------------------+
| ``CLICK TO POSITION``     |  Clic sur la position x,y                                       |
+---------------------------+-----------------------------------------------------------------+
| DRAG FROM POSITION        |  Drag depuis la position x1,y1 vers x2,y2                       |
+---------------------------+-----------------------------------------------------------------+
| SWIPE FROM POSITION       |  Swipe depuis la position x1,y1 vers x2,y2                      |
+---------------------------+-----------------------------------------------------------------+
