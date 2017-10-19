---
title: Boletos Registrados
category: API CIELO ECOMMERCE
order: 1
---

### O que é Boleto Registrado?

O Boleto Registrado é um dos meios de pagamentos disponibilizados no E-commerce. Com o objetivo de mitigar fraudes, a Febraban em conjunto com os Bancos desenvolveu a modalidade registrada, tendo um controle centralizado de todos os boletos emitidos.  

### Qual o benefício em utilizá-lo?

A Cobrança Registrada foi desenvolvida para promover maior confiabilidade e segurança na compra online. O banco emissor tem conhecimento do boleto desde sua geração até sua liquidação. O lojista tem a opção de negativar o comprador que gerou e não pagou uma cobrança registrada.

Esta modalidade de cobrança permite que o comprador efetue o pagamento do boleto em qualquer agência bancária mesmo depois do vencimento.

### Qual problema estamos solucionando?

Atender à obrigatoriedade da Febraban de adequação dos boletos para modalidade registrada a partir do dia 10/07/2017, conforme tabela abaixo:


![](http://sizzling-oryx.cloudvent.net/images/Boletos/B1.png)

### Como a Integração ocorre na 3.0?

A 3.0 possui apenas um tipo de chamado, tanto para boletos do "Registrado" quanto "Não Registrados".
O mesmo código é usado para todos os bancos, e podem ser visualizado em: 

> https://developercielo.github.io/Webservice-3.0/#criando-uma-venda-de-boleto




-------------------------------------------------------------------



![](http://sizzling-oryx.cloudvent.net/images/Boletos/Bradesco.jpg)


### Como funciona - Fluxo Transacional Bradesco?

1. O comprador, após escolher o produto na loja virtual, seleciona a forma de pagamento Boleto Bradesco;
1. A loja virtual envia para a Cielo uma requisição chamando o meio de pagamento correspondente;
1. A Cielo se comunica com a aplicação do Banco Bradesco solicitando o registro do boleto;
1. Caso o registro seja realizado com sucesso, o Banco responde à solicitação devolvendo os dados de cobrança (código de barras, linha digitável, etc) e a **URL do Boleto**;
1. A Cielo envia no response o link para que a loja possa encaminhar ao comprador am ambiente Bancário;
1. O cliente acessa a URL do boleto (renderização) e então pode realizar o pagamento; 
1. A conciliação do documento é feita via serviço de consulta da Cielo ao sistema do Bradesco. 
1. Para receber as notificações de pagamento, a loja deve ter cadastrada a URL de Notificação e eventualmente utilizar nosso serviço de consulta. 



![](http://sizzling-oryx.cloudvent.net/images/Boletos/B2.png)




### Lojista - Ativando o Boleto no Bradesco

1. O lojista deverá contatar o gerente de relacionamento do Banco Bradesco para solicitar a contratação do Boleto Registrado via Gerenciador API;
1. A equipe técnica do Banco enviará para o e-mail do solicitante os dados de acesso ao Gerenciador API.
1. No painel do Bradesco, o lojista deverá acesse a aba “Configurações” e escolher a opção “Meios de Pagamento”.
1. O campo “Palavra-secreta” deve ser preenchido com uma senha. A operação é confirmada clicando em “Gerar nova chave de segurança”:
1. Ainda no [Painel do Bradesco](https://meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp), o cliente deve criar um Usuário de Consulta para atualizações de status.
2. O Lojista deverá realizar atualização dos dados cadastrais Bradesco para poder Transacionar. Ver [Tutorial](https://developercielo.github.io/Habilitacao-meios-de-pagamento/#bradesco).
 

![](http://sizzling-oryx.cloudvent.net/images/Boletos/B3.png)



### HD Cielo - Ativando o Boleto no Admin

O Lojista precisará informar ao HD os sequintes dados:

* **Agência:** código agência com traço.
* **Conta:** Conta corrente com traço.
* **Carteira:** Não é necessário para este boleto
* **Conciliação**: Número do convênio de cobrança (7 posições)
* **Convênio** Convênio de comércio eletrônico (6 posições)
 
Com esses dados, acesse siga os passos abaixo:

1 - Acesse o  Admin Braspag e selecione a opção “**Pesquisar Estabelecimento**”, existente dentro da aba “Admin” do menu superior:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB1.png)

2 - Utilize os filtros para localizar a loja:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB2.PNG)

3 - Dentro do cadastro da loja, vá até a sessão “**Meios de pagamento**” e clique no botão “**Editar**” ao lado do Boleto: 

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB3.png)






















































