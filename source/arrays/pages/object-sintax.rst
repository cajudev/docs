====================
5. Sintaxe de Objeto
====================

É possível manipular os valores do array interno dessa classe como se fossem propriedades.

5.1 Inserindo valores
---------------------

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();
   $arrays->lorem = 'ipsum';

   print_r($arrays);

   /*
      Cajudev\Arrays Object
         (
            [content:protected] => Array
               (
                  [lorem] => ipsum
               )

            [length:protected] => 1
            [backup:protected] => 
         )
   */

Apenas a palavra reservada ``length`` não pode ser utilizada por se tratar de um atributo somente leitura da classe.

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();
   $arrays->length = 10; // InvalidArgumentException: length property is readonly

5.2 Recebendo valores
---------------------

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();

   $arrays->lorem = 'ipsum';

   echo $arrays->lorem; // ipsum

.. note::

   Não é obrigatório realizar a verificação com a função ``isset()`` ao acessar posições desta maneira,
   pois internamente uma verificação é realizada e caso a posição não tenha sido inicializada o valor ``null`` é retornado.

5.3 Verificando nulidade
------------------------

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();

   $arrays->lorem = 'ipsum';

   echo isset($arrays->lorem); // true

   echo isset($arrays->ipsum); // false

5.4 Removendo valores
---------------------

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();

   $arrays->lorem = 'ipsum';

   unset($arrays->lorem);

   echo isset($arrays->lorem); // false

5.5 Sintaxe com chaves
----------------------

Propriedades em php não podem ser nomeadas com caracteres especiais como '.' ou '-'. Nesses casos é necessário observar a sintaxe a seguir.

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();

   $arrays->lorem-ipsum = 'dolor'; // sintax error

   $arrays->{'lorem-ipsum'} = 'dolor'; // funciona corretamente

   print_r($arrays);

   /*
   Cajudev\Arrays Object
      (
         [content:protected] => Array
            (
               [lorem-ipsum] => dolor
            )

         [length:protected] => 1
         [backup:protected] => 
      )
   */

5.6 Notação de ponto
--------------------

É possível manipular dados de forma multidimensional utilizando a notação de ponto descrita na seção 6.

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();

   $arrays->{'lorem.ipsum'} = 'dolor';

   print_r($arrays); exit;

   /*
   Cajudev\Arrays Object
   (
      [content:protected] => Array
         (
            [lorem] => Array
               (
                  [ipsum] => dolor
               )

         )

      [length:protected] => 1
      [backup:protected] => 
   )
   */