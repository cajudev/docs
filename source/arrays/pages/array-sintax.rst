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

4.2 Acessando valores
---------------------

Para acessar uma chave anteriormente setada, basta fazer como o de costume:

.. code-block:: php

   echo $arrays['lorem']; // ipsum

.. warning::

   Ao tentar acessar uma chave que ainda não foi setada, nenhum erro será emitido,
   porém a chave será criada automaticamente com o valor ``null``, então é importante
   que utilize o método ``isset`` ou o operador ``??`` para verificar a existência
   de uma chave antes de acessá-la.