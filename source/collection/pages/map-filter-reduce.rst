12. Map, Filter e Reduce
========================

12.1 Map
--------

O método ``map``, permite aplicar uma função callback em todos os elementos do array. Sua implementação
especial permite alterar tanto valores, quanto suas chaves.

.. code:: php

   $collection = new Collection(['lorem', 'ipsum', 'dolor']);
   $map = $collection->map(function($key, $value) {
      return [$key + 10 => strtoupper($value)];
   });

   print_r($map);

   /*
   Cajudev\Collection Object
      (
         [content:Cajudev\Collection:protected] => Array
            (
               [10] => LOREM
               [12] => IPSUM
               [12] => DOLOR
            )
         [length:protected] => 3
      )
   */

12.2 Filter
-----------

O método ``filter`` permite filtrar os elementos do array através de uma função callback.

.. code:: php

   $collection = new Collection([1, 2, 3, 4, 5, 6, 7, 8, 9]);

   $filter = $collection->filter(function($key, $value) {
      return $value < 5;
   });

   print_r($filter);

   /*
   Cajudev\Collection Object
      (
         [content:Cajudev\Collection:protected] => Array
            (
               [0] => 1
               [1] => 2
               [2] => 3
               [3] => 4
            )

         [length:protected] => 4
      )
   */

12.3 Reduce
-----------

O método ``reduce`` permite reduzir o objeto em um único valor. Ele recebe por parâmetro uma função callback a ser executada,
e repassa sempre dois argumentos, o primeiro é o valor anterior e o segundo é o valor atual.

Diferente do tradicional, o valor inicial fornecido será o **primeiro elemento do array** e não ``null`` como o de costume.

.. code:: php

   $collection = new Collection([1, 2, 3, 4]);
   
   $result = $collection->reduce(function($a, $b) {
      return $a + $b;
   });

   echo $result; // 10