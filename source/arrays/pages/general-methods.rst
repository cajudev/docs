=======================
13. Métodos de Uso Geral
=======================

13.1 Last
---------

Retorna o último elemento de um array (reinicia o ponteiro)

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');

   echo $arrays->last(); // 'dolor'

13.2 Shift
---------

Remove o primeiro elemento de um array (reinicia o ponteiro)

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');
   $arrays->shift();

   echo $arrays; // ["ipsum","dolor"]

13.3 Pop
-------

Remove o último elemento de um array (reinicia o ponteiro)

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');
   $arrays->pop();

   echo $arrays; // ["lorem","ipsum"]

13.4 Count ``(Deprecated)``
----------

O método count retorna a quantidade de elementos do array.

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', ['dolor' => ['sit' => 'amet']]);

   echo $arrays->count(); // 3