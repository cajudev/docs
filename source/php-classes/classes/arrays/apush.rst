=====
Apush
=====

O método ``apush`` é usado para adicionar (empurrar) um ou mais valores ao final do array
de maneira associativa onde o primeiro argumento corresponde à chave e o segundo ao valor,
sendo assim sussessivamente.

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays();
   $arrays->apush(
        'lorem' , 'ipsum',
        'dolor' , 'sit',
        'amet'  , 'consectetur'
    );
   print_r($arrays);

   /*
    Cajudev\Classes\Arrays Object
    (
        [content:protected] => Array
            (
                [lorem] => ipsum
                [dolor] => sit
                [amet] => consectetur
            )
    )
   */

.. note::

   Caso o número de argumento informado seja ímpar, o a última chave 
   informada terá valor ``null``

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays();
   $arrays->apush(
        'lorem' , 'ipsum',
        'dolor' , 'sit',
        'amet'
    );
   var_dump($arrays);

    /*
    class Cajudev\Classes\Arrays#413 (1) {
        protected $content =>
            array(3) {
                'lorem' => string(5) "ipsum"
                'dolor' => string(3) "sit"
                'amet' => NULL
            }
    }
    */