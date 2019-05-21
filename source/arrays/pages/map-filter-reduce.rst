11. Map, Filter e Reduce
========================

11.1 Map
--------

O método ``map``, permite aplicar uma função callback em todos os elementos do array. Sua implementação
especial permite alterar tanto valores, quanto suas chaves.

.. code:: php

   $arrays = new Arrays(['lorem', 'ipsum', 'dolor']);
   $arrays->map(function($key, $value) {
      return [$key + 10, strtoupper($value)];
   });

   print_r($arrays);

   /*
   Cajudev\Arrays Object
      (
         [content:Cajudev\Arrays:private] => Array
            (
               [10] => LOREM
               [11] => IPSUM
               [12] => DOLOR
            )
         [length:Cajudev\Arrays:private] => 3
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
         [content:Cajudev\Arrays:private] => Array
            (
               [0] => 1
               [1] => 2
               [2] => 3
               [3] => 4
            )

         [length:Cajudev\Arrays:private] => 4
      )
   */

11.3 Reduce
-----------

O método ``reduce`` permite reduzir o array em um único valor. Ele recebe por parâmetro uma função callback a ser executada,
e repassa sempre dois argumentos, o primeiro é o valor anterior e o segundo é o valor atual. Diferente dos métodos anteriores,
que alteram o conteúdo interno do array, esse método apenas retorna o resultado.

.. code:: php

   $arrays = new Arrays([1, 2, 3, 4]);
   
   $result = $arrays->reduce(function($a, $b) {
      return $a + $b;
   });

   echo $result; // 10