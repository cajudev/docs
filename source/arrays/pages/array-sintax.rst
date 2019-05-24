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

4.2 Acumulando Valores
----------------------

Uma caracteristica interessante dessa classe é que não é necessário inicializar posições no array para
utilizar os operadores de atribuição.

.. code:: php

   $array = [];

   //Isso seria necessário caso estivesse utilizando um array normal
   $array['sum'] = 0;

   //Para só então poder acumular
   $array['sum'] += $valor;

   //Mas não é necessário quando estiver utilizando um objeto Arrays
   $arrays = new Arrays();
   $arrays['sum'] += $valor; // atribuição válida

Isso é válido para qualquer um dos operadores listados em 
https://www.php.net/manual/pt_BR/language.operators.assignment.php.


4.3 Acessando valores
---------------------

Para acessar uma chave anteriormente setada, basta fazer como o de costume:

.. code:: php

   $arrays = new Arrays();

   $arrays['lorem'] = 'ipsum';

   echo $arrays['lorem']; // ipsum

Caso tente acessar uma chave inexistente, nenhum erro será emitido e o valor retornado será null
porém como consequência a chave será inicializada. Veja abaixo.

.. code:: php

   $arrays = new Arrays();

   // antes do acesso
   print_r($arrays);

   /*
   Cajudev\Arrays Object
      (
         [content:Cajudev\Arrays:protected] => Array
            (
            )
         [backup:protected] => 
         [length:Cajudev\Arrays:protected] => 0
      )
   */

   echo $arrays['lorem']; // null

   // após o acesso
   print_r($arrays);

   /*
   Cajudev\Arrays Object
      (
         [content:Cajudev\Arrays:protected] => Array
            (
               [lorem] => 
            )
         [backup:protected] => 
         [length:Cajudev\Arrays:protected] => 0
      )
   */

Para contornar isso, basta realizar uma verificação antes com o método ``isset()``,
ou usufruir do operador de coalescência ``??``.

.. code:: php

   $arrays = new Arrays();

   echo $array->isset('lorem') ? $array['lorem'] : null; // null

   echo $array['lorem'] ?? null; // null

Uma alternativa seria o uso do método ``get()`` descrito na seção anterior.