==========
CreditCard
==========

.. code:: php

   public static validate      (string $subject)
   public static validateArray (array  $array)

validate( )
-----------

.. code:: php

   use Cajudev\Validator\CreditCard;

   //Retorna um objeto CreditCard ou null se o número for inválido.

   if ($cc = CreditCard::validate("5277887630105547")) {
    
      $cc->getNumber();        // 5277 8876 3010 5547 <<< Formatado
      $cc->getNumber(false);   // 5277887630105547    <<< Sem Formatação
      $cc->getFlag()           // mastercard
      
   } else {
      ...
   }

validateArray( )
----------------

.. code:: php

   use Cajudev\Validator\CreditCard;

   //Retorna um array de objetos CreditCard contendo apenas números válidos.
  
   $array = ["4532 6941 9414 4788", "4532 6941 9414 4787", "3775 247152 71461"];
  
   if ($ccs = CreditCard::validateArray($array)) {

      print_r($ccs);

   } else {
      ...
   }

Resultado:
..........

.. code:: php

   Array
   (
      [0] => Cajudev\Validator\CreditCard Object
         (
            [number:Cajudev\Validator\CreditCard:private] => "4532694194144787"
            [flag:Cajudev\Validator\CreditCard:private] => "visa"
         )
   )