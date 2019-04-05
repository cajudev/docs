================
Sintaxe de Array
================

É possível manipular esta classe da mesma maneira que um array comum, acessando
chaves com a forma ``$array[$key]``. No entando, existem algumas características
interessantes que serão mostradas abaixo.

Inserindo valores
-----------------

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays();
   $arrays['lorem'] = 'ipsum';
   $arrays[] = 'dolor';

   print_r($arrays);

   /*
    Cajudev\Classes\Arrays Object
    (
        [content:protected] => Array
            (
                [lorem] => ipsum
                [0] => dolor
            )

    )
   */

Acessando valores
-----------------

Para acessar uma chave anteriormente setada, basta fazer como o de costume:

.. code-block:: php

   echo $arrays['lorem']; // ipsum

Ao tentar acessar uma chave que ainda não foi setada, nenhum erro será emitido,
apenas receberá como retorno o valor ``null``, e embora a classe possua,
isso dispensa o uso do método ``isset``.

.. code-block:: php

   var_dump($arrays['invalid']); // NULL