Les types de tests
============

La solution se base sur différents types de tests pour:
 - permettre la construction de tests avancés 
 - diminuer l'utilisation de script

.. image:: /_static/images/testlibrary/testing_approach.png
   
Test Abstract
-------------

Le ``test abstract`` (tax) permet d'écire un cas de test avec plusieurs étapes.
Ce format est orienté modélisation graphique donc ne nécessaite aucune connaissance en développement.

.. image:: /_static/images/testlibrary/tax.png

Test Unit
---------

Le ``test unit`` (tux) permet d'écire un cas de test avec plusieurs étapes.
Ce format est orienté développement.

.. image:: /_static/images/testlibrary/tux.png

.. note: ``Python`` est utilisé comme language de conception des tests.

Test Suite
---------

Le ``test suite`` (tsx) permet d'écire plusieurs cas de test avec plusieurs étapes.
Ce format est orienté développement.

.. image:: /_static/images/testlibrary/tsx.png

.. note: ``Python`` est utilisé comme language de conception des tests.

Test Plan
----------

Le ``test plan`` (tpx) permet d'écrire des scénarios de test.
La conception se réalise en imbriquant les tests `abstract`, `unit` et `suite`
Ce format de test necéssite aucune connaissance en développement.

.. image:: /_static/images/testlibrary/tpx.png

Test Global
----------

Le ``test global`` (tgx) permet d'écrire des campagnes de test.
La préparation des campagnes se réalise en important les tests `plans`.

.. image:: /_static/images/testlibrary/tgx.png

.. note:: il est aussi possible d'importer les autres types de tests.

	
	