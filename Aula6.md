# O que é HTTPS?

HTTPS (Protocolo de transferência de hipertexto seguro) é uma versão segura do protocolo HTTP que usa o SSL /TLS protocolo para criptografia e autenticação. HTTPS é especificado por RFC 2818 (Maio de 2000) e usa a porta 443 por padrão em vez da porta 80 do HTTP.

O protocolo HTTPS possibilita que os usuários do site transmitam dados confidenciais, como números de cartão de crédito, informações bancárias e credenciais de login com segurança pela Internet. Por esse motivo, HTTPS é especialmente importante para proteger atividades online, como compras, transações bancárias e trabalho remoto. No entanto, HTTPS está se tornando rapidamente o protocolo padrão para todos os sites, trocando ou não dados confidenciais com os usuários.

### Como o HTTPS é diferente do HTTP?

HTTPS adiciona criptografia, autenticaçãoe integridade para o protocolo HTTP:

Criptografia: 

    Como o HTTP foi originalmente projetado como um protocolo de texto não criptografado, ele é vulnerável a escutas e homem no meio ataques. Incluindo SSL /TLS criptografia, o HTTPS evita que os dados enviados pela Internet sejam interceptados e lidos por terceiros. Através criptografia de chave pública e a SSL /TLS aperto de mão, uma sessão de comunicação criptografada pode ser configurada com segurança entre duas partes que nunca se encontraram pessoalmente (por exemplo, um servidor da web e um navegador) por meio da criação de uma chave secreta compartilhada.

Autenticação: 

    Ao contrário do HTTP, o HTTPS inclui autenticação robusta via SSL /TLS protocolo. SSL / de um siteTLS certificado inclui um chave pública que um navegador da web pode usar para confirmar que os documentos enviados pelo servidor (como páginas HTML) foram assinados digitalmente por alguém em posse do correspondente chave privada. Se o certificado do servidor foi assinado por um publicamente confiável autoridade de certificação (CA), como SSL.com, o navegador aceitará que qualquer informação de identificação incluída no certificado tenha sido validada por um terceiro confiável.
    Sites HTTPS também podem ser configurados para autenticação mútua, no qual um navegador da web apresenta um certificado de cliente identificando o usuário. A autenticação mútua é útil para situações como trabalho remoto, onde é desejável incluir autenticação multifator, reduzindo o risco de Phishing ou outros ataques envolvendo roubo de credencial. Para obter mais informações sobre a configuração de certificados de cliente em navegadores da web, leia este tutorial.

Integridade: 
    
    Cada documento (como uma página da web, imagem ou arquivo JavaScript) enviado a um navegador por um servidor da web HTTPS inclui uma assinatura digital que um navegador da web pode usar para determinar se o documento não foi alterado por um terceiro ou de outra forma corrompido durante o trânsito. O servidor calcula um hash criptográfico do conteúdo do documento, incluído com seu certificado digital, que o navegador pode calcular de forma independente para provar que a integridade do documento está intacta.
    Juntas, essas garantias de criptografia, autenticação e integridade tornam o HTTPS um muito protocolo mais seguro para navegar e conduzir negócios na web do que HTTP.

### Que informações o HTTPS fornece aos usuários sobre os proprietários de sites?

CAs usam três métodos de validação ao emitir certificados digitais. O método de validação usado determina as informações que serão incluídas no SSL / de um siteTLS certificado:

- Validação de domínio (DV) simplesmente confirma que o nome de domínio coberto pelo certificado está sob o controle da entidade que solicitou o certificado.
- Organização / Validação Individual (OV / IV) os certificados incluem o nome validado de uma empresa ou outra organização (OV), ou de uma pessoa individual (IV).
- Extended Validation (EV) Os certificados representam o mais alto padrão de confiança na Internet e exigem o máximo esforço da CA para validar. Os certificados EV são emitidos apenas para empresas e outras organizações registradas, não para indivíduos, e incluem o nome validado dessa organização.


### Por que usar HTTPS?
Existem vários bons motivos para usar HTTPS em seu site e insistir no HTTPS ao navegar, fazer compras e trabalhar na web como um usuário:

Integridade e autenticação: 

    Por meio de criptografia e autenticação, o HTTPS protege a integridade da comunicação entre um site e os navegadores de um usuário. Seus usuários saberão que os dados enviados de seu servidor web não foram interceptados e / ou alterados por terceiros em trânsito. E, se você fez o investimento extra em certificados EV ou OV, eles também serão capazes de dizer que as informações realmente veio de sua empresa ou organização.

Privacidade: 

    É claro que ninguém quer que intrusos coloquem seus números de cartão de crédito e senhas enquanto fazem compras ou realizam transações bancárias online, e HTTPS é ótimo para evitar isso. Mas você clientes deseja que tudo o mais que você veja e faça na web seja um livro aberto para qualquer pessoa que queira espionar (incluindo governos, empregadores ou alguém que esteja criando um perfil para anonimizar suas atividades online)? HTTPS também desempenha um papel importante aqui.

Experiência de usuário: 

    Mudanças recentes na IU do navegador resultaram em sites HTTP sendo sinalizados como inseguro. Você deseja que os navegadores de seus clientes informem a eles que seu site não é seguro ou mostrem um cadeado riscado quando o visitarem? Claro que não!

Compatibilidade: 

    As alterações atuais do navegador estão levando o HTTP cada vez mais perto da incompatibilidade. Mozilla Firefox anunciou recentemente um opcional Modo somente HTTPS, enquanto o Google Chrome está se movendo constantemente para bloquear conteúdo misto (Recursos HTTP vinculados a páginas HTTPS). Quando visto junto com os avisos do navegador de “insegurança” para sites HTTP, é fácil ver que a escrita está na parede para HTTP. Em 2020, todos os principais navegadores e dispositivos móveis atuais suportam HTTPS, então você não perderá usuários ao mudar de HTTP.

SEO: 

    Os mecanismos de pesquisa (incluindo o Google) usam HTTPS como um sinal de classificação ao gerar resultados de pesquisa. Portanto, os proprietários de sites podem obter um impulso de SEO fácil apenas configurando seus servidores da Web para usar HTTPS em vez de HTTP.

Resumindo, não há mais bons motivos para os sites públicos continuarem a oferecer suporte a HTTP. Mesmo a Governo dos Estados Unidos está a bordo!

### Como o HTTPS funciona?

HTTPS adiciona criptografia para o protocolo HTTP envolvendo o HTTP dentro do SSL /TLS protocolo (é por isso que SSL é chamado de protocolo de túnel), para que todas as mensagens sejam criptografadas em ambas as direções entre dois computadores em rede (por exemplo, um cliente e um servidor web). Embora um intruso ainda possa acessar endereços IP, números de portas, nomes de domínio, a quantidade de informações trocadas e a duração de uma sessão, todos os dados reais trocados são criptografados com segurança por SSL /TLS, Incluindo:

- URL de solicitação (qual página da web foi solicitada pelo cliente)
- Conteúdo do site
- Parâmetros de consulta
- Cabeçalhos
- Cookies

HTTPS também usa SSL /TLS protocolo para autenticação. SSL /TLS usa documentos digitais conhecidos como Certificados X.509 ligar criptográfico pares de chaves às identidades de entidades como sites, indivíduos e empresas. Cada par de chaves inclui um chave privada, que é mantido seguro e um chave pública, que pode ser amplamente distribuído. Qualquer pessoa com a chave pública pode usá-la para:

- Envie uma mensagem que apenas o possuidor da chave privada pode descriptografar.
- Confirme se uma mensagem foi assinada digitalmente por sua chave privada correspondente.

Se o certificado apresentado por um site HTTPS tiver sido assinado por uma empresa de confiança pública autoridade de certificação (CA), Tais como SSL.com, os usuários podem ter certeza de que a identidade do site foi validada por terceiros confiáveis ​​e rigorosamente auditados.

### O que acontece se meu site não usar HTTPS?

Em 2020, sites que não usam HTTPS ou servem conteúdo misto (servindo recursos como imagens via HTTP de páginas HTTPS) estão sujeitos a avisos e erros de segurança do navegador. Além disso, esses sites comprometem desnecessariamente a privacidade e a segurança de seus usuários e não são preferidos por algoritmos de mecanismo de pesquisa. Portanto, sites HTTP e de conteúdo misto podem esperar mais avisos e erros do navegador, menor confiança do usuário e SEO mais pobre do que se eles tivessem habilitado HTTPS.

### Como posso saber se um site usa HTTPS?

Um URL HTTPS começa com https:// em vez de http://. Navegadores modernos também indicam que um usuário está visitando um site HTTPS seguro exibindo um símbolo de cadeado fechado à esquerda da URL.
Em navegadores modernos como Chrome, Firefox e Safari, os usuários podem clique no cadeado para ver se o certificado digital de um site HTTPS inclui identificando informações sobre seu dono.

### Como habilito o HTTPS em meu site?

Para proteger um site público com HTTPS, é necessário instalar um SSL /TLS certificado assinado por um publicamente confiável autoridade de certificação (CA) no seu servidor web. SSL.com's Base de Conhecimento inclui muitos guias úteis e instruções para configurar uma ampla variedade de plataformas de servidor da web para oferecer suporte a HTTPS.