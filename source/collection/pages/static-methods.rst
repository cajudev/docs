=====================
15. Métodos Estáticos
=====================

15.1 isCollection
-------------

Verifica se dado objeto é uma instância da classe Arrays ou que extenda dela

.. code:: php

   use Cajudev\Collection;

   Collection::isCollection(new Collection()); // true

   Collection::isCollection(10); // false

15.2 Combine
-------------

Combina dois arrays em um novo objeto, utilizando o primeiro para chaves e o segundo para valores.
Ambos os argumentos podem ser simples arrays ou objetos dessa classe.

.. code:: php

   use Cajudev\Collection;

   $array = ['lorem', 'ipsum', 'dolor'];

   $collection = new Collection([1, 2, 3]);

   $result = Collection::combine($array, $collection);

   echo $result; // {"lorem":1,"ipsum":2,"dolor":3}

