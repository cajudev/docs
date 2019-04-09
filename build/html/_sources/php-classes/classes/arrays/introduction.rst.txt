=============
1. Introdução
=============

1.1 Instanciando um objeto vazio
--------------------------------

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();
   print_r($arrays);

   /*
      Cajudev\Arrays Object
      (
         [content:protected] => Array
            (
            )
      )
   */

1.2 Instanciando a partir de um array
-------------------------------------

.. code-block:: php

   use Cajudev\Arrays;

   $array = [1, '2', 'three' => 3];

   $arrays = new Arrays($array);
   print_r($arrays);

   /*
      Cajudev\Arrays Object
      (
         [content:protected] => Array
            (
                  [0] => 1
                  [1] => 2
                  [three] => 3
            )
      )
   */

1.3 Instanciando a partir de um objeto
--------------------------------------

.. code-block:: php

   use Cajudev\Arrays;

   $object = new Class() {
      private   $lorem  = 1;
      protected $ipsum  = 2;
      public    $dolor  = 3;
   };

   $arrays = new Arrays($object);
   print_r($arrays);

   /*
      Cajudev\Arrays Object
      (
         [content:protected] => Array
            (
                  [lorem] => 1
                  [ipsum] => 2
                  [dolor] => 3
            )
      )
   */