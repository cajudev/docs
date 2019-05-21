======================
12. Verificação de Tipo
======================

Esta classe implementa os principais métodos de verificação de tipos, para facilitar esse tipo de trabalho. Observe abaixo:

.. code-block:: php

   use Cajudev\Arrays;

   $arrays['ten'] = 10;
   var_dump($arrays->isInt('ten')); // true

Os seguinte métodos são suportados: ``isInt, isBool, isFloat, isNumeric, isString e isArray``.

Todos esses métodos também podem ser utilizados com a notação de ponto

.. code-block:: php

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
    se o conteúdo for um **array** ou um objeto **Arrays**.