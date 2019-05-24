====
Date
====

Responsável por verificar a validade de uma data dado um formato específico e ainda podendo converter facilmente entre formatos.

Tabela de Caracteres
====================

Para uma rápida assimilação, utilizamos uma sintaxe igual à utilizada na função nativa ``date()``

========= ========= ===========================================
Caractere Descrição Intervalo                                  
d         dia       01-31                                      
j         dia       1-31                                       
m         mês       01-12                                      
n         mês       1-12                                       
y         ano       00-99 (20xx entre 00-69 e 19xx entre 70-99)
Y         ano       1970-2099                                  
========= ========= ===========================================

Exemplos
========

.. code:: php

   public static validate      (string $subject, string $format)
   public static validateArray (array  $array,   string $pattern)

validate( )
-----------

.. code:: php

   use Cajudev\Validator\Date;

   //Retorna um objeto Date ou null se a data for inválida.

   if ($date = Date::validate('2018-12-19', 'Y-m-d')) {
      
      $date->getDate();        // 2018-12-19 <<< Mesmo formato de entrada
      $date->getDate('d/m/y'); // 19/12/18   <<< Saída personalizada
      $date->getDay();         // 19
      $date->getMonth();       // 12
      $date->getYear();        // 2018
      $date->getTimestamp()    // 1545177600
      
   } else {
      ...
   }

validateArray( )
----------------

.. code:: php

   use Cajudev\Validator\Date;

   //Retorna um array de objetos Date contendo apenas datas válidas.
   
   $array = ['2018-12-19', '12/05/2018', '14-02-18', '2018/01/05', '1995-02-18', '20.08.2000'];
   
   if ($dates = Date::validateArray($array, 'Y-m-d')) {

      print_r($dates);

   } else {
         ...
   }

Resultado:
..........

.. code:: php

   Array
   (
      [0] => Cajudev\Validator\Date Object
         (
            [date:Cajudev\Validator\Date:private] => "2018-12-19"
            [day:Cajudev\Validator\Date:private] => "19"
            [month:Cajudev\Validator\Date:private] => "12"
            [year:Cajudev\Validator\Date:private] => "2018"
            [timestamp:Cajudev\Validator\Date:private] => "1545177600"
         )

      [1] => Cajudev\Validator\Date Object
         (
            [date:Cajudev\Validator\Date:private] => "1995-02-18"
            [day:Cajudev\Validator\Date:private] => "18"
            [month:Cajudev\Validator\Date:private] => "02"
            [year:Cajudev\Validator\Date:private] => "1995"
            [timestamp:Cajudev\Validator\Date:private] => "793065600"
         )
   )