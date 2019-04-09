==========================
8. Iterando sobre o Objeto
==========================

8.1 Iterando em um laço for-each
--------------------------------

A utilização da classe em um laço for-each é a mesma a de um array comum

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem' => 'ipsum', 'dolor' => 'sit']);

   foreach ($arrays as $key => $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
   }

   /*
        key: lorem value: ipsum
        key: dolor value: sit
   */

8.2 Iterando em um laço while
--------------------------------

A utilização da classe em um laço while é realizada da seguinte maneira:

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();
   $arrays->push('lorem', 'ipsum', 'dolor', 'sit');

    while ($arrays->valid()) {
        echo "key {$arrays->key()} value: {$arrays->current()}" . PHP_EOL;
        $arrays->next();
    }

   /*
        key: lorem value: ipsum
        key: dolor value: sit
   */   

8.3 Iterando com o método for
-----------------------------

O método ``for`` é uma maneira interessante de se iterar por um objeto Arrays.

Ele recebe três argumentos, o primeiro é o ponto de partida, o segundo é o 
incremento, e o último é uma função anônima que recebe por meio de injeção a chave e
o valor de cada iteração.

8.3.1 Iterando para frente
..........................

.. code-block:: php

    use Cajudev\Arrays;

    $arrays = new Arrays();

    $arrays->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $arrays->for(0, 2, function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
    });

   /*
        key: 0 value: lorem
        key: 2 value: dolor
        key: 4 value: amet
   */   


8.3.2 Iterando para trás
........................

Caso você queira iterar inversamente o array, basta informar como
segundo argumento um valor negativo.

.. code-block:: php

    use Cajudev\Arrays;

    $arrays = new Arrays();

    $arrays->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $arrays->for(3, -1, function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
    });

    /*
        key: 3 value: sit
        key: 2 value: dolor
        key: 1 value: ipsum
        key: 0 value: lorem
    */   

8.3.3 Iterando arrays mistos
............................

Esse método também funciona com arrays associativos e arrays mistos.

.. code-block:: php

    use Cajudev\Arrays;

    $arrays = new Arrays();

    $arrays['lorem'] = 'ipsum';
    $arrays->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');
    $arrays['dolor'] = 'sit';

    $arrays->for(0, 1, function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
    });

    /*
        key: lorem value: ipsum
        key: 0 value: lorem
        key: 1 value: ipsum
        key: 2 value: dolor
        key: 3 value: sit
        key: 4 value: amet
        key: 5 value: consectetur
        key: dolor value: sit
    */   

8.3.4 Realizando modificações
.............................

Caso você necessite fazer modificações internas no array ao invés de somente obter dados,
você precisará adicionar um ``use`` passando o seu objeto:

.. code-block:: php

    use Cajudev\Arrays;

    $arrays = new Arrays();

    $arrays->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $arrays->for(0, 2, function($key, $value) use ($arrays) {
        $arrays[$key] = 'Hello World';
    });

    print_r($arrays);

    /*
        Cajudev\Arrays Object
        (
            [content:protected] => Array
                (
                    [0] => Hello World
                    [1] => ipsum
                    [2] => Hello World
                    [3] => sit
                    [4] => Hello World
                    [5] => consectetur
                )
                
            [length:Cajudev\Arrays:private] => 
        )
    */

8.3.5 Parando a iteração
........................

As vezes existe a necessite de pular uma iteração ou até mesmo pará-la.
Nestes casos, basta que você retorne da função anônima os valores 'break' ou 'continue'.

.. code-block:: php

    use Cajudev\Arrays;

    $arrays = new Arrays(0, 1, 2, 3, 4, 5);

    $arrays->for(0, 1, function($key, $value) {
        if ($value > 2) {
            return 'break';
        }
        echo $value . ' ';    // 0 1 2
    });

    $arrays->for(0, 1, function($key, $value) {
        if ($value == 2) {
            return 'continue';
        }
        echo $value . ' ';   // 0 1 3 4 5
    });

8.3.6 Exemplo de utilização
...........................

Dado um certo array com números de 0 a 100, como você faria para obter todos os
números pares maiores ou iguais a 70? Utilizando o método for, essa tarefa é muito simples.

.. code-block:: php

    use Cajudev\Arrays;

    $arrays = new Arrays(
        0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14,
        15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27,
        28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40,
        41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53,
        54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66,
        67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79,
        80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92,
        93, 94, 95, 96, 97, 98, 99, 100
    );

    $arrays->for(70, 2, function($key, $value) {
        echo $value . ', ';
    });

    // 70, 72, 74, 76, 78, 80, 82, 84, 86, 88, 90, 92, 94, 96, 98, 100,