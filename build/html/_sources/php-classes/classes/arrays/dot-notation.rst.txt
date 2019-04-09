===================
5. Notação de Ponto
===================

Uma característica muito interessante que essa classe possui é a possibilidade
de navegar entre seu conteúdo utilizando a notação de ponto.

5.1 Inserindo valores
---------------------

Para criar arrays multidimensionais facilmente, sem a utilização de milhares de colchetes,
basta realizar a atribuição com a notação de ponto, como no exemplo abaixo:

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays();
   $arrays['lorem.ipsum.dolor'] = 'amet';
   $arrays['lorem.ipsum'][] = 'consectetur';
   $arrays['lorem.ipsum'][] = ['sit' => ['amet' => 'dolor']];

   print_r($arrays); // Imprimindo todo o objeto

   /*
        Cajudev\Arrays Object
        (
            [content:protected] => Array
                (
                    [lorem] => Array
                        (
                            [ipsum] => Array
                                (
                                    [dolor] => amet
                                    [0] => consectetur
                                    [1] => Array
                                        (
                                            [sit] => Array
                                                (
                                                    [amet] => dolor
                                                )

                                        )

                                )

                        )

                )

            [length:Cajudev\Arrays:private] => 
        )
   */

5.2 Acessando valores
---------------------

Da mesma forma, é possível facilmente percorrer o objeto para acessar seu conteúdo.
Para os exemplos que serão mostrados abaixo, considere o objeto anteriormente criado.

.. code-block:: php
   
   // Navegando entre os valores

   echo $arrays['lorem.ipsum.1.sit.amet']; // dolor

   // Também é possível misturar as sintaxes se assim o preferir.

   echo $arrays['lorem.ipsum'][1]['sit.amet']; //dolor

