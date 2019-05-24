11. Map, Filter e Reduce
========================

11.1 Map
--------

O método ``map``, permite aplicar uma função callback em todos os elementos do array. Sua implementação
especial permite alterar tanto valores, quanto suas chaves.

O retorno esperado é um novo array, sendo o primeiro elemento a chave e o segundo o valor.

.. code:: php

   $arrays = new Arrays(['lorem', 'ipsum', 'dolor']);
   $arrays->map(function($key, $value) {
      return [$key + 10, strtoupper($value)];
   });

   print_r($arrays);

   /*
   Cajudev\Arrays Object
      (
         [content:Cajudev\Arrays:protected] => Array
            (
               [10] => LOREM
               [11] => IPSUM
               [12] => DOLOR
            )
         [backup:protected] => 
         [length:protected] => 3
      )
   */

11.2 Filter
-----------

O método ``filter`` permite filtrar os elementos do array através de uma função callback. A função receberá valor e chave respectivamente.

.. code:: php

   $arrays = new Arrays([1, 2, 3, 4, 5, 6, 7, 8, 9]);

   $arrays->filter(function($value, $key) {
      return $value < 5;
   });

   print_r($arrays);

   /*
   Cajudev\Arrays Object
      (
         [content:Cajudev\Arrays:protected] => Array
            (
               [0] => 1
               [1] => 2
               [2] => 3
               [3] => 4
            )

         [backup:protected] => 
         [length:protected] => 4
      )
   */

11.3 Reduce
-----------

O método ``reduce`` permite reduzir o array em um único valor. Ele recebe por parâmetro uma função callback a ser executada,
e repassa sempre dois argumentos, o primeiro é o valor anterior e o segundo é o valor atual.

Diferente do tradicional, o valor inicial fornecido será o **primeiro elemento do array** e não ``null`` como o de costume.

.. code:: php

   $arrays = new Arrays([1, 2, 3, 4]);
   
   $result = $arrays->reduce(function($a, $b) {
      return $a + $b;
   });

   echo $result; // 10