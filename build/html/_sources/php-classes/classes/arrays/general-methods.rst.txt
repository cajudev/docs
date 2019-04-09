=======================
9. Métodos de Uso Geral
=======================

9.1 Count
---------

O método count retorna a quantidade de elementos do array

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', ['dolor' => ['sit' => 'amet']]);

   echo $arrays->count(); // 3

Caso o argumento $mode seja informado como ``COUNT_RECURSIVE`` ou ``1``, o retorno será
a quantidade total de elementos e não apenas do nível atual.

.. code-block:: php

   echo $arrays->count(1); // 5

9.2 CountOne
------------

Conta a quantidade de elementos de um array, salvando essa informação internamente
na classe e retornando sempre que for chamado.

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem', 'ipsum', 'dolor']);
   $arrays->countOne();

   print_r($arrays);

   /*
       Cajudev\Arrays Object
        (
            [content:protected] => Array
                (
                    [0] => lorem
                    [1] => ipsum
                    [2] => dolor
                )

            [length:Cajudev\Arrays:private] => 3
        )
   */

Útil para ser usado em loops, sem a necessidade de criar variáveis

.. code-block:: php

   while ($foo < $arrays->countOne()) {
       // comandos
   }

9.3 Last
---------

Retorna o último elemento de um array (reinicia o ponteiro)

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');

   echo $arrays->last(); // 'dolor'

9.4 Shift
---------

Remove o primeiro elemento de um array (reinicia o ponteiro)

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');
   $arrays->shift();

   echo $arrays; // ["ipsum","dolor"]

9.5 Pop
-------

Remove o último elemento de um array (reinicia o ponteiro)

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');
   $arrays->pop();

   echo $arrays; // ["lorem","ipsum"]