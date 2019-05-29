======================
13. Verificação de Tipo
======================

Esta classe implementa seis métodos de verificação de tipos.

São eles: ``isInt``, ``isBool``, ``isFloat``, ``isNumeric``, ``isString`` e ``isArray``.

Não confunda, a verificação o tipo é realizada internamente, observe abaixo:

.. code:: php

   use Cajudev\Arrays;

   $arrays['ten'] = 10;
   var_dump($arrays->isInt('ten')); // true

Todos esses métodos também podem ser utilizados com a notação de ponto

.. code:: php

   use Cajudev\Arrays;

   $arrays['results'] = [
       'winner' => [
           'name'  => 'player',
           'score' => 152
       ]
   ];
   var_dump($arrays->isString('results.winner.score')); // false
   var_dump($arrays->isString('results.winner.name')); // true

.. note::

    Uma única ressalva é que o método **isArray** retornará **true**, independentemente
    se o conteúdo for um **array** simples ou um objeto **Arrays**.