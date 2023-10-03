# Versões do HTTP

## Evolução do HTTP

HTTP (HyperText Transfer Protocol) é o protocolo subjacente da World Wide Web. Desenvolvido por Tim Berners-Lee e sua equipe entre 1989-1991, o HTTP passou por muitas mudanças que ajudaram a manter sua simplicidade e ao mesmo tempo moldar sua flexibilidade. Continue lendo para saber como o HTTP evoluiu de um protocolo projetado para troca de arquivos em um ambiente de laboratório semiconfiável para um moderno labirinto de internet que transporta imagens e vídeos em alta resolução e 3D.

## Invenção da World Wide Web

Em 1989, enquanto trabalhava no CERN, Tim Berners-Lee escreveu uma proposta para construir um sistema de hipertexto na Internet. Inicialmente chamado de Mesh , mais tarde foi renomeado como World Wide Web durante sua implementação em 1990. Construído sobre os protocolos TCP e IP existentes, consistia em 4 blocos de construção:

- Um formato textual para representar documentos de hipertexto, a HyperText Markup Language (HTML).
- Um protocolo simples para troca desses documentos, o HyperText Transfer Protocol (HTTP).
- Um cliente para exibir (e editar) esses documentos, o primeiro navegador chamado WorldWideWeb .
- Um servidor para dar acesso ao documento, uma versão anterior do httpd .
Esses quatro blocos de construção foram concluídos no final de 1990, e os primeiros servidores estavam rodando fora do CERN no início de 1991. Em 6 de agosto de 1991, Tim Berners-Lee postou no grupo de notícias público alt.hypertext . Este é agora considerado o início oficial da World Wide Web como um projeto público.

O protocolo HTTP usado nessas fases iniciais era muito simples. Posteriormente, foi apelidado de HTTP/0.9 e às vezes é chamado de protocolo de uma linha.

## HTTP/0.9 – O protocolo de uma linha

A versão inicial do HTTP não tinha número de versão; mais tarde foi chamado de 0.9 para diferenciá-lo das versões posteriores. O HTTP/0.9 era extremamente simples: as solicitações consistiam em uma única linha e começavam com o único método possível GETseguido do caminho para o recurso. O URL completo não foi incluído porque o protocolo, o servidor e a porta não eram necessários depois de conectado ao servidor.

Solicitacao

    GET /mypage.html

A resposta também foi extremamente simples: consistia apenas no próprio arquivo.

Resposta

    <html>
    A very simple HTML page
    </html>

Ao contrário das evoluções subsequentes, não houve cabeçalhos HTTP. Isso significava que apenas arquivos HTML poderiam ser transmitidos. Não houve status ou códigos de erro. Caso houvesse algum problema, um arquivo HTML específico era gerado e incluía uma descrição do problema para consumo humano.

## HTTP/1.0 – Construindo extensibilidade

O HTTP/0.9 era muito limitado, mas navegadores e servidores rapidamente o tornaram mais versátil:

- As informações de versão foram enviadas em cada solicitação ( HTTP/1.0foram anexadas à GETlinha).
- Uma linha de código de status também foi enviada no início de uma resposta. Isso permitiu que o próprio navegador reconhecesse o sucesso ou o fracasso de uma solicitação e adaptasse seu comportamento de acordo. Por exemplo, atualizando ou usando seu cache local de uma forma específica.
- O conceito de cabeçalhos HTTP foi introduzido tanto para solicitações quanto para respostas. Os metadados puderam ser transmitidos e o protocolo tornou-se extremamente flexível e extensível.
- Documentos diferentes de arquivos HTML simples podem ser transmitidos graças ao Content-Typecabeçalho.

Neste momento, uma solicitação e resposta típicas eram assim:

Solicitacao

    GET /mypage.html HTTP/1.0
    User-Agent: NCSA_Mosaic/2.0 (Windows 3.1)

Resposta

    200 OK
    Date: Tue, 15 Nov 1994 08:12:31 GMT
    Server: CERN/3.0 libwww/2.17
    Content-Type: text/html
    <HTML>
    A page with an image
    <IMG SRC="/myimage.gif">
    </HTML>

Foi seguida por uma segunda conexão e uma solicitação para buscar a imagem (com a resposta correspondente):

Solicitacao

    GET /myimage.gif HTTP/1.0
    User-Agent: NCSA_Mosaic/2.0 (Windows 3.1)

Resposta

    200 OK
    Date: Tue, 15 Nov 1994 08:12:32 GMT
    Server: CERN/3.0 libwww/2.17
    Content-Type: text/gif
    (image content)

Entre 1991-1995, estes foram introduzidos com uma abordagem de tentativa e ver. Um servidor e um navegador adicionariam um recurso e veriam se ele ganhava força. Problemas de interoperabilidade eram comuns. Em um esforço para resolver esses problemas, um documento informativo que descreveu as práticas comuns foi publicado em novembro de 1996. Ele era conhecido como RFC 1945 e definia HTTP/1.0.

## HTTP/1.1 – O protocolo padronizado

Enquanto isso, a padronização adequada estava em andamento. Isso aconteceu paralelamente às diversas implementações do HTTP/1.0. A primeira versão padronizada do HTTP, HTTP/1.1, foi publicada no início de 1997, apenas alguns meses depois do HTTP/1.0.

HTTP/1.1 esclareceu ambiguidades e introduziu inúmeras melhorias:

- Uma conexão poderia ser reutilizada, o que economizava tempo. Já não precisava de ser aberto várias vezes para exibir os recursos incorporados no único documento original.
- Pipelining foi adicionado. Isso permitiu que uma segunda solicitação fosse enviada antes que a resposta à primeira fosse totalmente transmitida. Isso reduziu a latência da comunicação.
- Respostas fragmentadas também foram suportadas.
- Mecanismos adicionais de controle de cache foram introduzidos.
- A negociação de conteúdo, incluindo idioma, codificação e tipo, foi introduzida. Um cliente e um servidor agora poderiam concordar sobre qual conteúdo trocar.
- Graças ao **Host** cabeçalho, a capacidade de hospedar diferentes domínios do mesmo endereço IP permitiu a colocação de servidores.
Um fluxo típico de solicitações, através de uma única conexão, era assim:

Solicitacao

    GET /en-US/docs/Glossary/Simple_header HTTP/1.1
    Host: developer.mozilla.org
    User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate, br
    Referer: https://developer.mozilla.org/en-US/docs/Glossary/Simple_header

Resposta

    200 OK
    Connection: Keep-Alive
    Content-Encoding: gzip
    Content-Type: text/html; charset=utf-8
    Date: Wed, 20 Jul 2016 10:55:30 GMT
    Etag: "547fa7e369ef56031dd3bff2ace9fc0832eb251a"
    Keep-Alive: timeout=5, max=1000
    Last-Modified: Tue, 19 Jul 2016 00:59:33 GMT
    Server: Apache
    Transfer-Encoding: chunked
    Vary: Cookie, Accept-Encoding

    (content)

Solicitacao

    GET /static/img/header-background.png HTTP/1.1
    Host: developer.mozilla.org
    User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
    Accept: */*
    Accept-Language: en-US,en;q=0.5
    Accept-Encoding: gzip, deflate, br
    Referer: https://developer.mozilla.org/en-US/docs/Glossary/Simple_header

Resposta

    200 OK
    Age: 9578461
    Cache-Control: public, max-age=315360000
    Connection: keep-alive
    Content-Length: 3077
    Content-Type: image/png
    Date: Thu, 31 Mar 2016 13:34:46 GMT
    Last-Modified: Wed, 21 Oct 2015 18:27:50 GMT
    Server: Apache

    (image content of 3077 bytes)

HTTP/1.1 foi publicado pela primeira vez como RFC 2068 em janeiro de 1997.

## Mais de 15 anos de extensões

A extensibilidade do HTTP facilitou a criação de novos cabeçalhos e métodos. Embora o protocolo HTTP/1.1 tenha sido refinado em duas revisões, RFC 2616 publicada em junho de 1999 e RFC 7230 - RFC 7235 publicada em junho de 2014 antes do lançamento do HTTP/2, ele permaneceu extremamente estável por mais de 15 anos.

### Usando HTTP para transmissões seguras

A maior mudança no HTTP foi feita no final de 1994. Em vez de enviar HTTP através de uma pilha TCP/IP básica, a empresa de serviços de informática Netscape Communications criou uma camada adicional de transmissão criptografada: SSL. O SSL 1.0 nunca foi lançado ao público, mas o SSL 2.0 e seu sucessor, o SSL 3.0, permitiram a criação de sites de comércio eletrônico. Para isso, criptografaram e garantiram a autenticidade das mensagens trocadas entre servidor e cliente. O SSL acabou sendo padronizado e tornou-se TLS.

Durante o mesmo período, ficou claro que era necessária uma camada de transporte criptografada. A web deixou de ser uma rede predominantemente acadêmica e, em vez disso, tornou-se uma selva onde anunciantes, indivíduos aleatórios e criminosos competiam pelo máximo de dados privados possível. À medida que os aplicativos desenvolvidos sobre HTTP se tornaram mais poderosos e exigiam acesso a informações privadas, como catálogos de endereços, e-mail e localização do usuário, o TLS tornou-se necessário fora do caso de uso de comércio eletrônico.

### Usando HTTP para aplicativos complexos

Tim Berners-Lee originalmente não imaginou o HTTP como um meio somente leitura. Ele queria criar uma web onde as pessoas pudessem adicionar e mover documentos remotamente – uma espécie de sistema de arquivos distribuído. Por volta de 1996, o HTTP foi estendido para permitir a autoria e um padrão chamado WebDAV foi criado. Ele cresceu para incluir aplicativos específicos como CardDAV para lidar com entradas do catálogo de endereços e CalDAV para lidar com calendários. Mas todas essas extensões *DAV tinham uma falha: elas só eram utilizáveis ​​quando implementadas pelos servidores.

Em 2000, um novo padrão para uso de HTTP foi projetado: transferência de estado representacional (ou REST). A API não era baseada nos novos métodos HTTP, mas sim no acesso a URIs específicos com métodos HTTP/1.1 básicos. Isso permitiu que qualquer aplicativo da web permitisse que uma API recuperasse e modificasse seus dados sem precisar atualizar os navegadores ou servidores. Todas as informações necessárias foram incorporadas nos arquivos que os sites veiculavam através do padrão HTTP/1.1. A desvantagem do modelo REST era que cada site definia sua própria API RESTful fora do padrão e tinha controle total sobre ela. Isso diferia das extensões *DAV, onde clientes e servidores eram interoperáveis. APIs RESTful tornaram-se muito comuns na década de 2010.

Desde 2005, mais APIs foram disponibilizadas para páginas da web. Várias dessas APIs criam extensões para o protocolo HTTP para fins específicos:

- **Eventos enviados pelo servidor** , onde o servidor pode enviar mensagens ocasionais para o navegador.
- **WebSocket** , um novo protocolo que pode ser configurado atualizando uma conexão HTTP existente.

### Relaxando o modelo de segurança da web

O HTTP é independente do modelo de segurança da web, conhecido como política de mesma origem . Na verdade, o modelo atual de segurança web foi desenvolvido após a criação do HTTP! Ao longo dos anos, revelou-se útil levantar algumas restrições desta política sob certas restrições. O servidor transmitiu ao cliente quanto e quando suspender tais restrições usando um novo conjunto de cabeçalhos HTTP. Eles foram definidos em especificações como Cross-Origin Resource Sharing (CORS) e Content Security Policy (CSP).

Além dessas grandes extensões, muitos outros cabeçalhos foram adicionados, às vezes apenas experimentalmente. Cabeçalhos notáveis ​​são o cabeçalho Do Not Track ( DNT) para controlar a privacidade, X-Frame-Optionse Upgrade-Insecure-Requestsmuitos mais existem.

## HTTP/2 – Um protocolo para maior desempenho

Com o passar dos anos, as páginas da web se tornaram mais complexas. Alguns deles eram até aplicativos por direito próprio. Mais mídias visuais foram exibidas e o volume e o tamanho dos scripts agregando interatividade também aumentaram. Muito mais dados foram transmitidos por meio de um número significativamente maior de solicitações HTTP e isso criou mais complexidade e sobrecarga para conexões HTTP/1.1. Para dar conta disso, o Google implementou um protocolo experimental SPDY no início de 2010. Essa forma alternativa de troca de dados entre cliente e servidor despertou o interesse de desenvolvedores que trabalham tanto em navegadores quanto em servidores. O SPDY definiu um aumento na capacidade de resposta e resolveu o problema de transmissão duplicada de dados, servindo de base para o protocolo HTTP/2.

O protocolo HTTP/2 difere do HTTP/1.1 em alguns aspectos:

- É um protocolo binário em vez de um protocolo de texto. Não pode ser lido e criado manualmente. Apesar deste obstáculo, permite a implementação de técnicas de otimização melhoradas.
- É um protocolo multiplexado. Solicitações paralelas podem ser feitas na mesma conexão, removendo as restrições do protocolo HTTP/1.x.
- Ele compacta cabeçalhos. Como muitas vezes são semelhantes entre um conjunto de solicitações, isso elimina a duplicação e a sobrecarga dos dados transmitidos.
- Ele permite que um servidor preencha dados em um cache do cliente por meio de um mecanismo chamado server push.

Oficialmente padronizado em maio de 2015, o uso de HTTP/2 atingiu o pico em janeiro de 2022, em 46,9% de todos os sites (veja estas estatísticas ). Sites de alto tráfego mostraram a adoção mais rápida em um esforço para economizar despesas gerais de transferência de dados e orçamentos subsequentes.

Essa rápida adoção ocorreu provavelmente porque o HTTP/2 não exigia alterações em sites e aplicativos. Para utilizá-lo era necessário apenas um servidor atualizado e que se comunicasse com um navegador recente. Apenas um conjunto limitado de grupos foi necessário para desencadear a adoção e, à medida que as versões legadas de navegadores e servidores foram renovadas, o uso aumentou naturalmente, sem trabalho significativo para os desenvolvedores web.

## Evolução pós-HTTP/2

A extensibilidade do HTTP ainda está sendo usada para adicionar novos recursos. Notavelmente, podemos citar novas extensões do protocolo HTTP que surgiram em 2016:

- O suporte Alt-Svcpermitiu a dissociação da identificação e da localização de um determinado recurso. Isso significou um mecanismo de cache CDN mais inteligente .
- A introdução de dicas de cliente permitiu que o navegador ou cliente comunicasse proativamente informações sobre seus requisitos e restrições de hardware ao servidor.
- A introdução de prefixos relacionados à segurança no Cookiecabeçalho ajudou a garantir que os cookies seguros não pudessem ser alterados.

## HTTP/3 - HTTP sobre QUIC

A próxima versão principal do HTTP, HTTP/3, tem a mesma semântica das versões anteriores do HTTP, mas usa QUIC em vez de TCP para a parte da camada de transporte. Em outubro de 2022, 26% de todos os sites usavam HTTP/3 .

O QUIC foi projetado para fornecer latência muito menor para conexões HTTP. Assim como o HTTP/2, é um protocolo multiplexado, mas o HTTP/2 é executado em uma única conexão TCP, portanto, a detecção de perda de pacotes e a retransmissão tratadas na camada TCP podem bloquear todos os fluxos. O QUIC executa vários fluxos sobre UDP e implementa detecção e retransmissão de perda de pacotes independentemente para cada fluxo, de modo que, se ocorrer um erro, apenas o fluxo com dados nesse pacote seja bloqueado.

Definido na RFC 9114 , o HTTP/3 é compatível com a maioria dos principais navegadores, incluindo Chromium (e suas variantes como Chrome e Edge) e Firefox.