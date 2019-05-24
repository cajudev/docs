==
Rg
==

.. code:: php

   public static validate      (string $subject)
   public static validateArray (array  $array)

validate( )
-----------

.. code:: php

   use Cajudev\Validator\Rg;

   //Retorna um objeto Rg ou null se o número for inválido.

   if ($rg = Rg::validate("43.230.115-X")) {
      
      $rg->getNumber();        // 43.230.115-X <<< Formatado
      $rg->getNumber(false);   // 43230115X    <<< Sem Formatação
      
   } else {
      ...
   }

validateArray( )
----------------

.. code:: php

  use Cajudev\Validator\Rg;

  //Retorna um array de objetos Rg contendo apenas números válidos.
  
  $array = ["32.331.620-7", "43.513.112-6", "26.178.384-1", "15.978.609-7", "43.230.111-X"];
  
  if ($rgs = Rg::validateArray($array)) {

      print_r($rgs);

  } else {
      ...
  }

Resultado:
..........

.. code:: php

   Array
   (
      [0] => Cajudev\Validator\Rg Object
         (
            [number:Cajudev\Validator\Rg:private] => "323316207"
         )

      [1] => Cajudev\Validator\Rg Object
         (
            [number:Cajudev\Validator\Rg:private] => "435131126"
         )

      [2] => Cajudev\Validator\Rg Object
         (
            [number:Cajudev\Validator\Rg:private] => "261783841"
         )
   )