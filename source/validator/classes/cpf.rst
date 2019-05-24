===
Cpf
===

.. code:: php

   public static validate      (string $subject)
   public static validateArray (array  $array)

validate( )
-----------

.. code:: php

   use Cajudev\Validator\Cpf;

   //Retorna um objeto Cpf ou null se o número for inválido.

   if ($cpf = Cpf::validate("590.887.600-39")) {
   
      $cpf->getNumber();        // 590.887.600-39 <<< Formatado
      $cpf->getNumber(false);   // 59088760039    <<< Sem Formatação
      
   } else {
      ...
   }

validateArray( )
----------------

.. code:: php

   use Cajudev\Validator\Cpf;

   //Retorna um array de objetos Cpf contendo apenas números válidos.

   $array = ["438.784.570-81", "231.803.290-41", "477.107.930-69", "769.611.670-55"];

   if ($cpfs = Cpf::validateArray($array)) {

      print_r($cpfs);

   } else {
      ...
   }

Resultado:
..........

.. code:: php

   Array
   (
      [0] => Cajudev\Validator\Cpf Object
         (
            [number:Cajudev\Validator\Cpf:private] => "43878457081"
         )

      [1] => Cajudev\Validator\Cpf Object
         (
            [number:Cajudev\Validator\Cpf:private] => "23180329041"
         )
   )