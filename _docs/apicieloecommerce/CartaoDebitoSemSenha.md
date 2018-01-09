---
title: C.Débito sem Senha
category: API CIELO ECOMMERCE
order: 8
---

### O que é?

É um mecanismo para processar um **cartão de débito** sem a necessidade de submeter o comprador ao processo de autenticação.

Até então, pelas regras das bandeiras, a autenticação do portador era mandatório para todas as transações de cartão de débito no e-commerce. Lembrando que para cartões de crédito, o processo de autenticação permanece opcional. 

### Os principais requisitos para usufruir da funcionalidade são:

- Possuir uma afiliação do Cielo 3.0
- O estabelecimento deve estar **habilitado na Cielo/Bandeira**
- Funcional apenas para  Cartões emitidos pelos bancos
    - **Bradesco** - VISA
    - **Banco do Brasil** - VISA / MASTER / ELO

### Qual o benefício em utilizá-lo?

O processo de autenticação necessariamente cria algumas etapas adicionais no checkout do estabelecimento, além de redirecionar o portador para tela do banco, onde a autenticação acontece. 
Isso diminui a taxa de conversão.

Com a isenção do processo de autenticação, a experiência do usuário se torna semelhante ao fluxo do cartão de crédito não autenticavel.

Essa melhoria cria as sequintes possibilidades:

- Melhorar a conversão do meio de pagamento Cartão de Débito
- Viabilizar a recorrência com Cartão de Débito *(desenvolvimento futuro)*

### Público Alvo

Os clientes que atuam no e-Commerce, que o MCC esteja de acordo com as regras da adquirência para esta funcionalidade.
Normalmente, a Cielo tem liberado os lojistas que atuam no modelo de assinatura com recorrência.

### Como funciona?

O comprador, após escolher o produto na loja virtual, seleciona a forma de pagamento Cartão de Débito
A loja virtual envia para a Braspag uma requisição chamando o meio de pagamento correspondente;
A Braspag avalia o BIN do cartão, para verificar se o emissor e a bandeira do cartão é elegível para a isenção do processo de autenticação;
Se positivo, a Braspag envia uma requisição de cartão de débito, porém, sem a marcação para autenticação (Autorizar=3 e Produto=A);
Segue o fluxo padrão de autorização, e a Cielo retorna a resposta com o código de autorização ou erro;
 
