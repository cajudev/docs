==================================
6. Verificando e Removendo Valores
==================================

6.1 Verificando Nulidade
------------------------

Para verificar a existência de uma chave no array, você pode utilizar o método ``isset``.

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays();
   $arrays->apush( //lembre-se -> key, value, key, value, etc
        'lorem' , 'ipsum',
        'dolor' , 'sit',
        'amet'
    );
   var_dump($arrays->isset('lorem')); // bool(true)
   var_dump($arrays->isset('ipsum')); // bool(false)

Caso queira executar a lógica inversa, você pode utilizar o método ``noset``.

.. code-block:: php

   var_dump($arrays->noset('lorem')); // bool(false)
   var_dump($arrays->noset('ipsum')); // bool(true)

6.2 Verificando Valores Vazios
------------------------------

Para verificar se uma chave do array é vazia, utilize o método ``empty``.
Esse método equivale a utilização de ``$arrays->noset($key) || $arrays->get($key) == false``.

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays();

   $arrays->apush('lorem', 0);
   var_dump($arrays->empty('lorem')); //bool(true);

Para verificar se um valor não é vazio, você pode utilizar o método filled, que nada mais é
do que a negação do método anterior, equivalendo a ``$arrays->isset($key) && $arrays->get($key) == true``.

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays();

   $arrays->apush('lorem', 0);
   var_dump($arrays->filled('lorem')); //bool(false);