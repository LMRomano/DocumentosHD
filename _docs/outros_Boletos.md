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


* **Agência:** código agência com traço ou sem Hifen.
* **Conta:** Conta corrente com traço.
* **Carteira:** Não é necessário para este boleto
* **Conciliação**: Número do convênio de cobrança
* **Convênio** Convênio de comércio eletrônico

Além desses dados, é necessario as credenciais do Bradesco:

* **Usuário**: E-mail usado no acesso do [Painel do Bradesco](https://meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp)
* **Senha**: Chave de segurança criada dentro do [Painel do Bradesco](https://meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp). **Não é a senha de acesso ao Painel Bradesco**

> Essas credenciais são usadas para que a 3.0 possa consultar o status do Boleto. <BR><BR> **Exemplos:** <BR> **Usuário**: cielo@cielo.com <BR> **Senha / Chave de Segurança**: qcnmFA-Y2rGm4meWLzrEzSpdPARBsmblZSqfKLwq7DM


Com esses dados, acesse o Admin e siga os passos abaixo:

1 - Acesse o  Admin Braspag e selecione a opção “**Pesquisar Estabelecimento**”, existente dentro da aba “Admin” do menu superior:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB1.png)

2 - Utilize os filtros para localizar a loja:

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB2.PNG)

3 - Dentro do cadastro da loja, vá até a sessão “**Meios de pagamento**” e clique no botão “**Editar**” ao lado do Boleto: 

![](http://sizzling-oryx.cloudvent.net/images/Boletos/AB3.png)

4 - Digite os dados exibidos na tela de cadastros

![](http://sizzling-oryx.cloudvent.net/images/Boletos/BR.PNG)


Dados e formatos a serem inseridos:


| Dados                       | Descrição                              | Formato    | OBS                                                                                                     |
|-----------------------------|----------------------------------------|------------|---------------------------------------------------------------------------------------------------------|
| **Agência**                 | Código agência                         | 4 Dígitos  | com  ou sem Hifen                                                                                       |
| **Conta:**                  | Conta corrente                         | 7 Dígitos  | com Hifen                                                                                               |
| **Carteira:**               | **Não é necessário boleto Registrado** | 2 dígitos  | N/A                                                                                                     |
| **Conciliação**             | Número do convênio de cobrança         | 7 Dígitos  | Informado dentro [Painel do Bradesco](https://meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp) |
| **Convênio**                | Convênio de comércio eletrônico        | 6 Dígitos  | N/A                                                                                                     |
| **Nosso Numero**            | Contador incremental                   | 5 Dígitos  | Inserir "10000" -  A cada emissão de boleto esse numero aumenta em +1                                   |
| **Vencimento**              | Prazo de validade do boleto            | 6 Dígitos  | é o valor padrão, se nenhum outro valor for enviado via API                                             |
| **Assinatura de Afiliação** | Chave de segurança do **Bradesco**     | 50 Dígitos | Informado dentro [Painel do Bradesco](https://meiosdepagamentobradesco.com.br/gerenciadorapi/login.jsp) |                                                                                        


> No momento, é necessario solicitar a equipe de Suporte Braspag que o **Usuário** e **Senha** sejam cadastradas no boleto Bradesco. Após preencher os dados acima, entrem em contato com a Braspag fornecendo os dados de acesso a Sonda Bradesco <BR><BR><BR> **Exemplos:** <BR><br> **Usuário:** cielo@cielo.com <BR> **Senha / Chave de Segurança:** qcnmFA-Y2rGm4meWLzrEzSpdPARBsmblZSqfKLwq7DM


5 - Basta salvar as alterações. Pronto, o boleto está cadastrado na loja.



### Como funciona a Conciliação Automática (Atualização de Status)?

Para o meio de pagamento Boleto Registrado Bradesco  a conciliação é feita via sondagem em lote. 

A Sondagem em lote funciona da seguinte forma: diariamente a Braspag consulta o sistema do Bradesco em busca de boletos pagos na data anterior. Essa sondagem ocorre pela manhã **(às 4h, 6h, 8h, 10h e 12h)**.
Para receber as notificações de pagamento, a loja deve ter cadastrada a URL de Notificação em conjunto com a realização de GETs

**OBS:** Hoje, a sonda considera transações que estejam com a data de vencimento dentro do intervalo de 30 dias anteriores e 30 dias posteriores à data de Sondagem Este intervalo existe devido ao alto volume de boletos gerados, para que haja limitação do processo de sondagem.


### Conciliação Manual de Boletos

Para conciliar o boleto de forma manual, basta localizar o pedido no Admin e dentro dos Detalhes da Transação localizar o botão “Conciliar”. Desta forma o pedido terá o status alterado de “Não Pago" para “Pago”.


### Contatos Bradesco

Suporte: 
* kit@scopus.com.br
* homologacao@scopus.com.br
* com.eletronico@bradesco.com.br
* comerciobradesco@scopus.com.br 

-------------------------------------------------------------------



![](http://sizzling-oryx.cloudvent.net/images/Boletos/BancoDoBrasil.jpg)


### Como funciona - Fluxo Transacional Banco do Brasil?

1. O comprador, após escolher o produto na loja virtual, seleciona a forma de pagamento Boleto Registrado Banco do Brasil;
1. A loja virtual envia para a Braspag uma requisição chamando o meio de pagamento correspondente;
1. A Braspag se comunica com a aplicação do Banco solicitando o registro do boleto;
1. O Banco responde à solicitação de registro;
1. Caso o registro seja realizado com sucesso, a Braspag "gera" o boleto conforme os dados retornados pelo banco;
1. A Braspag envia no response, o link para imprimir o boleto
1. A loja retorna este link ao comprador
1. Para receber as notificações de pagamento, a loja deve ter cadastrada a URL de Notificação e eventualmente utilizar nosso serviço de consulta. 


![](http://sizzling-oryx.cloudvent.net/images/Boletos/FluxoBB.png)


### Lojista - Ativando o Boleto no Banco do Brasil

O lojista deverá contatar o gerente de relacionamento do Banco do Brasil para solicitar a habilitação do produto Boleto Registrado; o formulário a seguir deve ser preenchido conforme abaixo e entregue ao gerente: 

- URL (site) retorno à loja: https://www.pagador.com.br
- Formato arquivo Retorno: (X) CBR643
- Meio de retorno: (X) Mainframe – para empresa com sistema próprio, que não usam o GFN.














