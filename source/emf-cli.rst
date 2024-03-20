===========
EMF CLI
===========

Client documentation page.


Titre de niveau 2
-----------------

Titre de niveau 3
~~~~~~~~~~~~~~~~~

Un autre titre de niveau 2
--------------------------



Voici du texte en *italique*, en **gras**, et voici du ``code inline``.


Pour faire un lien inline c'est simple :
lien vers le `liens de la doc <https://github.com/easy-model-fusion/docs/>`_




Liste à puce :

* Ceci est une liste
* un autre élément

  * Une sous-liste
  * notez bien le saut de ligne avec la liste principale,
    ça ne marchera pas si vous l'oubliez !

* un dernier élément




Liste ordonnée :

1. Un
2. Deux
3. Trois




Voici comment faire un bloc de code simple ::

   Ceci est un bloc de code. Il est créé grâce aux doubles deux-points.





On peut aussi définir un bloc de code avec une syntaxe
plus explicite, grâce à laquelle on peut indiquer à Sphinx dans quel
langage il est rédigé, ce qui lui permettra d'activer la coloration
syntaxique :

.. code-block:: python

   #!/usr/bin/env python

   print("Ceci est un bloc de code Python\n")




.. NOTE::

   Ceci est une note.

.. WARNING::

   Ceci est un avertissement !

.. IMPORTANT::

   Ceci est important !


+-----------+-----------+-----------+
| Heading 1 | Heading 2 | Heading 3 |
+===========+===========+===========+
| Hello     | World     |           |
+-----------+-----------+-----------+
| foo       |                       |
+-----------+          bar          |
| baz       |                       |
+-----------+-----------------------+



.. csv-table:: Title!
        :header: "Produit", "Quantité", "Description"
        :widths: 15, 10, 30

        "Albatross", 2.99, "On a stick!"
        "Crunchy Frog", 1.49, "If we took the bones out, it wouldn't be
         crunchy, now would it?"
        "Gannet Ripple", 1.99, "On a stick!"