# Cookies e sessões

### Pra que servem cookies e sessões:

O protocolo HTTP é stateless, ou seja, ele não mantém um estado/conexão. Toda a interação que o seu cliente fizer com um servidor web acarretará em uma nova requisição e resposta.
As requisições são independentes e possuem um tempo de vida (conexão, envio de mensagem, resposta, encerramento da conexão). O servidor web não é capaz de identificar se duas requisições vieram de um mesmo navegador, e o mesmo não faz nenhum gerenciamento em memória para que mensagens sejam compartilhadas entre requisições.
É para suprir esta necessidade que entram os cookies e sessões.

### Cookies:

Tecnicamente falando, um cookie é uma pequena quantidade de informação persistida temporariamente pelo navegador. Os navegadores normalmente limitam o tamanho dos cookies em até 4KB, e apagam cookies com a data de “validade vencida”.
Através de cookies o servidor web é capaz de trocar informações de estado com o navegador do usuário.
Assim podemos por exemplo fazer compras online adicionando produtos a um carrinho, se não houvessem os cookies as informações do carrinho seriam perdidas ao mudarmos de página.

Exemplo de cookie feito utilizando-se do PHP:

    <?php
        // cookies.php
    ​
        if (isset($_COOKIE['cookie_teste'])) {
            echo 'Você JÁ passou por aqui!';
        } else {
            echo 'Você NUNCA passou por aqui.';
            setcookie('cookie_teste', 'Algum valor...', time() + 3600);
        }
    ?>


Aqui ao entrarmos em uma página o código verifica se o cookie existe, caso não exista o cookie é criado.
Vale ressaltar que nesse nosso exemplo o cookie tem duração de 3600 segundos.

### Sessions:

As sessões têm um princípio similar aos cookies, só que o armazenamento do estado é feito pelo servidor web, e não pelo navegador.
Por exemplo, quando construímos uma aplicação que necessita de autenticação, no momento em que o usuário efetuar o login, podemos até permitir que algumas informações sejam armazenadas em um cookie, mas dados mais “sensíveis”, como usuário e e-mail, são mais interessantes de serem guardadas em sessões. Isto, pois não é seguro que esse tipo de informação fique “viajando” pela web.
Mas se o HTTP é stateless, e o servidor web não tem como identificar que a requisição anterior veio do meu browser, como é que ele sabe que as informações que eu guardei em sessão são de fato minhas? Simples… através de cookies!

Quando iniciamos uma sessão, é enviado um cookie para o navegador, com um valor único que corresponde a sessão aberta no servidor web. Vamos ilustrar através do exemplo abaixo:

    <?php
        // sessions.php
    ​
        session_start();
    ​
        if (isset($_SESSION['usuario'])) {
            echo "Bem vindo {$_SESSION['usuario']}!";
        } else {
            echo 'Você NUNCA passou por aqui.';
            $_SESSION['usuario'] = 'João';
        }
    ?>


O código acima inicia uma sessão através do método session_start. Na primeira visita, será criado um índice usuario com o valor João.

Quando visitarmos o sessions.php novamente, o navegador informará ao servidor que ele possui um cookie chamado PHPSESSID. A partir daí o PHP pega o valor deste cookie, recupera a sessão da memória (ou de um banco de dados, ou arquivos em disco) e atribui este valor ao array global $_SESSION.