Dépannage
================

Code erreurs
------------

**Erreurs liées au moteur d'exécution**

+----------------------+-------------------------------------------------------------+
| Code erreur          | Description                                                 |
+----------------------+-------------------------------------------------------------+
| ERR_TE_000           | Erreur générique au niveau de l'exécution du test           |
+----------------------+-------------------------------------------------------------+
| ERR_TE_001           | Erreur générique au niveau de l'exécution du cas de test    |
+----------------------+-------------------------------------------------------------+
| ERR_TE_500           | Erreur générique au niveau de l'exécution du script         |
+----------------------+-------------------------------------------------------------+

**Erreurs liées aux étapes de tests**

+----------------------+-------------------------------------------------------------+
| Code erreur          | Description                                                 |
+----------------------+-------------------------------------------------------------+
| ERR_STP_001          | L'étape est déjà démarrée, la fonction `start()`            |
|                      | est appelée plusieurs fois dans le test pour une même étape.|
+----------------------+-------------------------------------------------------------+
| ERR_STP_005          | Le testeur essaye de positionner un résultat sur l'étape    |
|                      | alors que la fonction `start()` n'a pas été utilisée en amont|
+----------------------+-------------------------------------------------------------+

**Erreurs liées à l'accès aux paramètres de test**

+----------------------+--------------------------------------------------------------------------+
| Code erreur          | Description                                                              |
+----------------------+--------------------------------------------------------------------------+
| ERR_PRO_004          | Le paramètre demandé dans la fonction `input` n'existe pas dans le test  |
+----------------------+--------------------------------------------------------------------------+

FAQ
---

Impossible de générer la description HTML d'un test
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

L'impossibilité de générer la description d'un test peut venir de plusiers choses:
 - la version des adaptateurs ou librairies utilisés dans le test n'est pas la bonne
 - une erreur de syntaxe existe dans un test
 - un appel au cache est utilisé dans la définition des étapes de tests
