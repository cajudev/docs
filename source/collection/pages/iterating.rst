==========================
10. Iterando sobre o Objeto
==========================

10.1 Iterando em um laço for-each
--------------------------------

A utilização da classe em um laço for-each é a mesma a de um array comum

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['lorem' => 'ipsum', 'dolor' => 'sit']);

   foreach ($collection as $key => $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
   }

   /*
        key: lorem value: ipsum
        key: dolor value: sit
   */

10.2 Iterando com o método each
-------------------------------

10.2.1 Percorrendo o array
.........................

O método ``each()`` performa um loop for-each internamente através de uma função callback.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection(['lorem' => 'ipsum', 'dolor' => 'sit']);

   $collection->each(function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
   });

    /*
        key: lorem value: ipsum
        key: dolor value: sit
   */
   
10.2.2 Parando a iteração
........................

Para pular uma iteração basta utilizar um ``return``.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection([0, 1, 2, 3, 4, 5]);

    $collection->each(function($key, $value) {
        if ($value > 2) {
            return;
        }
        echo $value . ' ';    // 0 1 2
    });

10.3 Iterando em um laço while
--------------------------------

O objeto responsável por iterar entre os valores dessa classe é o ``CollectionIterator``.

No exemplo abaixo, vocẽ poderá observar sua utilização em um laço while.

.. code:: php

   use Cajudev\Collection;

   $collection = new Collection();
   $collection->push('lorem', 'ipsum', 'dolor', 'sit');

   $iterator = $collection->getIterator();

    while ($iterator->valid()) {
        echo "key {$iterator->key()} value: {$iterator->current()}" . PHP_EOL;
        $iterator->next();
    }

   /*
        key: lorem value: ipsum
        key: dolor value: sit
   */   

10.4 Iterando com o método for
-----------------------------

O método ``for()`` permite iterar um objeto Collection através de passos.

Ele recebe três argumentos, o primeiro é o ponto de partida, o segundo é o 
incremento, e o último é uma função anônima que recebe por meio de injeção a chave e
o valor de cada iteração.

10.4.1 Iterando "para frente"
............................

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection();

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $collection->for(0, 2, function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
    });

   /*
        key: 0 value: lorem
        key: 2 value: dolor
        key: 4 value: amet
   */

10.4.2 Iterando "para trás"
..........................

Caso você queira iterar inversamente o objeto, basta informar como
segundo argumento um valor negativo.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection();

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $collection->for(3, -1, function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
    });

    /*
        key: 3 value: sit
        key: 2 value: dolor
        key: 1 value: ipsum
        key: 0 value: lorem
    */   

Tome o cuidado de não informar um valor inválido

.. code:: php

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $collection->for(7, -1, function($key, $value) {
        echo "key: {$key} value: {$value}" . PHP_EOL;
    });

    // Undefined offset: 7

10.4.3 Realizando modificações
.............................

Caso você necessite fazer modificações internas ao invés de somente obter dados,
você precisará adicionar um ``use`` passando o próprio objeto:

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection();

    $collection->push('lorem', 'ipsum', 'dolor', 'sit', 'amet', 'consectetur');

    $collection->for(0, 2, function($key, $value) use ($collection) {
        $collection[$key] = 'Hello World';
    });

    print_r($collection);

    /*
        Cajudev\Collection Object
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
                
            [length:Cajudev\Collection:protected] => 
        )
    */

10.4.4 Exemplo de utilização
...........................

Dado um certo array com números de 0 a 100, como você faria para obter todos os
números pares maiores ou iguais a 70? Utilizando o método ``for()``, essa tarefa é muito simples.

.. code:: php

    use Cajudev\Collection;

    $collection = new Collection(
        0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14,
        15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27,
        28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40,
        41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53,
        54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66,
        67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79,
        80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92,
        93, 94, 95, 96, 97, 98, 99, 100
    );

    $collection->for(70, 2, function($key, $value) {
        echo $value . ', ';
    });

    // 70, 72, 74, 76, 78, 80, 82, 84, 86, 88, 90, 92, 94, 96, 98, 100,