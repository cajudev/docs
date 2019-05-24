=======================
13. Métodos de Uso Geral
=======================

13.1 Last
---------

Retorna o último elemento de um array (reinicia o ponteiro)

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');

   echo $arrays->last(); // 'dolor'

13.2 Shift
---------

Remove o primeiro elemento de um array (reinicia o ponteiro)

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');
   $arrays->shift();

   echo $arrays; // ["ipsum","dolor"]

13.3 Pop
-------

Remove o último elemento de um array (reinicia o ponteiro)

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');
   $arrays->pop();

   echo $arrays; // ["lorem","ipsum"]

13.4 Count ``(Deprecated)``
----------

Retorna a quantidade de elementos do array.

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', ['dolor' => ['sit' => 'amet']]);

   echo $arrays->count(); // 3

13.5 Keys
---------

Retorna um novo objeto contento as chaves do objeto atual

.. code:: php

    use Cajudev\Arrays;

    $arrays = new Arrays(['three' => 3, 'eight' => 8, 'two' => 2]);

    $keys = $arrays->keys();

    echo $keys; // ["three", "eight", "two"]

13.6 Values
-----------

Retorna um novo objeto contento os valores do objeto atual

.. code:: php

    use Cajudev\Arrays;

    $arrays = new Arrays(['three' => 3, 'eight' => 8, 'two' => 2]);

    $values = $arrays->values();

    echo $values; // [3, 8, 2]

13.7 Chunk
----------

Quebra o array em partes iguais. Caso receba ``true`` como segundo parâmetro preservará as chaves do array.

.. code:: php

    use Cajudev\Arrays;

    $arrays = new Arrays([1, 2, 3, 4, 5]);

    $arrays->chunk(2);

    print_r($arrays);

    /*
    Cajudev\Arrays Object
        (
            [content:Cajudev\Arrays:protected] => Array
                (
                    [0] => Array
                        (
                            [0] => 1
                            [1] => 2
                        )
                    [1] => Array
                        (
                            [0] => 3
                            [1] => 4
                        )
                    [2] => Array
                        (
                            [0] => 5
                        )
                )
            [backup:protected] => 
            [length:protected] => 3
        )
    */

13.8 Join
----------

Junta os elementos do array em uma string.

.. code:: php

    use Cajudev\Arrays;

    $arrays = new Arrays([1, 2, 3, 4, 5]);

    $result = $arrays->join('-');

    echo $result; // 1-2-3-4-5

13.9 Column
-----------

Retorna um objeto contento os valores da coluna informada.

.. code:: php

    use Cajudev\Arrays;

    $arrays = new Arrays();

    $arrays[] = ['lorem' => '1234', 'ipsum' => 8000];
    $arrays[] = ['lorem' => '4321', 'ipsum' => 1500];
    $arrays[] = ['lorem' => '9999', 'ipsum' => 0015];
    $arrays[] = ['lorem' => '1111', 'ipsum' => 3315];

    echo $arrays->column('lorem'); // ["1234","4321","9999","1111"]

13.10 Lower
-----------

Altera para minúsculo as chaves do array.

.. code:: php

    use Cajudev\Arrays;

    $arrays = new Arrays(['LOREM' => 1, 'IPSUM' => 2]);

    echo $arrays->lower(); // {"lorem":1,"ipsum":2}

13.11 Upper
-----------

Altera para maiúsculo as chaves do array.

.. code:: php

    use Cajudev\Arrays;

    $arrays = new Arrays(['lorem' => 1, 'ipsum' => 2]);

    echo $arrays->upper(); // {"LOREM":1,"IPSUM":2}

