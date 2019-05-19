======================
7. Imprimindo o Objeto
======================

Ao tentarmos utilizar construtores de linguagem como ``echo`` ou ``print`` em um objeto, 
um erro é emitido pelo php, pois o mesmo não sabe como tratar esse retorno. Felizmente, 
nossa classe implementa um método que retorna nesses casos,
o conteúdo do array interno em formato JSON.

.. code-block:: php

   use Cajudev\Arrays;

   $arrays = new Arrays(['lorem' => 'ipsum', 'dolor' => 'sit', 'amet' => 'consectetur']);
   echo $arrays; 
   
   // {"lorem":"ipsum","dolor":"sit","amet":"consectetur"}