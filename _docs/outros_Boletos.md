---
title: Boletos Registrados
category: API CIELO ECOMMERCE
order: 1
---

### O que é Boleto Registrado?

O Boleto Registrado é um dos meios de pagamentos disponibilizados no E-commerce. Com o objetivo de mitigar fraudes, a Febraban em conjunto com os Bancos desenvolveu a modalidade registrada, tendo um controle centralizado de todos os boletos emitidos.  

### O Qual o benefício em utilizá-lo?

A Cobrança Registrada foi desenvolvida para promover maior confiabilidade e segurança na compra online. O banco emissor tem conhecimento do boleto desde sua geração até sua liquidação. O lojista tem a opção de negativar o comprador que gerou e não pagou uma cobrança registrada.

Esta modalidade de cobrança permite que o comprador efetue o pagamento do boleto em qualquer agência bancária mesmo depois do vencimento.

### O Qual problema estamos solucionando?

Atender à obrigatoriedade da Febraban de adequação dos boletos para modalidade registrada a partir do dia 10/07/2017, conforme tabela abaixo:


IMAGEM 1


## Boleto Bradesco


### Público Alvo

Qualquer cliente que queira fornecer a solução de pagamento Boleto Registrado via Banco Bradesco.


### Como funciona?

1. O comprador, após escolher o produto na loja virtual, seleciona a forma de pagamento Boleto Bradesco;
1.A loja virtual envia para a Braspag uma requisição chamando o meio de pagamento correspondente;
1.A Braspag se comunica com a aplicação do Banco Bradesco solicitando o registro do boleto;
1.Caso o registro seja realizado com sucesso, o Banco responde à solicitação devolvendo os dados de cobrança (código de barras, linha digitável, etc) e a URL do Boleto;
1.A Braspag envia no response este link para que a loja possa encaminhar ao comprador;
1.O cliente acessa a URL do boleto (renderização) e então pode realizar o pagamento; 
1.A conciliação do documento é feita via serviço de consulta da Braspag ao sistema do Bradesco. 
1.Para receber as notificações de pagamento, a loja deve ter cadastrada a URL de Notificação e eventualmente utilizar nosso serviço de consulta. 