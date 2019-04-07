=======================
9. Métodos de Uso Geral
=======================

9.1 Count
---------

O método count retorna a quantidade de elementos do array

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', ['dolor' => ['sit' => 'amet']]);

   echo $arrays->count(); // 3

Caso o argumento $mode seja informado como ``COUNT_RECURSIVE`` ou ``1``, o retorno será
a quantidade total de elementos e não apenas do nível atual.

.. code-block:: php

   echo $arrays->count(1); // 5

9.2 Last
---------

Retorna o último elemento de um array (reinicia o ponteiro)

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');

   echo $arrays->last(); // 'dolor'

9.3 Shift
---------

Remove o primeiro elemento de um array (reinicia o ponteiro)

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');
   $arrays->shift();

   echo $arrays; // ["ipsum","dolor"]

9.4 Pop
-------

Remove o último elemento de um array (reinicia o ponteiro)

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');
   $arrays->pop();

   echo $arrays; // ["lorem","ipsum"]