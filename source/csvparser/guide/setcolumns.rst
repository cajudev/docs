======================
Customizando o Retorno
======================

.. code:: php

   use Cajudev\CsvParser;

   $dir = __DIR__ . '/file.csv';

   $csv = new CsvParser($dir);

   $csv->setDelimiter(';');

   $csv->setColumns(['Produto', 'Preço', 'Pagamento', 'Nome']);

   $results = $csv->parse();

   print_r($results);

Ou se você preferir:
--------------------

.. code:: php

   $columns = ['Produto', 'Preço', 'Pagamento', 'Nome'];

   $results = $csv->setDelimiter(';')->setColumns($columns)->parse();

Resultado:
----------

.. parsed-literal::

      Array
      (
         [0] => Array
            (
               [Produto] => "Produto1"
               [Preço] => " R$ 1.400,00"
               [Pagamento] => "Mastercard"
               [Nome] => "João"
            )

         [1] => Array
            (
               [Produto] => "Produto2"
               [Preço] => " R$ 1.800,00"
               [Pagamento] => "Visa"
               [Nome] => "Maria"
            )

         [2] => Array
            (
               [Produto] => "Produto3"
               [Preço] => " R$ 1.200,00"
               [Pagamento] => "Mastercard"
               [Nome] => "Pedro"
            )

         [3] => Array
            (
               [Produto] => "Produto3"
               [Preço] => " R$ 2.200,00"
               [Pagamento] => "Mastercard"
               [Nome] => "Henrique"
            )

         [4] => Array
            (
               [Produto] => "Produto2"
               [Preço] => " R$ 1.200,00"
               [Pagamento] => "Visa"
               [Nome] => "Julio"
            )

         [5] => Array
            (
               [Produto] => "Produto2"
               [Preço] => " R$ 5.000,00"
               [Pagamento] => "Visa"
               [Nome] => "Emanuel"
            )

         [6] => Array
            (
               [Produto] => "Produto2"
               [Preço] => " R$ 3.600,00"
               [Pagamento] => "Visa"
               [Nome] => "Silvia"
            )

         [7] => Array
            (
               [Produto] => "Produto1"
               [Preço] => " R$ 1.200,00"
               [Pagamento] => "Visa"
               [Nome] => "Reinaldo"
            )
      )