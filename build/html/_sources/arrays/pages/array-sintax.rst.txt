===================
4. Sintaxe de Array
===================

É possível manipular esta classe da mesma maneira que um array comum, acessando
chaves com a forma ``$array[$key]``.

4.1 Inserindo valores
---------------------

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();
   $arrays['lorem'] = 'ipsum';
   $arrays[] = 'dolor';

   print_r($arrays);

   /*
    Cajudev\Arrays Object
        (
            [length:Cajudev\Arrays:private] => 2
            [content:protected] => Array
                (
                    [lorem] => ipsum
                    [0] => dolor
                )

        )
   */

Uma caracteristica muito interessante é que não é necessário inicializar posições no array para
utilizar os operadores de atribuição.

.. code-block:: php

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


4.2 Acessando valores
---------------------

Para acessar uma chave anteriormente setada, basta fazer como o de costume:

.. code-block:: php

   $arrays = new Arrays();

   $arrays['lorem'] = 'ipsum';

   echo $arrays['lorem']; // ipsum

Caso tente acessar uma chave inexistente, nenhum erro será emitido e o valor retornado será null
porém como consequência a chave será inicializada. Veja abaixo.

.. code-block:: php

   $arrays = new Arrays();

   print_r($arrays);

   /*
   Cajudev\Arrays Object
      (
         [content:Cajudev\Arrays:private] => Array
            (
            )
         [length:Cajudev\Arrays:private] => 0
      )
   */

   echo $arrays['lorem']; // null

   print_r($arrays);

   /*
   Cajudev\Arrays Object
      (
         [content:Cajudev\Arrays:private] => Array
            (
               [lorem] => 
            )
         [length:Cajudev\Arrays:private] => 0
      )
   */

Se esse não é o comportamento desejado, basta realizar uma verificação antes com o método ``isset``,
ou usufruir do operador de coalescência ``??``.

.. code-block:: php

   $arrays = new Arrays();

   echo $array->isset('lorem') ? $array['lorem'] : null; // null

   echo $array['lorem'] ?? null; // null
