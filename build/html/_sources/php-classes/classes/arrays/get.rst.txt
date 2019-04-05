===
Get
===

O método ``get`` é usado para ter acesso ao array interno da classe. Embora seu uso não 
seja recomendado pois quebra o conceito de encapsulamento e proteção de dados,
existem situações onde você realmente precisará do conteúdo em forma de array.

.. code-block:: php

   use Cajudev\Classes\Arrays;

   $arrays = new Arrays('lorem', 'ipsum', 'dolor');
   var_dump($arrays->get());

   /*
    array(3) {
        [0] => string(5) "lorem"
        [1] => string(5) "ipsum"
        [2] => string(5) "dolor"
    }
   */