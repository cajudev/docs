=============
1. Introdução
=============

1.1 Instanciando um objeto vazio
--------------------------------

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays();
   print_r($arrays);

   /*
      Cajudev\Classes\Arrays Object
      (
         [content:protected] => Array
            (
            )
      )
   */

1.2 Instanciando a partir de um array
-------------------------------------

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $array = [1, '2', 'three' => 3];

   $arrays = new Arrays($array);
   print_r($arrays);

   /*
      Cajudev\Classes\Arrays Object
      (
         [content:protected] => Array
            (
                  [0] => 1
                  [1] => 2
                  [three] => 3
            )
      )
   */

1.3 Instanciando a partir de uma lista de valores
-------------------------------------------------

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $int    = 5;
   $std    = new StdClass;
   $string = 'lorem ipsum';

   $arrays = new Arrays($int, $std, $string);
   print_r($arrays);

   /*
      Cajudev\Classes\Arrays Object
      (
         [content:protected] => Array
            (
                  [0] => 5
                  [1] => stdClass Object
                     (
                     )

                  [2] => lorem ipsum
            )
      )
   */

1.4 Instanciando a partir de um objeto
--------------------------------------

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $object = new Class() {
      private   $lorem  = 1;
      protected $ipsum  = 2;
      public    $dolor  = 3;
   };

   $arrays = new Arrays($object);
   print_r($arrays);

   /*
      Cajudev\Classes\Arrays Object
      (
         [content:protected] => Array
            (
                  [lorem] => 1
                  [ipsum] => 2
                  [dolor] => 3
            )
      )
   */