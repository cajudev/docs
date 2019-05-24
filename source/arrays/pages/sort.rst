=====================
10. Ordenando o Array
=====================

10.1 Ordenando valores
----------------------

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays([3, 4, 8, 7, 1, 5]);
   $arrays->sort(); //[1,3,4,5,7,8]

10.2 Ordenando valores em ordem inversa
---------------------------------------

.. code:: php

   use Cajudev\Arrays;

   $arrays = new Arrays([3, 4, 8, 7, 1, 5]);
   $arrays->rsort(); //[8,7,5,4,3,1]

10.3 Ordenando valores mantendo associação
------------------------------------------

.. code:: php

   use Cajudev\Arrays;

    $arrays = new Arrays([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $arrays->asort(); //{"dolor":"amet","sit":"consectetur","lorem":"ipsum"}

10.4 Ordenando valores em ordem inversa mantendo associação
-----------------------------------------------------------

.. code:: php

   use Cajudev\Arrays;

    $arrays = new Arrays([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $arrays->arsort(); // {"lorem":"ipsum","sit":"consectetur","dolor":"amet"}

10.5 Ordenando por chaves
-------------------------

.. code:: php

   use Cajudev\Arrays;

    $arrays = new Arrays([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $arrays->ksort(); //{"dolor":"amet","lorem":"ipsum","sit":"consectetur"}

10.6 Ordenando por chaves em ordem inversa
------------------------------------------

.. code:: php

   use Cajudev\Arrays;

    $arrays = new Arrays([
        'lorem' => 'ipsum',
        'dolor' => 'amet',
        'sit' => 'consectetur'
    ]);
    $arrays->krsort(); //{"sit":"consectetur","lorem":"ipsum","dolor":"amet"}