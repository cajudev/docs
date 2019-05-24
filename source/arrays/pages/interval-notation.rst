=======================
6. Notação de Intervalo
=======================

Uma forma muito interessante de acessar parte de um objeto Arrays é através
da notação de intervalo. Veja o exemplo abaixo.

.. code:: php

   use Cajudev\Arrays;

    $arrays = new Arrays([
        'zero'  => 0, 'one'  => 1, 'two' => 2, 'three' => 3,
        'four'  => 4, 'five' => 5, 'six' => 6, 'seven' => 7,
        'eight' => 8, 'nine' => 9, 'ten' => 10
    ]);

    echo $arrays['2:5']; // {"two":2,"three":3,"four":4,"five":5}

Caso você informe um valor inicial maior que o valor final, o resultado será
um array inverso do intervalo definido. 

.. code:: php

   use Cajudev\Arrays;

    $arrays = new Arrays([
        'zero'  => 0, 'one'  => 1, 'two' => 2, 'three' => 3,
        'four'  => 4, 'five' => 5, 'six' => 6, 'seven' => 7,
        'eight' => 8, 'nine' => 9, 'ten' => 10
    ]);

    echo $arrays['6:3']; // {"six":6,"five":5,"four":4,"three":3}

Vale ressaltar que é possível misturar todas as funcionalidades vistas até agora
juntamente com a notação de intervalo. Observe abaixo:

.. code:: php

   use Cajudev\Arrays;

        $arrays = new Arrays([
            'numbers' => [
                'even' => ['two' => 2, 'four' => 4, 'six' => 6, 'eight' => 8],
                'odd'  => ['one' => 1, 'three' => 3, 'five' => 5, 'seven' => 7],
            ],
        ]);
    
        $arrays['numbers.even']['0:2']->each(function($key, $value) {
            echo "key: {$key} value: {$value}" . PHP_EOL;
        });

        /*
            key: two value: 2
            key: four value: 4
            key: six value: 6
        */