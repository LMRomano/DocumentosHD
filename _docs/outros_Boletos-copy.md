---
title: Teste de Markdown
category: Teste - Cielo
order: 1
---


### O que &eacute; Boleto Registrado?

O **Boleto Registrado** &eacute; um dos meios de pagamentos disponibilizados no E-commerce. Com o objetivo de mitigar fraudes, a Febraban em conjunto com os Bancos desenvolveu a modalidade registrada, tendo um controle centralizado de todos os boletos emitidos.

### Qual o benef&iacute;cio em utiliz&aacute;-lo?

A Cobran&ccedil;a Registrada foi desenvolvida para promover maior confiabilidade e seguran&ccedil;a na compra online. O banco emissor tem conhecimento do boleto desde sua gera&ccedil;&atilde;o at&eacute; sua liquida&ccedil;&atilde;o. O lojista tem a op&ccedil;&atilde;o de negativar o comprador que gerou e n&atilde;o pagou uma cobran&ccedil;a registrada.

Esta modalidade de cobran&ccedil;a permite que o comprador efetue o pagamento do boleto em qualquer ag&ecirc;ncia banc&aacute;ria mesmo depois do vencimento.

### Qual problema estamos solucionando?

Atender &agrave; obrigatoriedade da Febraban de adequa&ccedil;&atilde;o dos boletos para modalidade registrada a partir do dia 10/07/2017, conforme tabela abaixo:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/B1.png)

### Como a Integra&ccedil;&atilde;o ocorre na 3.0?

A 3.0 possui apenas um tipo de chamado, tanto para boletos do “Registrado” quanto “N&atilde;o Registrados”. O mesmo c&oacute;digo &eacute; usado para todos os bancos, e podem ser visualizado em:

> https://developercielo.github.io/Webservice-3.0/#criando-uma-venda-de-boleto

---

![](http://sizzling-oryx.cloudvent.net/images/Boletos/Bradesco.jpg)

### Como funciona - Fluxo Transacional Bradesco?

1. O comprador, ap&oacute;s escolher o produto na loja virtual, seleciona a forma de pagamento Boleto Bradesco;
2. A loja virtual envia para a Cielo uma requisi&ccedil;&atilde;o chamando o meio de pagamento correspondente;
3. A Cielo se comunica com a aplica&ccedil;&atilde;o do Banco Bradesco solicitando o registro do boleto;
4. Caso o registro seja realizado com sucesso, o Banco responde &agrave; solicita&ccedil;&atilde;o devolvendo os dados de cobran&ccedil;a (c&oacute;digo de barras, linha digit&aacute;vel, etc) e a **URL do Boleto**;
5. A Cielo envia no response o link para que a loja possa encaminhar ao comprador am ambiente Banc&aacute;rio;
6. O cliente acessa a URL do boleto (renderiza&ccedil;&atilde;o) e ent&atilde;o pode realizar o pagamento;
7. A concilia&ccedil;&atilde;o do documento &eacute; feita via servi&ccedil;o de consulta da Cielo ao sistema do Bradesco.
8. Para receber as notifica&ccedil;&otilde;es de pagamento, a loja deve ter cadastrada a URL de Notifica&ccedil;&atilde;o e eventualmente utilizar nosso servi&ccedil;o de consulta.

![](http://sizzling-oryx.cloudvent.net/images/Boletos/B2.png)

### Lojista - Ativando o Boleto no Bradesco

1. O lojista dever&aacute; contatar o gerente de relacionamento do Banco Bradesco para solicitar a contrata&ccedil;&atilde;o do Boleto Registrado via Gerenciador API;
2. A equipe t&eacute;cnica do Banco enviar&aacute; para o e-mail do solicitante os dados de acesso ao Gerenciador API.
3. No painel do Bradesco, o lojista dever&aacute; acesse a aba “Configura&ccedil;&otilde;es” e escolher a op&ccedil;&atilde;o “Meios de Pagamento”.
4. O campo “Palavra-secreta” deve ser preenchido com uma senha. A opera&ccedil;&atilde;o &eacute; confirmada clicando em “Gerar nova chave de seguran&ccedil;a”:
5. Ainda no [Painel do Bradesco](https://meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp), o cliente deve criar um Usu&aacute;rio de Consulta para atualiza&ccedil;&otilde;es de status.
6. O Lojista dever&aacute; realizar atualiza&ccedil;&atilde;o dos dados cadastrais Bradesco para poder Transacionar. Ver [Tutorial](https://developercielo.github.io/Habilitacao-meios-de-pagamento/#bradesco).

![](http://sizzling-oryx.cloudvent.net/images/Boletos/B3.png)

### HD Cielo - Ativando o Boleto no Admin

O Lojista precisar&aacute; informar ao HD os sequintes dados:

* **Ag&ecirc;ncia:** c&oacute;digo ag&ecirc;ncia com tra&ccedil;o ou sem Hifen.
* **Conta:** Conta corrente com tra&ccedil;o.
* **Carteira:** N&atilde;o &eacute; necess&aacute;rio para este boleto
* **Concilia&ccedil;&atilde;o**: N&uacute;mero do conv&ecirc;nio de cobran&ccedil;a
* **Conv&ecirc;nio** Conv&ecirc;nio de com&eacute;rcio eletr&ocirc;nico

Al&eacute;m desses dados, &eacute; necessario as credenciais do Bradesco:

* **Usu&aacute;rio**: E-mail usado no acesso do [Painel do Bradesco](https://meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp)
* **Senha**: Chave de seguran&ccedil;a criada dentro do [Painel do Bradesco](https://meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp). **N&atilde;o &eacute; a senha de acesso ao Painel Bradesco**

> Essas credenciais s&atilde;o usadas para que a 3.0 possa consultar o status do Boleto.<br><br>**Exemplos:**<br>**Usu&aacute;rio**: cielo@cielo.com<br>**Senha / Chave de Seguran&ccedil;a**: qcnmFA-Y2rGm4meWLzrEzSpdPARBsmblZSqfKLwq7DM

Com esses dados, acesse o Admin e siga os passos abaixo:

1 - Acesse o Admin Braspag e selecione a op&ccedil;&atilde;o “**Pesquisar Estabelecimento**”, existente dentro da aba “Admin” do menu superior:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB1.png)

2 - Utilize os filtros para localizar a loja:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB2.PNG)

3 - Dentro do cadastro da loja, v&aacute; at&eacute; a sess&atilde;o “**Meios de pagamento**” e clique no bot&atilde;o “**Editar**” ao lado do Boleto:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB3.png)

4 - Digite os dados exibidos na tela de cadastros

![](http://sizzling-oryx.cloudvent.net/images/Boletos/BR.PNG)

Dados e formatos a serem inseridos:

| Dados | Descri&ccedil;&atilde;o | Formato | OBS |
| --- | --- | --- | --- |
| **Ag&ecirc;ncia** | C&oacute;digo ag&ecirc;ncia | 4 D&iacute;gitos | com ou sem Hifen |
| **Conta:** | Conta corrente | 7 D&iacute;gitos | com Hifen |
| **Carteira:** | **N&atilde;o &eacute; necess&aacute;rio boleto Registrado** | 2 d&iacute;gitos | N/A |
| **Concilia&ccedil;&atilde;o** | N&uacute;mero do conv&ecirc;nio de cobran&ccedil;a | 7 D&iacute;gitos | Informado dentro [Painel do Bradesco](https://meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp) |
| **Conv&ecirc;nio** | Conv&ecirc;nio de com&eacute;rcio eletr&ocirc;nico | 6 D&iacute;gitos | N/A |
| **Nosso Numero** | Contador incremental | 5 D&iacute;gitos | Inserir “10000” - A cada emiss&atilde;o de boleto esse numero aumenta em +1 |
| **Vencimento** | Prazo de validade do boleto | 6 D&iacute;gitos | &eacute; o valor padr&atilde;o, se nenhum outro valor for enviado via API |
| **Assinatura de Afilia&ccedil;&atilde;o** | Chave de seguran&ccedil;a do **Bradesco** | 50 D&iacute;gitos | Informado dentro [Painel do Bradesco](https://meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp) |

> No momento, &eacute; necessario solicitar a equipe de Suporte Braspag que o **Usu&aacute;rio** e **Senha** sejam cadastradas no boleto Bradesco. Ap&oacute;s preencher os dados acima, entrem em contato com a Braspag fornecendo os dados de acesso a Sonda Bradesco<br><br><br>**Exemplos:**<br><br>**Usu&aacute;rio:** cielo@cielo.com<br>**Senha / Chave de Seguran&ccedil;a:** qcnmFA-Y2rGm4meWLzrEzSpdPARBsmblZSqfKLwq7DM

5 - Basta salvar as altera&ccedil;&otilde;es. Pronto, o boleto est&aacute; cadastrado na loja.

### Como funciona a Concilia&ccedil;&atilde;o Autom&aacute;tica (Atualiza&ccedil;&atilde;o de Status)?

Para o meio de pagamento Boleto Registrado Bradesco a concilia&ccedil;&atilde;o &eacute; feita via sondagem em lote.

A Sondagem em lote funciona da seguinte forma: diariamente a Braspag consulta o sistema do Bradesco em busca de boletos pagos na data anterior. Essa sondagem ocorre pela manh&atilde; **(&agrave;s 4h, 6h, 8h, 10h e 12h)**. Para receber as notifica&ccedil;&otilde;es de pagamento, a loja deve ter cadastrada a URL de Notifica&ccedil;&atilde;o em conjunto com a realiza&ccedil;&atilde;o de GETs

**OBS:** Hoje, a sonda considera transa&ccedil;&otilde;es que estejam com a data de vencimento dentro do intervalo de 30 dias anteriores e 30 dias posteriores &agrave; data de Sondagem Este intervalo existe devido ao alto volume de boletos gerados, para que haja limita&ccedil;&atilde;o do processo de sondagem.

### Concilia&ccedil;&atilde;o Manual de Boletos

Para conciliar o boleto de forma manual, basta localizar o pedido no Admin e dentro dos Detalhes da Transa&ccedil;&atilde;o localizar o bot&atilde;o “Conciliar”. Desta forma o pedido ter&aacute; o status alterado de “N&atilde;o Pago” para “Pago”.

### Contatos Bradesco

Suporte:

* kit@scopus.com.br
* homologacao@scopus.com.br
* com.eletronico@bradesco.com.br
* comerciobradesco@scopus.com.br

---

![](http://sizzling-oryx.cloudvent.net/images/Boletos/BancoDoBrasil.jpg)

### Como funciona - Fluxo Transacional Banco do Brasil?

1. O comprador, ap&oacute;s escolher o produto na loja virtual, seleciona a forma de pagamento Boleto Registrado Banco do Brasil;
2. A loja virtual envia para a Braspag uma requisi&ccedil;&atilde;o chamando o meio de pagamento correspondente;
3. A Braspag se comunica com a aplica&ccedil;&atilde;o do Banco solicitando o registro do boleto;
4. O Banco responde &agrave; solicita&ccedil;&atilde;o de registro;
5. Caso o registro seja realizado com sucesso, a Braspag “gera” o boleto conforme os dados retornados pelo banco;
6. A Braspag envia no response, o link para imprimir o boleto
7. A loja retorna este link ao comprador
8. Para receber as notifica&ccedil;&otilde;es de pagamento, a loja deve ter cadastrada a URL de Notifica&ccedil;&atilde;o e eventualmente utilizar nosso servi&ccedil;o de consulta.

![](http://sizzling-oryx.cloudvent.net/images/Boletos/FluxoBB.png)

### Lojista - Ativando o Boleto no Banco do Brasil

* O lojista dever&aacute; contatar o gerente de relacionamento do Banco do Brasil para solicitar a habilita&ccedil;&atilde;o do produto Boleto Registrado; o formul&aacute;rio a seguir deve ser preenchido conforme abaixo e entregue ao gerente.
  * **URL (site) retorno &agrave; loja**: https://www.pagador.com.br
  * **Formato arquivo Retorno**: (X) CBR643
  * **Meio de retorno**: {X) Mainframe – para empresa com sistema pr&oacute;prio, que n&atilde;o usam o GFN.

![](http://sizzling-oryx.cloudvent.net/images/Boletos/Regbb00.PNG) ![](http://sizzling-oryx.cloudvent.net/images/Boletos/Regbb01.PNG)

* Ao final do credenciamento, o lojista receber&aacute; um documento com como o que segue abaixo

![](http://sizzling-oryx.cloudvent.net/images/Boletos/Regbb02.jpg)

* As informa&ccedil;&otilde;es que o lojista deve passar, via ticket na ferramenta de suporte da Braspag, s&atilde;o:
  * Conv&ecirc;nio do Com&eacute;rcio Eletr&ocirc;nico
  * N&uacute;mero do Conv&ecirc;nio de Cobran&ccedil;a
  * Ag&ecirc;ncia
  * Conta
* Ap&oacute;s habilitar o meio de pagamento no cadastro da loja, gerar um pedido teste enviando as informa&ccedil;&otilde;es obrigat&oacute;rias para registro (nome do comprador, CPF e endere&ccedil;o completo).

*OBS*: A loja dever&aacute; obrigat&oacute;riamente enviar no contrato da API os dados: Nome do Comprador, CPF e Endere&ccedil;o.

### Particularidades Boleto Registrado Banco do Brasil

No Boleto Registrado Banco do Brasil, a linha digit&aacute;vel n&atilde;o ser&aacute; retornado no response da requisi&ccedil;&atilde;o.

Esta informa&ccedil;&atilde;o ficar&aacute; dispon&iacute;vel ap&oacute;s concilia&ccedil;&atilde;o.

Para todos os campos texto, inclusive o campo de instru&ccedil;&otilde;es e relacionados ao endere&ccedil;o, s&atilde;o aceitos como caracteres v&aacute;lidos:

* as letras de A a Z (MAI&Uacute;SCULAS);
* caracteres especiais de conjun&ccedil;&atilde;o: h&iacute;fen (-), ap&oacute;strofo (‘) quando utilizados, *n&atilde;o pode conter espa&ccedil;os entre as letras*;
  * *Exemplos corretos:* D’EL-REI, D’ALCORTIVO, SANT’ANA
  * *Exemplos incorretos:* D’EL - REI
* at&eacute; um espa&ccedil;o em branco entre palavras

### HD Cielo - Ativando o Boleto no Admin

O Lojista precisar&aacute; informar ao HD os sequintes dados:

* **Ag&ecirc;ncia:** c&oacute;digo ag&ecirc;ncia com tra&ccedil;o ou sem Hifen.
* **Conta:** Conta corrente com tra&ccedil;o.
* **Carteira:** N&atilde;o &eacute; necess&aacute;rio para este boleto
* **Concilia&ccedil;&atilde;o**: N&uacute;mero do conv&ecirc;nio de cobran&ccedil;a
* **Conv&ecirc;nio** Conv&ecirc;nio de com&eacute;rcio eletr&ocirc;nico

Com esses dados, acesse o Admin e siga os passos abaixo:

1 - Acesse o Admin Braspag e selecione a op&ccedil;&atilde;o “**Pesquisar Estabelecimento**”, existente dentro da aba “Admin” do menu superior:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB1.png)

2 - Utilize os filtros para localizar a loja:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB2.PNG)

3 - Dentro do cadastro da loja, v&aacute; at&eacute; a sess&atilde;o “**Meios de pagamento**” e clique no bot&atilde;o “**Editar**” ao lado do Boleto:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB3.png)

4 - Digite os dados exibidos na tela de cadastros

![](http://sizzling-oryx.cloudvent.net/images/Boletos/BB.PNG)

Dados e formatos a serem inseridos:

| Dados | Descri&ccedil;&atilde;o | Formato | OBS |
| --- | --- | --- | --- |
| **Ag&ecirc;ncia** | C&oacute;digo ag&ecirc;ncia | 4 D&iacute;gitos | Hifen Obrig&aacute;t&oacute;rio |
| **Conta:** | Conta corrente | 7 D&iacute;gitos | Hifen Obrig&aacute;t&oacute;rio |
| **Carteira:** | **N&atilde;o &eacute; necess&aacute;rio boleto Registrado** | 2 d&iacute;gitos | N/A |
| **Concilia&ccedil;&atilde;o** | N&uacute;mero do conv&ecirc;nio de cobran&ccedil;a | 7 D&iacute;gitos | inserir o *Conv&ecirc;nio de cobran&ccedil;a* fornecido pelo banco |
| **Conv&ecirc;nio** | Conv&ecirc;nio de com&eacute;rcio eletr&ocirc;nico | 7 D&iacute;gitos | inserir o *Conv&ecirc;nio de Comercio Eletr&ocirc;nico* fornecido pelo banco |
| **Nosso Numero** | Contador incremental | 5 D&iacute;gitos | Inserir “10000” - A cada emiss&atilde;o de boleto esse numero aumenta em +1 |
| **Vencimento** | Prazo de validade do boleto | 6 D&iacute;gitos | &eacute; o valor padr&atilde;o, se nenhum outro valor for enviado via API |
| **Instru&ccedil;&otilde;es** | Informa&ccedil;&otilde;es exibidas no boleto | 50 D&iacute;gitos | Somente numeros e letras de A-Z |

5 - Basta salvar as altera&ccedil;&otilde;es. Pronto, o boleto est&aacute; cadastrado na loja.

### Como funciona a Concilia&ccedil;&atilde;o Autom&aacute;tica (Atualiza&ccedil;&atilde;o de Status)?

> **NO MOMENTO, O BOLETO REGISTRADO BANCO DO BRASIL N&Atilde;O REALIZA ATUALIZA&Ccedil;&Atilde;O DE STATUS AUTOM&Aacute;TICA**

As instru&ccedil;&otilde;es abaixo s&atilde;o para a cria&ccedil;&atilde;o e defini&ccedil;&atilde;o de troca de arquivos para concilia&ccedil;&atilde;o bancaria entre BB e Braspag. \*\* O fluxo abaixo ainda n&atilde;o foi implementado para API Cielo\*\*

O lojista pode optar por utilizar a Concilia&ccedil;&atilde;o Autom&aacute;tica de Boletos. Para que seja estabelecido o relacionamento entre o Banco e a VAN Nexxera, o lojista deve preencher a carta de abertura de relacionamento banc&aacute;rio (carta dispon&iacute;vel na &uacute;ltima p&aacute;gina deste documento). Esta deve ser devidamente preenchida pelo cliente e entregue ao gerente de relacionamento respons&aacute;vel pela conta corrente onde o valor dos boletos ser&aacute; creditado.

O gerente dever&aacute; encaminhar esta carta ao setor de conectividade de seu banco. Este setor tamb&eacute;m &eacute; conhecido com setor de EDI ou setor de troca de arquivos eletr&ocirc;nicos do banco, e &eacute; respons&aacute;vel por abrir um relacionamento para tr&aacute;fego dos arquivos de retorno entre banco e Nexxera.

Verifica&ccedil;&atilde;o de Abertura de Relacionamento

Para certificar-se de que foi realizada a abertura de relacionamento, encaminhar um e-mail para implantacao@nexxera.com

| Exemplo de e-mail |
| --- |
| “Prezados,<br><br>Por gentileza, verificar se a empresa abaixo possui relacionamento para tr&aacute;fego de arquivos de retorno do banco [**Nome do Banco**].<br>- Nome Fantasia:<br>- Raz&atilde;o Social:<br>- CNPJ:<br>- Ag&ecirc;ncia:<br>- Conta:<br>- Convenio/Cedente:<br><br>Em caso positivo, informar o C&oacute;digo de Concilia&ccedil;&atilde;o, Nomenclatura de Retorno, tipo de servi&ccedil;o e layout dos arquivos de retorno<br><br>Atenciosamente,” |

> Cada lojista dever&aacute; realizar uma troca de arquivos de concilia&ccedil;&atilde;o com a Cielo/Braspag para ter uma sistema de atualiza&ccedil;&atilde;o de status funcional na API Cielo ecommerce.<br>O Fluxo de cadastro e troca de arquivos ainda ser&aacute; definido. Hoje os lojistas precisar&atilde;o realizar concilia&ccedil;&atilde;o manual