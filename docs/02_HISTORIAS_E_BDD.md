# Histórias de usuário e critérios de aceitação | PDV integrado ao ABS

**Classificação:** documentação **proposta para demonstração**, derivada do estudo fictício.  
**Fonte das regras:** [documentação original](../DOCUMENTACAO_ORIGINAL.md) e [matriz de regras](./01_ESPECIFICACAO_FUNCIONAL.md).

> As histórias e IDs abaixo foram criados para demonstrar prática de **Análise de Negócios, User Stories, BDD e critérios de aceite**. Não significam que houve desenvolvimento, implementação, homologação ou aprovação por um cliente real.

## HU-01 — Disparo do preparo após a venda

**Como** operação de ponto de venda, **quero** que o PDV envie um comando ao ABS após a finalização da venda, **para** iniciar o preparo da bebida conforme as regras do pedido.

**Critério de aceitação — cenário 01:**

- **Dado** que uma venda de bebida foi finalizada no PDV;
- **Quando** ocorrer a etapa de integração descrita no estudo;
- **Então** deverá ser enviado um **comando de preparo** à máquina ABS.

**Rastreabilidade:** descrição original de integração / RF-01.

## HU-02 — Sabores e categoria de bebida

**Como** pessoa que realiza um pedido, **quero** escolher um dos sabores previstos no estudo, **para** receber a bebida selecionada.

**Critério de aceitação — cenário 02 (refrigerante):**

- **Dado** que o pedido seja de refrigerante;
- **Quando** forem apresentadas as opções disponíveis;
- **Então** devem constar **Coca** e **Guaraná**.

**Critério de aceitação — cenário 03 (suco):**

- **Dado** que o pedido seja de suco;
- **Quando** forem apresentadas as opções disponíveis;
- **Então** devem constar **Uva** e **Laranja**.

**Rastreabilidade:** RN-01 / RF-02.

## HU-03 — Recipiente por categoria

**Como** operação de preparo, **quero** que o tipo de copo seja definido pela categoria da bebida, **para** respeitar a padronização definida no caso.

**Critério de aceitação — cenário 04:**

- **Dado** um pedido de refrigerante;
- **Quando** a bebida for preparada;
- **Então** deverá ser utilizado **copo de papel**.

**Critério de aceitação — cenário 05:**

- **Dado** um pedido de suco;
- **Quando** a bebida for preparada;
- **Então** deverá ser utilizado **copo de plástico**.

**Rastreabilidade:** RN-02 / RF-03.

## HU-04 — Gelo padrão e opção sem gelo

**Como** pessoa que realiza um pedido, **quero** escolher a opção sem gelo ou receber a quantidade prevista para a bebida, **para** que o preparo respeite minha seleção.

**Critério de aceitação — cenário 06:**

- **Dado** um pedido de refrigerante **com gelo**;
- **Quando** a bebida for preparada;
- **Então** deverão ser adicionadas **6 pedras de gelo**.

**Critério de aceitação — cenário 07:**

- **Dado** um pedido de suco **com gelo**;
- **Quando** a bebida for preparada;
- **Então** deverão ser adicionadas **12 pedras de gelo**.

**Critério de aceitação — cenário 08:**

- **Dado** um pedido com opção **sem gelo**;
- **Quando** a bebida for preparada;
- **Então** **não deverá ser adicionado gelo**, independentemente da categoria.

**Rastreabilidade:** RN-03 / RF-04.

## HU-05 — Tamanhos por categoria

**Como** pessoa que realiza um pedido, **quero** visualizar os tamanhos disponíveis para cada bebida, **para** escolher entre as opções definidas.

**Critério de aceitação — cenário 09:**

- **Dado** que a bebida seja um refrigerante;
- **Quando** os tamanhos disponíveis forem considerados;
- **Então** deverão ser **300 ml, 500 ml e 700 ml**.

**Critério de aceitação — cenário 10:**

- **Dado** que a bebida seja um suco;
- **Quando** os tamanhos disponíveis forem considerados;
- **Então** deverão ser **300 ml e 500 ml**.

**Rastreabilidade:** RN-04 / RF-05.

*O comportamento diante de um tamanho não disponível não foi descrito no estudo original; por isso não há aqui uma regra inventada de rejeição, bloqueio ou mensagem de erro.*

## HU-06 — Tampa por modalidade do pedido

**Como** operação de preparo, **quero** que o tipo de tampa acompanhe a modalidade de consumo, **para** cumprir a regra definida para entrega ou consumo no restaurante.

**Critério de aceitação — cenário 11:**

- **Dado** um pedido do tipo **Take Out (Delivery)**;
- **Quando** a bebida for finalizada;
- **Então** deverá receber **tampa sem furo**.

**Critério de aceitação — cenário 12:**

- **Dado** um pedido do tipo **Eat In** (consumo no restaurante);
- **Quando** a bebida for finalizada;
- **Então** deverá receber **tampa com furo para canudo**.

**Rastreabilidade:** RN-05 / RF-06.

## Exemplo de ponta a ponta — aplicação combinada das regras

**Cenário ilustrativo A — Guaraná, 500 ml, com gelo, Take Out**

- Sabor: **Guaraná**; categoria: refrigerante;
- Recipiente: **copo de papel**;
- Gelo: **6 pedras**;
- Tamanho: **500 ml**;
- Tampa: **sem furo**.

**Cenário ilustrativo B — Uva, 300 ml, sem gelo, Eat In**

- Sabor: **Uva**; categoria: suco;
- Recipiente: **copo de plástico**;
- Gelo: **nenhum**;
- Tamanho: **300 ml**;
- Tampa: **com furo para canudo**.

Estes dois exemplos são **combinações didáticas** das regras originais; não são registros de pedidos reais ou execuções de teste.

## O que não foi determinado

Interface do PDV, layout de telas, formato do comando, status e retorno do ABS, controles de segurança, logs, política de tentativas, sensor de estoque e tratamento de erros **não constam da fonte**. Uma implementação real exigiria Discovery e refinamento adicional.

**Leitura complementar:** [matriz de testes sugeridos](./03_MATRIZ_DE_TESTES.md) · [fluxograma original e imagens](../README.md#fluxograma-original-do-processo).
