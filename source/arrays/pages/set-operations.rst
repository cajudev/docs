===========================
13. Operações com Conjuntos
===========================

Todos os métodos descritos nesta seção seguem a seguinte lógica: Cada index do objeto equivale à um conjunto.

O que significa que o objeto abaixo...

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays([
       [1, 2, 3],
       [3, 4, 5],
   ]);

... possui dois conjuntos de números inteiros.

13.1 União
----------

O método ``union()`` realiza a união entre todos os conjuntos do objeto. Valores repetidos são removidos.

.. code:: php

   $arrays->union(); // [1, 2, 3, 4, 5]

13.2 Diferença
--------------

O método ``diff()`` realiza a diferença entre todos os conjuntos do objeto. 
A ordem dos conjuntos altera diretamente o valor final.

.. code:: php

   $arrays = new Arrays([
      [1, 2, 3],
      [3, 4, 5],
   ]);

   $arrays->diff(); // [1, 2]

   $arrays = new Arrays([
      [3, 4, 5],
      [1, 2, 3],
   ]);

   $arrays->diff(); // [4, 5]

13.3 Intersecção
----------------

O método ``intersect()`` realiza a intersecção entre todos os conjuntos do objeto.

.. code:: php

   $arrays = new Arrays([
      [1, 2, 3, 4],
      [3, 4, 5, 6],
   ]);

   $arrays->intersect(); // [3, 4]

13.4 Produto cartesiano
-----------------------

O método ``cartesian()`` realiza o produto cartesiano entre todos os conjuntos do objeto.

.. code:: php

   $arrays = new Arrays([
      [1, 2, 3],
      [3, 4, 5],
   ]);

   $arrays->cartesian(); // [[1,3], [1,4], [1,5], [2,3], [2,4], [2,5], [3,3], [3,4], [3,5]]