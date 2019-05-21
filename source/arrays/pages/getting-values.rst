====================
3. Recebendo Valores
====================

O método ``get`` possui função dupla. Ele pode receber como argumento uma chave ou mais
retornando assim um valor correpondente, ou, caso não seja passado nenhum argumento
retornará todo o array interno da classe. Esse método também suporta a notação de ponto descrita na seção 5.

3.1 Selecionando dados
----------------------

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem', 'ipsum', ['dolor' => ['sit' => 'amet']]]);

   echo $arrays->get(0); //lorem

   // chamadas encadeadas...
   echo $arrays->get(2)->get('dolor')->get('sit'); //amet

   // ou com argumentos variáveis...
   echo $arrays->get(2, 'dolor', 'sit'); //amet

   // ou ainda com a notação de ponto...
   echo $arrays->get('2.dolor.sit'); //amet

3.2 Recebendo todo o conteúdo
-----------------------------

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem', 'ipsum', ['dolor' => ['sit' => 'amet']]]);
   
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

3.3 Recebendo o tamanho do array
--------------------------------

A cada inserção ou remoção de valores, o atributo interno ``length`` é atualizado,
portanto para receber o tamanho do array, basta acessá-lo diretamente.

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem', 'ipsum', ['dolor' => ['sit', 'amet']]]);
   
   echo $arrays->length; // 3
   echo $arrays[2]['dolor']->length; // 2