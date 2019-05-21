====================
2. Inserindo valores
====================

2.1 Push
--------

O método ``push`` é usado para adicionar (empurrar) um ou mais valores ao final do array

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem', 'ipsum', 'dolor']);
   $arrays->push('sit', 'amet', 'consectetur');
   print_r($arrays);

   /*
      Cajudev\Arrays Object
         (
            [length:Cajudev\Arrays:private] => 6
            [content:protected] => Array
               (
                  [0] => lorem
                  [1] => ipsum
                  [2] => dolor
                  [3] => sit
                  [4] => amet
                  [5] => consectetur
               )

         )
   */

2.2 Unshift
-----------

O método ``unshift`` é usado para adicionar (empurrar) um ou mais valores no início do array

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem', 'ipsum', 'dolor']);
   $arrays->unshift('sit', 'amet', 'consectetur');
   print_r($arrays);

   /*
      Cajudev\Arrays Object
         (
            [length:Cajudev\Arrays:private] => 6
            [content:protected] => Array
               (
                  [0] => sit
                  [1] => amet
                  [2] => consectetur
                  [3] => lorem
                  [4] => ipsum
                  [5] => dolor
               )
         )
   */

2.3 Set
-------

Esse método ``set`` é usado para associar uma chave à um valor.  Como primeiro argumento, deve ser
informado o valor, e os demais são as chaves. Ele também suporta a notação de ponto descrita na seção 5.

.. code:: php

   // adicionando o valor 'lorem' na chave 'ipsum'
   $arrays->set('lorem', 'ipsum');

   // adicionando o valor 'lorem' na chave 'ipsum > dolor'
   $arrays->set('lorem', 'ipsum', 'dolor');

   // adicionando o valor 'lorem' na chave 'ipsum > dolor > amet' e assim por diante.
   $arrays->set('lorem', 'ipsum', 'dolor', 'amet');

   // ou com a notação de ponto
   $arrays->set('lorem', 'ipsum.dolor.amet');