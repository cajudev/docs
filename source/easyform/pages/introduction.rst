=============
1. Introdução
=============

1.1 Fundamentos
---------------

O primeiro passo para entender a motivação e o funcionamento dessa biblioteca é pensar que
geralmente, elementos de formulário possuem estruturas padronizadas.

.. note::

   Para todos os exemplos que serão mostrados, o uso do framework **bootstrap** estará presente,
   porém a biblioteca não possui nenhum tipo de vinculo ou limitação em relação a isso.

Nesse primeiro exemplo, vamos tomar como principio que uma tag input, geralmente vem precedida
de uma tag label.

Em HTML sua estrutura seria algo como:

.. code-block:: html

   <label for="username">Nome de Usuário</label>
   <input id="username" type="text" class="form-control">

Colocaremos isso dentro de uma estrutura básica HTML e veremos sua renderização na tela

Pode pode realizar o download dos arquivos de exemplo clicando aqui_:

.. code-block:: html

   <!DOCTYPE html>
   <html lang="pt-br">
   <head>
      <title>Easy Form</title>
      <meta charset="utf-8" />
      <link
         rel="stylesheet"
         href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css"
         integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T"
         crossorigin="anonymous"
      />
      <link rel="stylesheet" href="style.css" />
   </head>
   <body>
      <div class="container mt-5">
         <div class="title-container">
            <h1 class="title">Guia do Usuário Easy Form</h1>
         </div>
         <form>
            <label for="username">Nome de Usuário</label>
            <input id="username" type="text" class="form-control" />
         </form>
      </div>
   </body>
   </html>

Resultado:

.. raw:: html

   <div class="container mb-4">
      <div class="title-container">
         <h1 class="title">Guia do Usuário Easy Form</h1>
      </div>
      <form>
         <label for="username">Nome de Usuário</label>
         <input id="username" type="text" class="form-control" />
      </form>
   </div>

Agora removeremos o formulário do HTML deixando uma tag como referência para ser substituída pelo back end.
Esse trabalho geralmente é feito usando um template engine, no nosso caso utilizaremos o twig_, mas fique a 
vontade para escolher outro.



.. _aqui: http://www.google.com.br/
.. _twig: https://twig.symfony.com/

