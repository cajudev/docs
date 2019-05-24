=============
1. Introdução
=============

1.1 Instanciando um objeto vazio
--------------------------------

Ao analisar a estrutura do objeto, podemos ver que o mesmo possui 3 atributos:
``content``, ``backup`` e ``length``.

Todos possuem visibilidade ``protected``, permitindo com que você crie uma fachada
para a classe em sua aplicação através de herança, se assim o quiser.

O atributo ``content`` armazena todo o conteúdo adicionado ao objeto.

O atributo ``backup`` armazena uma cópia de segurança de ``content``,
quando o método ``backup()`` é chamado.

Por fim, o atributo ``length``, armazena o tamanho atual do array, tornando
desnecessário o uso de funções como ``count()``.

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();
   print_r($arrays);

   /*
      Cajudev\Arrays Object
         (
            [content:protected] => Array
               (
               )
            [backup:protected] => 
            [length:protected] => 0
         )
   */

1.2 Instanciando a partir de um array
-------------------------------------

Opcionalmente, o construtor do objeto pode receber como argumento
um valor inicial em forma de array.

.. code:: php

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
            [backup:protected] => 
            [length:Cajudev\Arrays:protected] => 3
         )
   */

1.3 Instanciando a partir de um objeto
--------------------------------------

O método estático ``fromObject()`` realiza a conversão dos 
atributos de um objeto em um array associativo. 

Repare que o método independe da visibilidade do atributo.

.. code:: php

   use Cajudev\Arrays;

   $object = new Class() {
      protected   $lorem  = 1;
      protected $ipsum  = 2;
      public    $dolor  = 3;
   };

   $arrays = Arrays::fromObject($object);
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
            [backup:protected] => 
            [length:Cajudev\Arrays:protected] => 3
         )
   */