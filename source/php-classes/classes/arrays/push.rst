====
Push
====

O método ``push`` é usado para adicionar (empurrar) um ou mais valores ao final do array

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');
   $arrays->push('sit', 'amet', 'consectetur');
   print_r($arrays);

   /*
      Cajudev\Classes\Arrays Object
      (
         [content:protected] => Array
            (
                  [0] => lorem
                  [1] => ipsum
                  [2] => dolor
                  [3] => sit
                  [4] => amet
                  [5] => consectetur
            )
      )
   */