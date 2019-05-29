===================
4. Sintaxe de Array
===================

É possível manipular esta classe com a sintaxe de array ``$array[$key]``.

4.1 Inserindo valores
---------------------

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();
   $arrays['lorem'] = 'ipsum';
   $arrays[] = 'dolor';

   print_r($arrays);

   /*
    Cajudev\Arrays Object
        (
            [content:protected] => Array
                (
                    [lorem] => ipsum
                    [0] => dolor
                )
            [backup:protected] => 
            [length:Cajudev\Arrays:protected] => 2
        )
   */

4.2 Acessando valores
---------------------

Para acessar uma chave anteriormente setada, basta fazer como o de costume:

.. code:: php

   $arrays = new Arrays();

   $arrays['lorem'] = 'ipsum';

   echo $arrays['lorem']; // ipsum

Diferentemente do método ``get`` que nos retorna ``null`` em casos de chave inexistente tornando não
necessário o uso de verificações, a sintaxe de array requer um pequeno cuidado.

Caso você tente acessar uma posição inexistente, essa posição será inicializada como um array.

.. code:: php

   $arrays = new Arrays();

   $var = $arrays['lorem'];

   print_r($arrays); exit;

   /*
   Cajudev\Arrays Object
      (
         [content:protected] => Array
            (
                  [lorem] => Array
                     (
                     )

            )

         [backup:protected] => 
         [length:protected] => 1
      )
   */


Nesses casos sempre verifique antes utilizando o método ``isset()``, ou o operador de coalescência ``??``.

.. code:: php

   $arrays = new Arrays();

   echo $array->isset('lorem') ? $array['lorem'] : null; // null

   echo $array['lorem'] ?? null; // null