16. Backup e Restauração
========================

16.1 Backup
-----------

O método ``backup`` permite criar uma cópia de segurança do estado atual do objeto.

Vejamos um exemplo:

.. code:: php

    use Cajudev\Arrays;

    $arrays = new Arrays([1, 2, 3, 4, 5]);

    print_r($arrays); exit;

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

Agora realizaremos o backup:

.. code:: php

    $arrays->backup();
    print_r($arrays); exit;

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

            [backup:protected] => Array
                (
                    [0] => 1
                    [1] => 2
                    [2] => 3
                    [3] => 4
                    [4] => 5
                )

            [length:protected] => 5
        )
    */

Podemos processar os dados como quisermos:

.. code:: php

    $arrays->filter(function($value) {
        return $value > 2;
    });

    print_r($arrays);

    /*
    Cajudev\Arrays Object
        (
            [content:protected] => Array
                (
                    [2] => 3
                    [3] => 4
                    [4] => 5
                )

            [backup:protected] => Array
                (
                    [0] => 1
                    [1] => 2
                    [2] => 3
                    [3] => 4
                    [4] => 5
                )

            [length:protected] => 3
        )
    */

16.2 Restauração
----------------

O método ``restore`` permite restaurar os dados anteriormente salvos, limpando o backup.

.. code:: php

    $arrays->restore();

    print_r($arrays);

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
