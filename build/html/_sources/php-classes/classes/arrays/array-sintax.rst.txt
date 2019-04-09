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
        [content:protected] => Array
            (
                [lorem] => ipsum
                [0] => dolor
            )

    )
   */

4.2 Acessando valores
---------------------

Para acessar uma chave anteriormente setada, basta fazer como o de costume:

.. code-block:: php

   echo $arrays['lorem']; // ipsum

O diferencial é que ao tentar acessar uma chave que ainda não foi setada, nenhum erro será emitido,
apenas receberá como retorno o valor ``null``, e embora a classe possua,
isso dispensa o uso do método ``isset``.

.. code-block:: php

   var_dump($arrays['invalid']); // NULL