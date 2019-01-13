===============
Exemplos de Uso
===============

Montando uma expressão que valida CEP
-------------------------------------

.. code-block:: php

   use Cajudev\RegexBuilder\Regex;

   $regex = new Regex();

   $regex->beginning()
         ->list()
            ->number()->all()->close()
            ->exactly(5)
            ->close()
         ->symbol()->only('-')->close()
         ->list()
            ->number()->all()->close()
            ->exactly(3)
            ->close()
         ->ending()
         ->make();

   echo $regex->get();

Resultado
.........

.. code-block:: php

   "/^[0-9]{5}\-[0-9]{3}$/"

Montando uma expressão que valida CPF
-------------------------------------

.. code-block:: php

   use Cajudev\RegexBuilder\Regex;

   $regex = new Regex();

   $regex->beginning()
         ->list()
               ->number()->all()->close()
               ->exactly(3)
               ->close()
         ->symbol()->only('.')->close()
         ->list()
               ->number()->all()->close()
               ->exactly(3)
               ->close()
         ->symbol()->only('.')->close()
         ->list()
               ->number()->all()->close()
               ->exactly(3)
               ->close()
         ->symbol()->only('-')->close()
         ->list()
               ->number()->all()->close()
               ->exactly(2)
               ->close()
         ->ending()
         ->make();

   echo $regex->get();

Resultado
.........

.. code-block:: php

   "/^([0-9]{3}\.){2}[0-9]{3}\-[0-9]{2}$/"

Como você pode notar, a estrutura do builder tende a ocupar muitas linhas. Por causa disso, o seu ciclo de vida acaba se tornando:

1. Ajudar o programador a montar uma expressão utilizando uma sintaxe muito mais agradável.
2. Ser deletada e substituída pela expressão gerada. (Opcional)

Montando uma expressão que valida data
--------------------------------------

.. code-block:: php

   use Cajudev\RegexBuilder\Regex;

   $regex = new Regex();

   $regex->beginning()
         ->group()
            ->name('day')
            ->list()
               ->number()->range(0, 2)->close()
               ->close()
            ->list()
               ->number()->range(1, 9)->close()
               ->close()
            ->logic()->or()->close()
            ->list()
               ->number()->range(1, 3)->close()
               ->close()
            ->list()
               ->number()->range(0, 1)->close()
               ->close()
            ->close()
         ->group()
            ->name('month')
            ->number()->only(0)->close()
            ->list()
               ->number()->range(1, 9)->close()
               ->close()
            ->logic()->or()->close()
            ->number()->only(1)->close()
            ->list()
               ->number()->range(0, 2)->close()
               ->close()
            ->close()
         ->group()
            ->name('year')
            ->number()->list(1, 9)->close()
            ->list()
               ->number()->all()->close()
               ->exactly(2)
               ->close()
            ->logic()->or()->close()
            ->number()->list(2, 0)->close()
            ->list()
               ->number()->all()->close()
               ->exactly(2)
               ->close()
            ->close()
         ->ending()
         ->make();

   echo $regex->get();

Resultado
.........

.. code-block:: php

   "/^(?<day>[0-2][1-9]|[1-3][0-1])(?<month>0[1-9]|1[0-2])(?<year>19[0-9]{2}|20[0-9]{2})$/"