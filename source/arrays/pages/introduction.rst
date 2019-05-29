=============
1. Introdução
=============

1.1 Analisando a estrutura da classe
------------------------------------

Esta classe possui três atributos: ``content``, ``backup`` e ``length``.

Todos possuem visibilidade ``protected``, permitindo com que você use herança caso necessite.

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

1.2 Criando uma instância a partir de um array
----------------------------------------------

Você pode inicializar o objeto passando um array para o seu construtor.

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

1.3 Criando uma instância a partir de um objeto Arrays
------------------------------------------------------

Você também pode sem problemas passar como argumento um objeto desta classe
para o construtor, ele será convertido internamente.

.. code:: php

   use Cajudev\Arrays;

   $oldArrays = new Arrays([1, 2, 3, 4, 5]);

   $newArrays = new Arrays($oldArrays);

   print_r($newArrays); exit;

   /*
      Cajudev\Arrays Object
         (
            [content:protected] => Array
               (
                     [0] => 1
                     [1] => 2
                     [2] => 3
                     [3] => 4
                     [4] => 5
               )

            [backup:protected] => 
            [length:protected] => 5
         )
   */

1.4 Criando uma instância a partir de outros objetos
----------------------------------------------------

Outros objetos passados por parâmetro serão tratados de forma especial,
sendo parseados internamente.

Observe que a visibilidade dos atributos não afeta o parseamento.

.. code:: php

   use Cajudev\Arrays;

   $object = new Class() {
      protected $lorem  = 1;
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

            [backup:protected] => 
            [length:protected] => 3
         )
   */