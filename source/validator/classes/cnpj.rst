====
Cnpj
====

.. code:: php

   public static validate      (string $subject)
   public static validateArray (array  $array)

validate( )
-----------

.. code:: php

   use Cajudev\Validator\Cnpj;

   //Retorna um objeto Cnpj ou null se o número for inválido.

   if ($cnpj = Cnpj::validate("60.342.988/0001-07")) {
      
      $cnpj->getNumber();        // 60.342.988/0001-07 <<< Formatado
      $cnpj->getNumber(false);   // 60342988000107     <<< Sem Formatação
      
   } else {
      ...
   }

validateArray( )
----------------

.. code:: php

  use Cajudev\Validator\Cnpj;

  //Retorna um array de objetos Cnpj contendo apenas números válidos.
  
  $array = ["57.806.461/0001-74", "09.475.795/0001-69", "60.184.969/0001-81"];
  
  if ($cnpjs = Cnpj::validateArray($array)) {

      print_r($cnpjs);

  } else {
      ...
  }

Resultado:
..........

.. code:: php

   Array
   (
      [0] => Cajudev\Validator\Cnpj Object
         (
            [number:Cajudev\Validator\Cnpj:private] => "09475795000169"
         )
   )