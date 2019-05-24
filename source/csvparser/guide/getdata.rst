=============
Obtendo Dados
=============

.. code:: php

   use Cajudev\CsvParser;

   $dir = __DIR__ . '/file.csv';

   $csv = new CsvParser($dir);

   $csv->setDelimiter(';');

   $results = $csv->parse();

   print_r($results);

Ou se você preferir:
--------------------

.. code:: php

   $results = $csv->setDelimiter(';')->parse();

Resultado:
----------

.. parsed-literal::

      Array
      (
         [0] => Array
            (
               [Data] => "11/01/2019"
               [Produto] => "Produto1"
               [Preço] => " R$ 1.400,00"
               [Pagamento] => "Mastercard"
               [Nome] => "João"
               [Estado] => "Rio de Janeiro"
            )

         [1] => Array
            (
               [Data] => "12/01/2019"
               [Produto] => "Produto2"
               [Preço] => " R$ 1.800,00"
               [Pagamento] => "Visa"
               [Nome] => "Maria"
               [Estado] => "São Paulo"
            )

         [2] => Array
            (
               [Data] => "11/01/2019"
               [Produto] => "Produto3"
               [Preço] => " R$ 1.200,00"
               [Pagamento] => "Mastercard"
               [Nome] => "Pedro"
               [Estado] => "Minas Gerais"
            )

         [3] => Array
            (
               [Data] => "14/01/2019"
               [Produto] => "Produto3"
               [Preço] => " R$ 2.200,00"
               [Pagamento] => "Mastercard"
               [Nome] => "Henrique"
               [Estado] => "São Paulo"
            )

         [4] => Array
            (
               [Data] => "11/01/2019"
               [Produto] => "Produto2"
               [Preço] => " R$ 1.200,00"
               [Pagamento] => "Visa"
               [Nome] => "Julio"
               [Estado] => "Minas Gerais"
            )

         [5] => Array
            (
               [Data] => "16/01/2019"
               [Produto] => "Produto2"
               [Preço] => " R$ 5.000,00"
               [Pagamento] => "Visa"
               [Nome] => "Emanuel"
               [Estado] => "Rio de Janeiro"
            )

         [6] => Array
            (
               [Data] => "17/01/2019"
               [Produto] => "Produto2"
               [Preço] => " R$ 3.600,00"
               [Pagamento] => "Visa"
               [Nome] => "Silvia"
               [Estado] => "São Paulo"
            )

         [7] => Array
            (
               [Data] => "18/01/2019"
               [Produto] => "Produto1"
               [Preço] => " R$ 1.200,00"
               [Pagamento] => "Visa"
               [Nome] => "Reinaldo"
               [Estado] => "Minas Gerais"
            )
      )