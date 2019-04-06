==================================
7. Verificando e Removendo Valores
==================================

7.1 Verificando Nulidade
------------------------

Para verificar a existência de uma chave no array, você pode utilizar o método ``isset``.

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays(['lorem' => 'ipsum', 'dolor' => 'sit']);

   var_dump($arrays->isset('lorem')); // bool(true)
   var_dump($arrays->isset('ipsum')); // bool(false)

.. hint::

   Em todos os métodos dessa página, é possível aplicar o uso da notação de ponto,
   explicada na seção 5, como no exemplo abaixo:

.. code-block:: php

   use Cajudev\Classes\Arrays;

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

Caso queira executar a lógica inversa, você pode utilizar o método ``noset``.

.. code-block:: php

   var_dump($arrays->noset('lorem')); // bool(false)
   var_dump($arrays->noset('ipsum')); // bool(true)

7.2 Verificando Valores Vazios
------------------------------

Para verificar se uma chave do array é vazia, utilize o método ``empty``.
Esse método equivale a utilização de ``$arrays->noset($key) || $arrays->get($key) == false``.

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays();

   $arrays['lorem'] = false;
   var_dump($arrays->empty('lorem')); //bool(true);

Para verificar se um valor não é vazio, você pode utilizar o método filled, que nada mais é
do que a negação do método anterior, equivalendo a ``$arrays->isset($key) && $arrays->get($key) == true``.

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays();

   $arrays['lorem'] = false;
   var_dump($arrays->filled('lorem')); //bool(false);