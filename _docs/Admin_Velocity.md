---
title: Velocity
category: API CIELO ECOMMERCE
order: 1
---


### O que &eacute; Velocity

O Velocity &eacute; um tipo de mecanismo de preven&ccedil;&atilde;o &agrave; tentativas de fraude, que analisa especificamente o conceito de “**velocidade X dados transacionais**”. Ela analisa a frequ&ecirc;ncia que determinados dados s&atilde;o utilizados e se esse dados est&atilde;o inscritos em uma lista de comportamentos passiveis de a&ccedil;&otilde;es de seguran&ccedil;a.

Para estabelecimentos comerciais que atuam no mercado de com&eacute;rcio eletr&ocirc;nico e eventualmente recebem transa&ccedil;&otilde;es fraudulentas, o Velocity &eacute; um produto que identificar&aacute; os comportamentos suspeitos de fraude. A ferramenta tem o intuito de auxiliar na an&aacute;lise de fraude por um custo bem menor que uma ferramenta mais tradicional de mercado.

Ela &eacute; uma aliada na avalia&ccedil;&atilde;o de comportamentos suspeitos de compra, pois os c&aacute;lculos ser&atilde;o baseados em `elementos de rastreabilidade`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge}.

O Velocity oferece 4 tipos de funcionalidades para validar dados transacionais:

| Funcionalidade | Descri&ccedil;&atilde;o |
| --- | --- |
| **Regras de seguran&ccedil;a velocity** | O Lojista defini um grupo de regras de seguran&ccedil;a que v&atilde;o avaliar se determinados dados transacionais se repetem em um intervalo de tempo suspeito |
| **Quarentena** | Cria&ccedil;&atilde;o de uma lista de dados que ser&atilde;o analisados por um periodo de tempo determinado antes de serem considerados validos ou fraudulentos |
| **BlackList** | Cria&ccedil;&atilde;o de uma lista de dados que ao serem identificados impedem a transa&ccedil;&atilde;o de ser executada, evitando a cria&ccedil;&atilde;o de uma transa&ccedil;&atilde;o fraudulenta |
| **Whitelist** | Cria&ccedil;&atilde;o de uma lista de dados que ao serem identificados permitem que a transa&ccedil;&atilde;o de seja executada, mesmo que existam regras de seguran&ccedil;a em a&ccedil;&atilde;o |

As principais fun&ccedil;&otilde;es do Velocity s&atilde;o:

* Auxiliar na detec&ccedil;&atilde;o de elementos suspeitos de fraude.
* Fonte de dados para bloquear **ataques em rajada** (testes de cart&atilde;o, por exemplo), bem como avalia&ccedil;&otilde;es de comportamentos suspeitos de compra.
* C&aacute;lculos baseados em an&aacute;lise de velocidade de elementos rastre&aacute;veis e a incid&ecirc;ncia dos mesmos em determinados intervalos de tempo

A funcionalidade deve ser contratada &agrave; parte, e posteriormente habilitada em sua loja pela equipe de Suporte Cielo Ecommerce via o **Admin 3.0 da Braspag**

### Funcionamento do Velocity e habilita&ccedil;&atilde;o.

O Velocity funciona analisando dados enviados na integra&ccedil;&atilde;o padr&atilde;o da API Cielo Ecommerce. N&atilde;o &eacute; necessario incluir nenhuma n&oacute;s adicional a integra&ccedil;&atilde;o da loja para a cria&ccedil;&atilde;o da venda, mas ser&aacute; necessario alterar a forma como os dados s&atilde;o recebidos response.

As principais altera&ccedil;&otilde;es que devem ser realizadas **ocorrem dentro do Cadastro da loja** do lojista via o **Admin 3.0 braspag**. Nessa &aacute;rea que as funcionalidades ser&atilde;o habilitadas.

Para habilitar o Velocity basta:

1 - Acessar os dados de **Cadastro de Lojistas 3.0/Api Cielo Ecommerce**&nbsp;indo at&eacute; “**Demais funcionalidades”**

![](/uploads/versions/V0---x----379-195x---.JPG)

2 - Dentro de **Demais funcionalidades** Marcar o op&ccedil;&atilde;o velocity

![](./images/Velocity/V1.JPG)


3 - Com o Velocity habilitado, a op&ccedil;&atilde;o **“Configurar”** estar&aacute; disponivel ao lado da op&ccedil;&atilde;o “Velocity”. Esse menu ser&aacute; analisado mais afrente neste manual

![](/uploads/versions/V2---x----379-195x---.JPG)

Quando o Velocity est&aacute; ativo, a resposta da transa&ccedil;&atilde;o trar&aacute; um n&oacute; espec&iacute;fico chamado “Velocity”, com os detalhes da an&aacute;lise.

Dados dos retornados pelo Velocity

| Propriedade | Descri&ccedil;&atilde;o | Tipo | Tamanho |
| --- | --- | --- | --- |
| `VelocityAnalysis.Id`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} | Identificador da an&aacute;lise efetuada | GUID | 36 |
| `VelocityAnalysis.ResultMessage`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} | Accept ou Reject | Texto | 25 |
| `VelocityAnalysis.Score`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} | 100 | N&uacute;mero | 10 |
| `VelocityAnalysis.RejectReasons.RuleId`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} | C&oacute;digo da Regra que rejeitou | N&uacute;mero | 10 |
| `VelocityAnalysis.RejectReasons.Message`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} | Descri&ccedil;&atilde;o da Regra que rejeitou | Texto | 512 |

### Resposta

<div class="highlighter-rouge"><pre class="highlight"><code><span class="p">{</span><span class="w">
  </span><span class="nt">"MerchantOrderId"</span><span class="p">:</span><span class="w"> </span><span class="s2">"2017051202"</span><span class="p">,</span><span class="w">
  </span><span class="nt">"Customer"</span><span class="p">:</span><span class="w"> </span><span class="p">{</span><span class="w">
    </span><span class="nt">"Name"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Nome do Comprador"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Identity"</span><span class="p">:</span><span class="w"> </span><span class="s2">"12345678909"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"IdentityType"</span><span class="p">:</span><span class="w"> </span><span class="s2">"CPF"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Email"</span><span class="p">:</span><span class="w"> </span><span class="s2">"comprador@cielo.com.br"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Address"</span><span class="p">:</span><span class="w"> </span><span class="p">{</span><span class="w">
      </span><span class="nt">"Street"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Alameda Xingu"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Number"</span><span class="p">:</span><span class="w"> </span><span class="s2">"512"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Complement"</span><span class="p">:</span><span class="w"> </span><span class="s2">"27 andar"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"ZipCode"</span><span class="p">:</span><span class="w"> </span><span class="s2">"12345987"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"City"</span><span class="p">:</span><span class="w"> </span><span class="s2">"S&atilde;o Paulo"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"State"</span><span class="p">:</span><span class="w"> </span><span class="s2">"SP"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Country"</span><span class="p">:</span><span class="w"> </span><span class="s2">"BRA"</span><span class="w">
    </span><span class="p">},</span><span class="w">
    </span><span class="nt">"DeliveryAddress"</span><span class="p">:</span><span class="w"> </span><span class="p">{</span><span class="w">
      </span><span class="nt">"Street"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Alameda Xingu"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Number"</span><span class="p">:</span><span class="w"> </span><span class="s2">"512"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Complement"</span><span class="p">:</span><span class="w"> </span><span class="s2">"27 andar"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"ZipCode"</span><span class="p">:</span><span class="w"> </span><span class="s2">"12345987"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"City"</span><span class="p">:</span><span class="w"> </span><span class="s2">"S&atilde;o Paulo"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"State"</span><span class="p">:</span><span class="w"> </span><span class="s2">"SP"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Country"</span><span class="p">:</span><span class="w"> </span><span class="s2">"BRA"</span><span class="w">
    </span><span class="p">}</span><span class="w">
  </span><span class="p">},</span><span class="w">
  </span><span class="nt">"Payment"</span><span class="p">:</span><span class="w"> </span><span class="p">{</span><span class="w">
    </span><span class="nt">"ServiceTaxAmount"</span><span class="p">:</span><span class="w"> </span><span class="mi">0</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Installments"</span><span class="p">:</span><span class="w"> </span><span class="mi">1</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Interest"</span><span class="p">:</span><span class="w"> </span><span class="s2">"ByMerchant"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Capture"</span><span class="p">:</span><span class="w"> </span><span class="kc">true</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Authenticate"</span><span class="p">:</span><span class="w"> </span><span class="kc">false</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Recurrent"</span><span class="p">:</span><span class="w"> </span><span class="kc">false</span><span class="p">,</span><span class="w">
    </span><span class="nt">"CreditCard"</span><span class="p">:</span><span class="w"> </span><span class="p">{</span><span class="w">
      </span><span class="nt">"CardNumber"</span><span class="p">:</span><span class="w"> </span><span class="s2">"455187******0181"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Holder"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Nome do Portador"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"ExpirationDate"</span><span class="p">:</span><span class="w"> </span><span class="s2">"12/2027"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"SaveCard"</span><span class="p">:</span><span class="w"> </span><span class="kc">false</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Brand"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Undefined"</span><span class="w">
    </span><span class="p">},</span><span class="w">
    </span><span class="nt">"VelocityAnalysis"</span><span class="p">:</span><span class="w"> </span><span class="p">{</span><span class="w">
      </span><span class="nt">"Id"</span><span class="p">:</span><span class="w"> </span><span class="s2">"2d5e0463-47be-4964-b8ac-622a16a2b6c4"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"ResultMessage"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Reject"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Score"</span><span class="p">:</span><span class="w"> </span><span class="mi">100</span><span class="p">,</span><span class="w">
      </span><span class="nt">"RejectReasons"</span><span class="p">:</span><span class="w"> </span><span class="p">[</span><span class="w">
        </span><span class="p">{</span><span class="w">
          </span><span class="nt">"RuleId"</span><span class="p">:</span><span class="w"> </span><span class="mi">49</span><span class="p">,</span><span class="w">
          </span><span class="nt">"Message"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Bloqueado pela regra CardNumber. Name: M&aacute;ximo de 3 Hits de Cart&atilde;o em 1 dia. HitsQuantity: 3\. HitsTimeRangeInSeconds: 1440\. ExpirationBlockTimeInSeconds: 1440"</span><span class="w">
        </span><span class="p">}</span><span class="w">
      </span><span class="p">]</span><span class="w">
    </span><span class="p">},</span><span class="w">
    </span><span class="nt">"PaymentId"</span><span class="p">:</span><span class="w"> </span><span class="s2">"2d5e0463-47be-4964-b8ac-622a16a2b6c4"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"CreditCard"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Amount"</span><span class="p">:</span><span class="w"> </span><span class="mi">10000</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Currency"</span><span class="p">:</span><span class="w"> </span><span class="s2">"BRL"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Country"</span><span class="p">:</span><span class="w"> </span><span class="s2">"BRA"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Provider"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Simulado"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"ReasonCode"</span><span class="p">:</span><span class="w"> </span><span class="mi">16</span><span class="p">,</span><span class="w">
    </span><span class="nt">"ReasonMessage"</span><span class="p">:</span><span class="w"> </span><span class="s2">"AbortedByFraud"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Status"</span><span class="p">:</span><span class="w"> </span><span class="mi">0</span><span class="p">,</span><span class="w">
    </span><span class="nt">"ProviderReturnCode"</span><span class="p">:</span><span class="w"> </span><span class="s2">"BP171"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"ProviderReturnMessage"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Rejected by fraud risk (velocity)"</span><span class="p">,</span><span class="w">
    </span><span class="nt">"Links"</span><span class="p">:</span><span class="w"> </span><span class="p">[</span><span class="w">
      </span><span class="p">{</span><span class="w">
        </span><span class="nt">"Method"</span><span class="p">:</span><span class="w"> </span><span class="s2">"GET"</span><span class="p">,</span><span class="w">
        </span><span class="nt">"Rel"</span><span class="p">:</span><span class="w"> </span><span class="s2">"self"</span><span class="p">,</span><span class="w">
        </span><span class="nt">"Href"</span><span class="p">:</span><span class="w"> </span><span class="s2">"https://apiquery.cieloecommerce.cielo.com.br/1/sales/2d5e0463-47be-4964-b8ac-622a16a2b6c4"</span><span class="w">
      </span><span class="p">}</span><span class="w">
    </span><span class="p">]</span><span class="w">
  </span><span class="p">}</span><span class="w">
</span><span class="p">}</span><span class="w">

</span></code></pre></div>

## Criando Regras de seguran&ccedil;a Velocity

Para que o velocity funcione, o HD necessitar&aacute; cadastrar as regras de analise que o lojista solcitiar.

Antes de realizar o cadastro das regras, &eacute; importante compreender o funcionamento do Velocity:

A an&aacute;lise ocorre em cima de cada `elemento de rastreabilidade`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} (ER), contando quantas vezes (Q) o elemento foi identificado dentro de um determinado per&iacute;odo (P)

`Elementos de rastreabilidade`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} s&atilde;o:

| **Elementos de Rastreabilidade** |
| --- |
| 12 primeiros d&iacute;gitos do cart&atilde;o de cr&eacute;dito |
| Nome do portador do cart&atilde;o de cr&eacute;dito |
| CEP do endere&ccedil;o de cobran&ccedil;a |
| N&uacute;mero do cart&atilde;o de cr&eacute;dito |
| CEP do endere&ccedil;o de entrega |
| Documento do comprador |
| E-mail do comprador |
| N&uacute;mero do pedido |
| IP do comprador |

| Variavel | Descri&ccedil;&atilde;o |
| --- | --- |
| **ER** | Elemento de Rastreabilidade |
| **Q** | Quantidade |
| **P** | Per&iacute;odo |

Essas variaveis s&atilde;o analisadas seguindo a seguinte formula:

* **ER** = N&uacute;mero do cart&atilde;o de cr&eacute;dito
* **Q** = M&aacute;ximo de 5 hits
* **P** = 12 horas

**Regra** = M&aacute;ximo de 5 hits de cart&atilde;o em 12 hora(s)

> **Com isso, o Velocity executa a seguinte compara&ccedil;&atilde;o:** Ao receber a 6&ordf; transa&ccedil;&atilde;o com o mesmo n&uacute;mero de cart&atilde;o (ER) das outras 5 anteriores, a regra acima ao ser executada e detectar que a quantidade (Q) excedeu as 5 permitidas no per&iacute;odo (P) entre a data da primeira transa&ccedil;&atilde;o e a data da 6&ordf; recebida, a mesma ter&aacute; o **status de rejeitada**, o cart&atilde;o ir&aacute; para quarentena e a resposta ter&aacute; o conte&uacute;do de que a transa&ccedil;&atilde;o foi bloqueada devido a regra.

O Cadastro &eacute; realizado dentro da tela de configura&ccedil;&atilde;o do Velocity:

1 - Dentro de **Demais funcionalidades** clique em **“Configurar”**

![](/uploads/versions/V2---x----379-195x---.JPG)

2 - A tela abaixo &eacute; a tela de configura&ccedil;&atilde;o do Velocity e todas as suas funcionalidades. Clique em “Regras”:

![](/uploads/versions/V3---x----1009-745x---.JPG)

2 - Dentro de “Regra”, basta incluir as regras desejadas pelo lojista:

![](/uploads/versions/V4---x----1394-516x---.JPG)

&nbsp;

**OBS**: As regras ser&atilde;o aplic&aacute;veis apenas se elas estiverem selecionadas como “Habilitado”, caso contrario, elas estar&atilde;o registradas, mas n&atilde;o ser&atilde;o usadas na analise.

### Exemplos de LOG

Abaixo, como uma transa&ccedil;&atilde;o bloqueada por Velocity &eacute; apresentada no LOG

ADICIONAR Log1

## Quarentena

A Quarentena &eacute; uma tabela que armazena os valores por tipo de `Elementos de rastreabilidade`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} com um determinado tempo de expira&ccedil;&atilde;o.

Ao cadastrar uma regra &eacute; poss&iacute;vel especificar quanto tempo o valor de um determinado `Elemento de rastreabilidade`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} ir&aacute; ser levado em considera&ccedil;&atilde;o nas pr&oacute;ximas an&aacute;lises, ou seja, se o lojista quiser identificar a quantidade de vezes que o mesmo n&uacute;mero de cart&atilde;o se repetiu para um per&iacute;odo de 12 horas dentro de um intervalo de 2 dias, n&atilde;o ser&aacute; necess&aacute;rio o Velocity realizar esta contagem retroativa agrupando por per&iacute;odo. Neste cen&aacute;rio por exemplo, a aplica&ccedil;&atilde;o teria que realizar a contagem para os seguintes intervalos:

* D-2 = 0h as 12h
* D-2 = 12h as 0h
* D-1 = 0h as 12h
* D-1 = 12h as 0h

Com a quarentena, a aplica&ccedil;&atilde;o n&atilde;o ir&aacute; realizar essa contagem retroativa por per&iacute;odo, pois ao realizar uma an&aacute;lise, ser&aacute; verifica se existe algum valor do `Elemento de rastreabilidade`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} em quarentena.

**Exemplo:** Usando a regra acima, o tempo de expira&ccedil;&atilde;o se definido em 2 dias, a regra ser&aacute; analisada apenas para o per&iacute;odo j&aacute; configurado, ou seja, 12 horas para traz e ir&aacute; verificar durante 2 dias se n&uacute;mero do cart&atilde;o se encontra em quarentena.

**OBS**: Uma transa&ccedil;&atilde;o analisada, n&atilde;o bloqueada pela regra, mas bloqueada pela quarentena, tem o retorno informando que a mesma foi bloqueada pela quarentena.

<div class="highlighter-rouge"><pre class="highlight"><code><span class="p">{</span><span class="w">
      </span><span class="nt">"RuleId"</span><span class="p">:</span><span class="mi">18</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Message"</span><span class="p">:</span><span class="s2">"Bloqueado pela Quarentena - regra CardNumber. Name: M&aacute;ximo de
5 Hits de Cart&atilde;o em 12 hora(s). HitsQuantity:5. HitsTimeRangeInSeconds:43200. ExpirationBlockTimeInSeconds:86400"</span><span class="w">
   </span><span class="p">}</span><span class="w">
</span><span class="err">],</span><span class="w">
</span><span class="s2">"CorrelationId"</span><span class="err">:</span><span class="s2">"71c72be9-d16c-48d6-b949-
68f16835a772"</span><span class="err">,</span><span class="w">
</span><span class="s2">"ResultMessage"</span><span class="err">:</span><span class="s2">"Reject"</span><span class="err">,</span><span class="w">
</span><span class="s2">"Score"</span><span class="err">:</span><span class="mi">100</span><span class="err">,</span><span class="w">
</span><span class="s2">"ByPassed"</span><span class="err">:</span><span class="kc">false</span><span class="err">,</span><span class="w">
</span><span class="s2">"TransactionId"</span><span class="err">:</span><span class="s2">"a221f50c-14b4-483d-bfe3-
ea7549c148b9"</span><span class="err">,</span><span class="w">
</span><span class="s2">"Links"</span><span class="err">:</span><span class="p">[</span><span class="w">
   </span><span class="p">{</span><span class="w">
      </span><span class="nt">"Method"</span><span class="p">:</span><span class="s2">"GET"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Rel"</span><span class="p">:</span><span class="s2">"self"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"Href"</span><span class="p">:</span><span class="s2">"https://apiquery.cieloecommerce.cielo.com.br/Analysis/a221f50c-14b4-483d-bfe3-ea7549c148b9"</span><span class="w">
   </span><span class="p">}</span><span class="w">
</span><span class="p">]</span><span class="w">
</span><span class="err">}</span><span class="w">

</span></code></pre></div>

### Como configurar uma Quarentena

A configura&ccedil;&atilde;o da Quarentena &eacute; realizada pelo HD Cielo. O lojista deve informar os dados abaixo:

* Valor - Quantas vezes vai se repetir
* Data da expira&ccedil;&atilde;o da quarentena
* Regras:

M&aacute;ximo de 5 Hits de Cart&atilde;o em 12 horas M&aacute;ximo de 5 Hits de Documentos em 12 horas M&aacute;ximo de 7 Hits de Cart&atilde;o em 7 dias M&aacute;ximo de 7 Hits de Documentos em 7 dias

O Cadastro &eacute; realizado dentro da tela de configura&ccedil;&atilde;o do Velocity:

1 - Dentro de **Demais funcionalidades** clique em **“Configurar”**

![](/uploads/versions/V2---x----379-195x---.JPG)

2 - Na tela de configura&ccedil;&otilde;es do Velocity clique em “Quarentena”:

![](/uploads/versions/V3---x----1009-745x---.JPG)

2 - Dentro de “Quarentena”, basta incluir as variaveis enviadas pelo lojista:

![](/uploads/versions/V5---x----1016-782x---.JPG)

### Exemplos de LOG

Abaixo, como uma transa&ccedil;&atilde;o bloqueada por Quarentena no Velocity &eacute; apresentada no LOG

ADICIONAR LogQ1

## Blacklist

A BlackList &eacute; uma tabela oferecida pelo Velocity onde se armazena valores por tipo de `elementos de rastreabilidades`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} que o lojista deseja **bloquear** automaticamente.

Em transa&ccedil;&atilde;o a ser analisada, caso `elementos de rastreabilidades`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge}/Documento que esteja na blacklist, a mesma ser&aacute; bloqueada, independente de existir regra cadastra para este tipo de elemento de rastreabilidade ou n&atilde;o, e ter&aacute; o retorno informado que a mesma foi **bloqueada pela blacklist**, ou seja, a transa&ccedil;&atilde;o n&atilde;o ser&aacute; enviada a Autoriza&ccedil;&atilde;o

### Como configurar uma Blacklist

A configura&ccedil;&atilde;o da Blacklist &eacute; realizada via o HD Cielo. Basta solicitar a libera&ccedil;&atilde;o da funcionalidade no Velocity informando os dados abaixo:

* Qual `elemento de rastreabilidade`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} dever&aacute; ser bloqueado / EX: Identidade
* Informar o valor do `elemento de rastreabilidade`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge}a ser bloqueado /EX: Identidade = 21.435.787-95

&Eacute; possivel realizar varios cadastros para diferentes `elementos de rastreabilidades`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge}. Caso eles sejam reconhecidos no contrato, a transa&ccedil;&atilde;o n&atilde;o ser&aacute; enviada a Autoriza&ccedil;&atilde;o

O Cadastro &eacute; realizado dentro da tela de configura&ccedil;&atilde;o do Velocity:

1 - Dentro de **Demais funcionalidades** clique em **“Configurar”**

![](/uploads/versions/V2---x----379-195x---.JPG)

2 - Na tela de configura&ccedil;&otilde;es do Velocity clique em “Blacklist”:

![](/uploads/versions/V3---x----1009-745x---.JPG)

2 - Dentro de “Blacklist”, basta incluir as variaveis enviadas pelo lojista:

![](/uploads/versions/V6---x----1013-527x---.JPG)

## Whitelist

A Whitelist &eacute; uma tabela oferecida pelo Velocity onde se armazena valores por tipo de `elementos de rastreabilidades`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} que o lojista deseja **liberar** automaticamente das regras de seguran&ccedil;a do velocity.

Em transa&ccedil;&atilde;o a ser analisada, caso `elementos de rastreabilidades`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge}/Documento que esteja na Whitelist, a mesma n&atilde;o ser&aacute; analisada pelo velocity, independente de existir regra cadastra para este tipo de elemento de rastreabilidade ou n&atilde;o, sendo enviada para a autoriza&ccedil;&atilde;o como uma transa&ccedil;&atilde;o normal.

### Como configurar uma Whitelist

A configura&ccedil;&atilde;o da Whitelist &eacute; realizada via o HD Cielo. Basta solicitar a libera&ccedil;&atilde;o da funcionalidade no Velocity informando os dados abaixo:

* Qual `elemento de rastreabilidade`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge} dever&aacute; ser incluso na Whitelist / EX: Identidade
* Informar o valor do `elemento de rastreabilidade`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge}a ser liberado /EX: Identidade = 21.435.787-95

&Eacute; possivel realizar varios cadastros para diferentes `elementos de rastreabilidades`{: .highlighter-rouge.highlighter-rouge.highlighter-rouge.highlighter-rouge}. Caso eles sejam reconhecidos no contrato, a transa&ccedil;&atilde;o ser&aacute; enviada a Autoriza&ccedil;&atilde;o sem ser analisada pelo Velocity

O Cadastro &eacute; realizado dentro da tela de configura&ccedil;&atilde;o do Velocity:

1 - Dentro de **Demais funcionalidades** clique em **“Configurar”**

![](/uploads/versions/V2---x----379-195x---.JPG)

2 - Na tela de configura&ccedil;&otilde;es do Velocity clique em “Whitelist”:

![](/uploads/versions/V3---x----1009-745x---.JPG)

2 - Dentro de “Whitelist”, basta incluir as variaveis enviadas pelo lojista:

![](/uploads/versions/V6---x----1013-527x---.JPG)

## Hist&oacute;rico de Atualiza&ccedil;&otilde;es:

| Vers&atilde;o | Data | Descri&ccedil;&atilde;o |
| --- | --- | --- |
| 1.0 | 28/08/2017 | ✓ Vers&atilde;o inicial |
