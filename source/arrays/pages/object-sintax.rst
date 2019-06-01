====================
5. Sintaxe de Objeto
====================

É possível manipular os valores do array interno dessa classe como se fosse propriedades.

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