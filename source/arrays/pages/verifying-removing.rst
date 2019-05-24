==================================
8. Verificando e Removendo Valores
==================================

8.1 Verificando Nulidade
------------------------

Para verificar a existência de uma chave no array, você pode utilizar o método ``isset()``.

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem' => 'ipsum', 'dolor' => 'sit']);

   var_dump($arrays->isset('lorem')); // bool(true)
   var_dump($arrays->isset('ipsum')); // bool(false)

.. hint::

   Em todos os métodos dessa página, é possível aplicar o uso da notação de ponto,
   explicada na seção 5, como no exemplo abaixo:

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays([
      'lorem' => [
         'ipsum' => [
            'dolor' => [
               'sit' => 'amet'
            ]
         ],
      ]
   ]);

   var_dump($arrays->isset('lorem.ipsum.dolor.sit'));     // bool(true)
   var_dump($arrays['lorem.ipsum.dolor']->isset('sit')); // bool(true)

   var_dump($arrays->isset('lorem.ipsum.amet'));       // bool(false)
   var_dump($arrays['lorem.ipsum']->isset('amet'));   // bool(false)

Caso queira executar a lógica inversa, você pode utilizar o método ``noset()``.

.. code:: php

   var_dump($arrays->noset('lorem')); // bool(false)
   var_dump($arrays->noset('ipsum')); // bool(true)

8.2 Verificando Valores Vazios
------------------------------

Para verificar se uma chave do array é vazia, utilize o método ``empty()``.

Esse método equivale à utilização de ``!isset($arrays[$key]) || $arrays[$key] == false``.

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();

   $arrays['lorem'] = false;
   var_dump($arrays->empty('lorem')); //bool(true);

Para verificar se um valor não é vazio, você pode utilizar o método ``filled()``, que nada mais é
do que a negação do método anterior.

Esse método equivale à utilização de ``isset($arrays[$key]) && $arrays[$key] == true``.

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();

   $arrays['lorem'] = false;
   var_dump($arrays->filled('lorem')); //bool(false);

8.3 Removendo Valores
---------------------

Para remover um elemento do array utilize o método ``unset()``.

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays([  
      'lorem' => [
         'ipsum' => [
            'dolor' => [
               'sit' => 'amet'
            ]
         ],
      ]
   ]);

   echo $arrays; // {"lorem":{"ipsum":{"dolor":{"sit":"amet"}}}}

   $arrays->unset('lorem.ipsum.dolor');

   echo $arrays; // {"lorem":{"ipsum":[]}}
   