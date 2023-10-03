# A História do HTTP

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