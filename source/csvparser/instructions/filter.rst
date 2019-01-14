===============
Filtrando Dados
===============

.. code-block:: php

   use Cajudev\CsvParser;

   $dir = __DIR__ . '/file.csv';

   $csv = new CsvParser($dir);

   $csv->setDelimiter(';');

   $csv->setColumns(['Produto', 'Preço', 'Pagamento', 'Nome']);

   $csv->setFilters([                                   // 
      'Pagamento' => ['Visa'],                          // Linhas
      'Estado'    => ['São Paulo', 'Rio de Janeiro'],   // Acrescentadas
   ]);                                                  //

   $results = $csv->parse();

   print_r($results);

Resultado:
..........

.. parsed-literal::

      Array
      (
         [0] => Array
            (
               [Produto] => "Produto2"
               [Preço] => " R$ 1.800,00"
               [Pagamento] => "Visa"
               [Nome] => "Maria"
            )

         [1] => Array
            (
               [Produto] => "Produto2"
               [Preço] => " R$ 5.000,00"
               [Pagamento] => "Visa"
               [Nome] => "Emanuel"
            )

         [2] => Array
            (
               [Produto] => "Produto2"
               [Preço] => " R$ 3.600,00"
               [Pagamento] => "Visa"
               [Nome] => "Silvia"
            )
      )