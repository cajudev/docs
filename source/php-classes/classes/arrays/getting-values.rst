====================
3. Recebendo Valores
====================

O método ``get`` possui função dupla. Ele pode receber como argumento uma chave ou mais
retornando assim um valor correpondente, ou, caso não seja passado nenhum argumento
retornará todo o array interno da classe.

3.1 Selecionando dados
----------------------

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', ['dolor' => ['sit' => 'amet']]);

   echo $arrays->get(0); //lorem

   echo $arrays->get(2)->get('dolor')->get('sit'); //amet

   echo $arrays->get(2, 'dolor', 'sit'); //amet

   var_dump($arrays->get());

   /*
    array(3) {
        [0] => string(5) "lorem"
        [1] => string(5) "ipsum"
        [2] => array(1) {
            'dolor' => array(1) {
                'sit' => string(4) "amet"
            }
        }
    }
   */

3.2 Recebendo todo o conteúdo
-----------------------------

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', ['dolor' => ['sit' => 'amet']]);
   
   var_dump($arrays->get());

   /*
    array(3) {
        [0] => string(5) "lorem"
        [1] => string(5) "ipsum"
        [2] => array(1) {
            'dolor' => array(1) {
                'sit' => string(4) "amet"
            }
        }
    }
   */
   
.. note::

    Embora esse uso não     
    seja recomendado pois quebra o conceito de encapsulamento e proteção de dados,  
    existem situações onde você realmente precisará de todo o conteúdo em forma de array.

3.3 Utilizando a Dot Notation
-----------------------------

Existe uma forma interessante de navegar entre o conteúdo de um objeto Arrays,
utilizando a notação de ponto (ou quase isso) através do método ``fetch``.

A concepção deste método foi dada por https://www.linkedin.com/in/clebersonbieleski.

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays([
        'app' => [
            'config' => [
                'database' => [
                    'name'     => 'teste',
                    'host'     => 'localhost',
                    'password' => '1234'
                ]
            ]
        ]
    ]);

    echo $arrays->fetch('app.config.database.password'); // 1234