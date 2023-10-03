# O que é HTTP?

HTTP e um tipo de protocolo que transmite a linguagem HTML, sendo um tipo de requisição feita pelo usuário em navegadores web.

**Requests ou requisições** e o nome dado a solicitação do usuário

**Responses ou respostas** e o nome dado as respostas do servidor

É possível fazer requisições especificas de partes de documentos com HTTP, nao sei bem, talvez um vídeo dentro de uma pagina, como funciona o YT.

**TCP - Protocolo de Controle de Transmissao*

**TLS - Transport Layer Security* 

**SSL - Secure Scokets Layer*

## Agente usuário

Qualquer requisicao é sempre iniciada por um agente usuário. Ainda que hajam formas de simular uma requisicao iniciada pelo servidor (Exemplos?)

As requisicoes sao feitas usando o endereco de cada documento que é armazenado no servidor e por isso podemos colocar links dentro dos HTMLs, para poder fazer outra requisicao e acessar esse outro doc. Acredito que isso funcione tambem para areas fechadas de um site, para que somente quem tem acesso a certas areas podem acessar os documentos (HTMLs) destinados a certos grupos.

## Servidores

Os servidores sao maquinas virtuais que armazenam os documentos, que em sua maior parte sao HTML, mas dentro desses arquivos de HTML podem conter videos, imagens, formularios e etc.

Um servidor tambem pode ser dividido em varias maquinas e dividir a carga necessaria de empresas gigantescas.

## Proxies

Proxies sao os intermediarios, representantes ou ate mesmo mensageiros silenciosos. Estao inseridos de maneira fisica (exemplo sao os modens e roteadores) na rede e como transporte de informacao.

- cacheamento (o *cache* pode ser público ou privado, como o *cache* dos navegadores)
- filtragem (como um *scanner* de antivírus, controle de acesso, etc)
- balanceamento de carga (para permitir que vários servidores possam responder a diferentes requisições)
- autenticação (para controlar quem tem acesso aos recursos)
- autorização (para controlar quem tem acesso a determinada informação)
- registro de informação (permite o armazenamento de informações de histórico)

## Fluxo do HTTP

Quando o cliente quer comunicar com um servidor, este sendo um servidor final ou um proxy, ele realiza os seguintes passos:

1. Abre uma conexão TCP: A conexão TCP será usada para enviar uma requisição, ou várias, e receber uma resposta. O cliente pode abrir uma nova conexão, reusar uma conexão existente, ou abrir várias conexões aos servidores.
2. Envia uma mensagem HTTP: mensagens HTTP (antes do HTTP/2.0) são legíveis às pessoas. Com o HTTP/2.0, essas mensagens simples são encapsuladas dentro de quadros (frames), tornando-as impossíveis de ler diretamente, mas o princípio se mantém o mesmo.
    
    Solicitacao

        GET / HTTP/1.1
        Host: developer.mozilla.org
        Accept-Language: fr

3. Lê a resposta do servidor:
    
    Resposta

        HTTP/1.1 200 OK
        Date: Sat, 09 Oct 2010 14:28:02 GMT
        Server: Apache
        Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
        ETag: "51142bc1-7449-479b075b2891b"
        Accept-Ranges: bytes
        Content-Length: 29769
        Content-Type: text/html
        <!DOCTYPE html... (here comes the 29769 bytes of the requested web page)

4. Fecha ou reutiliza a conexão para requisições futuras.

Se a linha de montagem (pipelining) estiver ativada, várias requisições podem ser enviadas sem que a primeira resposta seja totalmente recebida. A linha de montagem HTTP se provou difícil de ser implementada nas redes existentes, onde peças antigas de software coexistem com versões modernas. A linha de montagem HTTP tem sido substituída no HTTP/2.0 com multiplexação mais robusta de requisições dentro de um quadro (frame).