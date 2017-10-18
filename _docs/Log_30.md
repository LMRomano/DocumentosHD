---
title: Api Cielo Ecommerce
category: LOG
order: 1
---

## O que é o LOG da API?


Logs são registros dos processos que ocorrem dentro da API Cielo. Eles marcam fluxos corretos e incorretos.


Logs possuem 2 níveis de informação:

* **Aplicação** – Define qual Log está sendo visualizado
* **Severidade** – Defini o tipo de informação vista

**Tipos de Severidade:**

* **Informação** – Mostra os dados trafegados na API - 99% do atendimento ocorre neste nível)
* **Error** – Mostra falhas dentro da API 
* **Critical** – Mostra falhas severas de fluxo




## Regras ara pesquisa em Log

O Log Braspag possui limitações operacionais, então é muito importante seguir as regras de abaixo para uma boa pesquisa:

| Regra                               | Motivo                                                                                                                                   |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| **Informação Textual**              | O Log é um grande arquivo onde a pesquisa por "Palavra Chave" é lenta. Foque em buscar usando MID ou RequestID                           |
| **Limite de 45 dias corridos**      | Após esse periodo, passamos a salvar dos em fita. Não é acessivel via PLataformas online.                                                |
| **Intervalo de tempo é importante** | Devido ao volume de dados armazenados, pesquisas devem ter o menor intevalo de tempo o possivel, evitando Time-out na respostas do Admin |


As melhores variaveis para se pesquisar no Log são (Em ordem de Eficiência)

1. RequestID
2. MID
3. Usar Palavra Chave




**Atenção A:** O **RequestID** é o identificador de uma ação dentro da Braspag. Ele se repete em todos os passos dessa ação. Um exemplo é a AUTORIZAÇÃO onde o RequestID que é gerado na requisição do Cliente, é o mesmo identificando o envio do pedido a Cielo, o mesmo que identifica a resposta Cielo e o mesmo que identifica a resposta ao Cliente.

**Atenção B:** Todo LOG possui um **RequestID**. Encontrar o RequestID varia de acordo com a ação executada:

| Ação                     | Como encontrar o RequestID                                                                                                                                                  |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Criação de transação** | Dentro de `Detalhes de transação` no Admin 3.0 basta ir na área de histórico da transação. Ele será apresentado la                                                          |
| **Consulta**             | A consulta não é apresentada em  `Detalhes de transação`. Aqui basta pesquisar o `MID + PalavraChave = PaymentID` em Log. Será possivel achar o Log da consulta + RequestID |
| **Captura/Cancelamento** | Essa opção fica disponivel em `Detalhes de transação` se bem sucedida. Em Caso de erro, deve ser feita a pesquisa de `MID + PalavraChave = PaymentID`                       |
| **Erros**                | Em Caso de erro, deve ser feita a pesquisa de `MID + PalavraChave = PaymentID/utro dado fornecido`                                                                          |







## Como Pesquisar no LOG API CIELO ECOMMERCE


Para pesquisar logs da API, basta seguir os passos adiante:

1 - Acesse o log via o **Admin Braspag Cielo** 
* Veja a aba LOGs
* Se preferir acesse: <https://admin.braspag.com.br/Logs/List?productDomain=CieloApi>

2 - Na tela de pesquisa **cruze** as variaveis para encontrar o a informação que busca:

Varivais de pesquisa:

1. **APLICAÇÃO:** CIELOAPI (Sempre)
2. **SEVERIDADE:** DEIXAR TODAS SELECIONADAS (Sempre)
2. RequestID
2. MID
3. Usar Palavra Chave
4. Intervalo






## Termos vinculados a LOGs

Abaixo uma Lista de Termos que podem ajudar na pesquisa:

| Termo                                          | Descrição                                                                                                                                                                  |
|------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Request: POST**                              | Texto normalmente encontrato em CRIAÇÃO de transações ou envio de informações dentro da **API**                                                                            |
| **Response: POST**                             | Texto de resposta a requisição de POST. Normalmente contem dados de Autorização ou Não autorização de transações ou de informações enviadas a API                          |
| **Request: GET**                               | Texto normalmente encontrato em CONSULTAS de transações ou envio de informações dentro da **API**                                                                          |
| **Response: GET**                              | Texto de resposta da CONSULTA. Pode conter dados transacionais ou de informações gerais da **API**                                                                         |
| **Request: PUT**                               | Texto normalmente encontrato em Atualizaçãoes de transações Como capturas, cancelamento ou Atualizações dos dados da transação ou da **API**, como CardToken e Recorrência |
| **Response: PUT**                              | Texto confirmando ou não a atualização do dado enviado                                                                                                                     |
| **[CIELO AUTHORIZE] Posting data to Cielo**    | Envio de dados para autorização Cielo. Essa é a segunda parte de um processo de autorização iniciado na API via o "Request: POST" do lojista                               |
| **[CIELO AUTHORIZE] Received data from Cielo** | Resposta sobre a autorização vinda diretamente do autorizador Cielo. A resposta é enviada ao lojista via o "Response: POST"                                                |
| **[CIELO CAPTURE] Posting data to Cielo**      | Envio de dados para Captura de uma transação dentro da Cielo. É um processo de captura iniciado na API via o "Request: PUT" do lojista                                     |
| **[CIELO CAPTURE] Received data from Cielo**   | Resposta sobre a captura vinda diretamente do autorizador Cielo. A resposta é enviada ao lojista via o "Response: PUT"                                                     |






## Histórico de Atualizações:

| Versão | Data       | Descrição                                                                                                      |
|:------:|------------|----------------------------------------------------------------------------------------------------------------|
| 1.0    | 28/08/2017 | ✓ Versão inicial                                                                                               |








