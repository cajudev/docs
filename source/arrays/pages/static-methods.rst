=====================
15. Métodos Estáticos
=====================

15.1 isArrays
-------------

Verifica se dado objeto é uma instância da classe Arrays ou que extenda dela

.. code:: php

   use Cajudev\Arrays;

   Arrays::isArrays(new Arrays()); // true

   Arrays::isArrays(10); // false

15.2 Combine
-------------

Combina dois arrays em um novo objeto, utilizando o primeiro para chaves e o segundo para valores.
Ambos os argumentos podem ser simples arrays ou objetos dessa classe.

.. code:: php

   use Cajudev\Arrays;

   $array = ['lorem', 'ipsum', 'dolor'];

   $arrays = new Arrays([1, 2, 3]);

   $result = Arrays::combine($array, $arrays);

   echo $result; // {"lorem":1,"ipsum":2,"dolor":3}

