D�pannage
================

Code erreurs
------------

**Erreurs li�s au moteur d'ex�cution**

+----------------------+-------------------------------------------------------------+
| Code erreur          | Description                                                 |
+----------------------+-------------------------------------------------------------+
| ERR_TE_000           | Erreur g�n�rique au niveau de l'ex�cution du test           |
+----------------------+-------------------------------------------------------------+
| ERR_TE_001           | Erreur g�n�rique au niveau de l'ex�cution du cas de test    |
+----------------------+-------------------------------------------------------------+
| ERR_TE_500           | Erreur g�n�rique au niveau de l'ex�cution du script         |
+----------------------+-------------------------------------------------------------+

**Erreurs li�s aux �tapes de tests**

+----------------------+-------------------------------------------------------------+
| Code erreur          | Description                                                 |
+----------------------+-------------------------------------------------------------+
| ERR_STP_001          | L'�tape est d�j� d�marr�e, la fonction `start()`            |
|                      | est appel� plusieurs fois dans le test pour une m�me �tape. |
+----------------------+-------------------------------------------------------------+
| ERR_STP_005          | Le testeur essaye de positionner un r�sultat sur l'�tape    |
|                      | alors que la fonction `start()` n'a pas �t� utilis� en amont|
+----------------------+-------------------------------------------------------------+

**Erreurs li�s � l'acc�s aux param�tres de test**

+----------------------+--------------------------------------------------------------------------+
| Code erreur          | Description                                                              |
+----------------------+--------------------------------------------------------------------------+
| ERR_PRO_004          | Le param�tre demand� dans la fonction `input` n'existe pas dans le test  |
+----------------------+--------------------------------------------------------------------------+


FAQ
---

Impossible de g�n�rer la description HTML d'un test
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

L'impossibilit� de g�n�rer un d�signe pour un test peut venir de plusiers choses:
 - la version des adaptateurs ou librairies utilis�s dans le test n'est pas bon
 - une erreur de syntaxe existe dans un test
 - un appel au cache est utilis� dans la d�finition des �tapes de tests
 