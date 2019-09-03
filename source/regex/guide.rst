===============
Guia do Usuário
===============

------------------
1. Casando padrões
------------------

.. code:: php
    
    $regex = new \Cajudev\Regex('/\w/');

    if ($regex->match('Lorem')) {  // true
        $regex->get(); // 'L'
    }

---------------------
2. Performance Global
---------------------

.. code:: php
    
    $regex = new \Cajudev\Regex('/\w/g'); // repare no modificador aqui

    if ($regex->match('Lorem')) {  // true
        $regex->get(); // ['L', 'o', 'r', 'e', 'm'];
    }

---------------
3. Substituição
---------------

.. code:: php
    
    $regex = new \Cajudev\Regex('/[aeiou]/');

    $regex->replace('lorem', '@'); // l@r@m

--------------------
4. Divisão em partes
--------------------

.. code:: php
    
    $regex = new \Cajudev\Regex('/[aeiou]/');

    $regex->split('lorem'); // ['l', 'r', 'm'];

-------------------------
5. Tratamento de Exceções
-------------------------

.. code:: php
    
    try {
        $regex = new \Cajudev\Regex('/\w'); // repare que a regex não foi fechada
    } catch (\Cajudev\RegularExpressionException $e) {
        echo $e->getMessage(); // No ending delimiter '/' found
    }