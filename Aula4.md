# Códigos de status de resposta HTTP
Os códigos de status de resposta HTTP indicam se uma solicitação HTTP específica foi concluída com êxito. As respostas são agrupadas em cinco classes:

- Respostas informativas ( 100- 199)
- Respostas bem-sucedidas ( 200- 299)
- Mensagens de redirecionamento ( 300– 399)
- Respostas de erro do cliente ( 400– 499)
- Respostas de erro do servidor ( 500– 599)

Os códigos de status listados abaixo são definidos pela RFC 9110 .

Observação: se você receber uma resposta que não esteja nesta lista , ela será uma resposta não padrão, possivelmente personalizada para o software do servidor.

### Respostas informativas

100 Continue

    Esta resposta provisória indica que o cliente deve continuar a solicitação ou ignorar a resposta se a solicitação já tiver sido concluída.

101 Switching Protocols

    Este código é enviado em resposta a um Upgradecabeçalho de solicitação do cliente e indica o protocolo para o qual o servidor está mudando.

102 Processing( WebDAV )

    Este código indica que o servidor recebeu e está processando a solicitação, mas ainda não há resposta disponível.

103 Early Hints Experimental
    
    Este código de status destina-se principalmente a ser usado com o Linkcabeçalho, permitindo que o agente do usuário comece a pré-carregar recursos enquanto o servidor prepara uma resposta.

### Respostas bem-sucedidas

200 OK

    A solicitação foi bem-sucedida. O significado do resultado de "sucesso" depende do método HTTP:

        GET: o recurso foi buscado e transmitido no corpo da mensagem.
        HEAD: os cabeçalhos de representação são incluídos na resposta sem qualquer corpo de mensagem.
        PUTou POST: O recurso que descreve o resultado da ação é transmitido no corpo da mensagem.
        TRACE: o corpo da mensagem contém a mensagem de solicitação recebida pelo servidor.

201 Created

    A solicitação foi bem-sucedida e, como resultado, um novo recurso foi criado. Normalmente, esta é a resposta enviada após POSTsolicitações ou algumas PUTsolicitações.

202 Accepted

    A solicitação foi recebida, mas ainda não foi atendida. É evasivo, pois não há como no HTTP enviar posteriormente uma resposta assíncrona indicando o resultado da solicitação. Destina-se aos casos em que outro processo ou servidor trata a solicitação, ou para processamento em lote.

203 Non-Authoritative Information

    Este código de resposta significa que os metadados retornados não são exatamente os mesmos que estão disponíveis no servidor de origem, mas são coletados de uma cópia local ou de terceiros. Isto é usado principalmente para espelhos ou backups de outro recurso. Exceto nesse caso específico, a 200 OKresposta é preferida a este status.

204 No Content

    Não há conteúdo a ser enviado para esta solicitação, mas os cabeçalhos podem ser úteis. O agente do usuário pode atualizar seus cabeçalhos em cache para este recurso com os novos.

205 Reset Content

    Diz ao agente do usuário para redefinir o documento que enviou esta solicitação.

206 Partial Content

    Este código de resposta é usado quando o Rangecabeçalho é enviado do cliente para solicitar apenas parte de um recurso.

207 Multi-Status( WebDAV )
    
    Transmite informações sobre vários recursos, para situações em que vários códigos de status podem ser apropriados.

208 Already Reported( WebDAV )
    
    Usado dentro de um <dav:propstat>elemento de resposta para evitar enumerar repetidamente os membros internos de múltiplas associações à mesma coleção.

226 IM Used( Codificação HTTP Delta )
    
    O servidor atendeu a uma GETsolicitação do recurso e a resposta é uma representação do resultado de uma ou mais manipulações de instância aplicadas à instância atual.

### Mensagens de redirecionamento

300 Multiple Choices

    A solicitação tem mais de uma resposta possível. O agente ou usuário do usuário deve escolher um deles. (Não existe uma forma padronizada de escolher uma das respostas, mas são recomendados links HTML para as possibilidades para que o usuário possa escolher.)

301 Moved Permanently

    A URL do recurso solicitado foi alterada permanentemente. A nova URL é fornecida na resposta.

302 Found

    Este código de resposta significa que o URI do recurso solicitado foi alterado temporariamente . Outras alterações no URI poderão ser feitas no futuro. Portanto, esse mesmo URI deverá ser utilizado pelo cliente em solicitações futuras.

303 See Other

    O servidor enviou esta resposta para direcionar o cliente para obter o recurso solicitado em outro URI com uma solicitação GET.

304 Not Modified

    Isso é usado para fins de cache. Ele informa ao cliente que a resposta não foi modificada, para que o cliente possa continuar a usar a mesma versão em cache da resposta.

305 Use Proxy Descontinuada

    Definido em uma versão anterior da especificação HTTP para indicar que uma resposta solicitada deve ser acessada por um proxy. Ele foi descontinuado devido a questões de segurança relacionadas à configuração em banda de um proxy.

306 unused

    Este código de resposta não é mais usado; é apenas reservado. Foi usado em uma versão anterior da especificação HTTP/1.1.

307 Temporary Redirect

    O servidor envia esta resposta para direcionar o cliente a obter o recurso solicitado em outro URI com o mesmo método usado na solicitação anterior. Tem a mesma semântica do 302 Foundcódigo de resposta HTTP, com a exceção de que o agente do usuário não deve alterar o método HTTP usado: se a POSTfoi usado na primeira solicitação, a POSTdeve ser usado na segunda solicitação.

308 Permanent Redirect

    Isso significa que o recurso agora está permanentemente localizado em outro URI, especificado pelo Location:cabeçalho HTTP Response. Tem a mesma semântica do 301 Moved Permanentlycódigo de resposta HTTP, com a exceção de que o agente do usuário não deve alterar o método HTTP usado: se a POSTfoi usado na primeira solicitação, a POSTdeve ser usado na segunda solicitação.

### Respostas de erro do cliente

400 Bad Request

    O servidor não pode ou não irá processar a solicitação devido a algo que é percebido como um erro do cliente (por exemplo, sintaxe de solicitação malformada, enquadramento de mensagem de solicitação inválido ou roteamento de solicitação enganoso).

401 Unauthorized

    Embora o padrão HTTP especifique "não autorizado", semanticamente esta resposta significa "não autenticado". Ou seja, o cliente deve se autenticar para obter a resposta solicitada.

402 Payment Required Experimental

    Este código de resposta está reservado para uso futuro. O objetivo inicial para a criação deste código era utilizá-lo para sistemas de pagamento digital, no entanto, este código de status é usado muito raramente e não existe nenhuma convenção padrão.

403 Forbidden

    O cliente não possui direitos de acesso ao conteúdo; isto é, não é autorizado, portanto o servidor se recusa a fornecer o recurso solicitado. Ao contrário 401 Unauthorized, a identidade do cliente é conhecida pelo servidor.

404 Not Found

    O servidor não consegue encontrar o recurso solicitado. No navegador, isso significa que o URL não é reconhecido. Em uma API, isso também pode significar que o endpoint é válido, mas o recurso em si não existe. Os servidores também podem enviar esta resposta em vez de 403 Forbiddenocultar a existência de um recurso de um cliente não autorizado. Este código de resposta é provavelmente o mais conhecido devido à sua ocorrência frequente na web.

405 Method Not Allowed

    O método de solicitação é conhecido pelo servidor, mas não é suportado pelo recurso de destino. Por exemplo, uma API pode não permitir chamadas DELETEpara remover um recurso.

406 Not Acceptable

    Esta resposta é enviada quando o servidor web, após realizar a negociação de conteúdo orientada pelo servidor , não encontra nenhum conteúdo que esteja em conformidade com os critérios fornecidos pelo agente do usuário.

407 Proxy Authentication Required

    Isso é semelhante, 401 Unauthorizedmas a autenticação precisa ser feita por um proxy.

408 Request Timeout

    Esta resposta é enviada em conexão ociosa por alguns servidores, mesmo sem nenhuma solicitação prévia do cliente. Isso significa que o servidor gostaria de encerrar esta conexão não utilizada. Esta resposta é muito mais usada porque alguns navegadores, como Chrome, Firefox 27+ ou IE9, usam mecanismos de pré-conexão HTTP para acelerar a navegação. Observe também que alguns servidores simplesmente encerram a conexão sem enviar esta mensagem.

409 Conflict

    Esta resposta é enviada quando uma solicitação entra em conflito com o estado atual do servidor.

410 Gone

    Esta resposta é enviada quando o conteúdo solicitado foi excluído permanentemente do servidor, sem endereço de encaminhamento. Espera-se que os clientes removam seus caches e links para o recurso. A especificação HTTP pretende que este código de status seja usado para "serviços promocionais por tempo limitado". As APIs não devem se sentir obrigadas a indicar recursos que foram excluídos com esse código de status.

411 Length Required

    O servidor rejeitou a solicitação porque o Content-Lengthcampo do cabeçalho não está definido e o servidor exige isso.

412 Precondition Failed

    O cliente indicou pré-condições em seus cabeçalhos que o servidor não atende.

413 Payload Too Large

    A entidade solicitada é maior que os limites definidos pelo servidor. O servidor pode fechar a conexão ou retornar um Retry-Aftercampo de cabeçalho.

414 URI Too Long

    O URI solicitado pelo cliente é mais longo do que o servidor deseja interpretar.

415 Unsupported Media Type

    O formato de mídia dos dados solicitados não é suportado pelo servidor, portanto o servidor está rejeitando a solicitação.

416 Range Not Satisfiable

    O intervalo especificado pelo Rangecampo de cabeçalho na solicitação não pode ser atendido. É possível que o intervalo esteja fora do tamanho dos dados do URI de destino.

417 Expectation Failed

    Este código de resposta significa que a expectativa indicada pelo Expectcampo do cabeçalho da solicitação não pode ser atendida pelo servidor.

418 I'm a teapot

    O garçom recusa a tentativa de preparar café com bule.

421 Misdirected Request

    A solicitação foi direcionada a um servidor que não consegue produzir uma resposta. Isso pode ser enviado por um servidor que não esteja configurado para produzir respostas para a combinação de esquema e autoridade incluída no URI da solicitação.

422 Unprocessable Content( WebDAV )

    A solicitação estava bem formada, mas não pôde ser atendida devido a erros semânticos.

423 Locked( WebDAV )

    O recurso que está sendo acessado está bloqueado.

424 Failed Dependency( WebDAV )

    A solicitação falhou devido à falha de uma solicitação anterior.

425 Too Early Experimental

    Indica que o servidor não está disposto a correr o risco de processar uma solicitação que possa ser reproduzida.

426 Upgrade Required

    O servidor se recusa a executar a solicitação usando o protocolo atual, mas pode estar disposto a fazê-lo após o cliente atualizar para um protocolo diferente. O servidor envia um Upgradecabeçalho em uma resposta 426 para indicar o(s) protocolo(s) necessário(s).

428 Precondition Required

    O servidor de origem exige que a solicitação seja condicional. Esta resposta tem como objetivo evitar o problema de 'atualização perdida', onde um cliente GETaltera o estado do recurso e o PUTenvia de volta ao servidor, quando entretanto um terceiro modifica o estado no servidor, levando a um conflito.

429 Too Many Requests

    O usuário enviou muitas solicitações em um determinado período ("limitação de taxa").

431 Request Header Fields Too Large

    O servidor não está disposto a processar a solicitação porque seus campos de cabeçalho são muito grandes. A solicitação pode ser reenviada após a redução do tamanho dos campos do cabeçalho da solicitação.

451 Unavailable For Legal Reasons

    O agente do usuário solicitou um recurso que não pode ser fornecido legalmente, como uma página da Web censurada por um governo.

### Respostas de erro do servidor

500 Internal Server Error
    
    O servidor encontrou uma situação que não sabe como lidar.

501 Not Implemented

    O método de solicitação não é suportado pelo servidor e não pode ser manipulado. Os únicos métodos que os servidores são obrigados a suportar (e, portanto, que não devem retornar este código) são GETe HEAD.

502 Bad Gateway

    Essa resposta de erro significa que o servidor, enquanto trabalhava como gateway para obter a resposta necessária para tratar a solicitação, obteve uma resposta inválida.

503 Service Unavailable

    O servidor não está pronto para lidar com a solicitação. As causas comuns são um servidor que está fora do ar para manutenção ou sobrecarregado. Observe que junto com esta resposta deverá ser enviada uma página amigável explicando o problema. Esta resposta deve ser utilizada para condições temporárias e o Retry-Aftercabeçalho HTTP deve, se possível, conter o tempo estimado antes da recuperação do serviço. O webmaster também deve tomar cuidado com os cabeçalhos relacionados ao cache que são enviados junto com esta resposta, já que essas respostas de condições temporárias geralmente não devem ser armazenadas em cache.

504 Gateway Timeout

    Esta resposta de erro é dada quando o servidor está agindo como um gateway e não consegue obter uma resposta a tempo.

505 HTTP Version Not Supported

    A versão HTTP usada na solicitação não é suportada pelo servidor.

506 Variant Also Negotiates

    O servidor tem um erro de configuração interno: o recurso variante escolhido está configurado para se envolver na negociação de conteúdo transparente e, portanto, não é um ponto final adequado no processo de negociação.

507 Insufficient Storage( WebDAV )

    O método não pôde ser executado no recurso porque o servidor não consegue armazenar a representação necessária para concluir a solicitação com êxito.

508 Loop Detected( WebDAV )

    O servidor detectou um loop infinito ao processar a solicitação.

510 Not Extended

    Outras extensões da solicitação são necessárias para que o servidor a atenda.

511 Network Authentication Required

    Indica que o cliente precisa se autenticar para obter acesso à rede.