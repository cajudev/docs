====================
2. Inserindo valores
====================

2.1 Inserindo valores ao final do array
---------------------------------------

.. raw:: php
   
   <?php
   
   highlight_string('<?php function push(string ...$values): self');

O método ``push()`` aceita um número variável de argumentos e serve para adicionar (empurrar) valores ao final do array.

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem', 'ipsum', 'dolor']);
   $arrays->push('sit', 'amet', 'consectetur');
   print_r($arrays);

   /*
      Cajudev\Arrays Object
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
            [backup:protected] => 
            [length:Cajudev\Arrays:protected] => 6
         )
   */

2.2 Inserindo valores no início do array
----------------------------------------

O método ``unshift()`` aceita um número variável de argumentos e serve para adicionar valores no início do array

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem', 'ipsum', 'dolor']);
   $arrays->unshift('sit', 'amet', 'consectetur');
   print_r($arrays);

   /*
      Cajudev\Arrays Object
         (
            [content:protected] => Array
               (
                  [0] => sit
                  [1] => amet
                  [2] => consectetur
                  [3] => lorem
                  [4] => ipsum
                  [5] => dolor
               )
               [backup:protected] => 
               [length:Cajudev\Arrays:protected] => 6
         )
   */

2.3 Associando valores à chaves
-------------------------------

O método ``set()`` é usado para associar uma ou mais chaves à um valor.  Como primeiro argumento, deve ser
informado o valor, e os demais são as chaves. Ele também suporta a notação de ponto descrita na seção 5.

.. code:: php

   // adicionando o valor 'lorem' na chave 'ipsum'
   $arrays->set('lorem', 'ipsum');
   print_r($arrays);

   /*
      Cajudev\Arrays Object
         (
            [content:protected] => Array
               (
                     [ipsum] => lorem
               )

            [length:protected] => 1
            [backup:protected] => 
         )
   */

   // adicionando o valor 'lorem' nas chaves 'ipsum e dolor'
   $arrays->set('lorem', 'ipsum', 'dolor');
   print_r($arrays); 

   /*
      Cajudev\Arrays Object
         (
            [content:protected] => Array
               (
                     [ipsum] => lorem
                     [dolor] => lorem
               )

            [length:protected] => 2
            [backup:protected] => 
         )
   */

   // adicionando de maneira multidimensional
   $arrays->set('lorem', 'ipsum.dolor.amet');
   print_r($arrays);

   /*
      Cajudev\Arrays Object
         (
            [content:protected] => Array
               (
                     [ipsum] => Array
                        (
                           [dolor] => Array
                                 (
                                    [amet] => lorem
                                 )

                        )

               )

            [length:protected] => 1
            [backup:protected] => 
         )
   */

2.4 Inserindo dados por referência
----------------------------------

O método ``setByReference()`` permitir atribuir por referência um conteúdo à classe.

.. code:: php

   use Cajudev\Arrays;

   $session = new Arrays();

   $session->setByReference($_SESSION);
   
   $session->set('Lorem', 'hello.world');

   print_r($_SESSION);

   /*
      Array
         (
            [hello] => Array
               (
                     [world] => Lorem
               )

         )
   */