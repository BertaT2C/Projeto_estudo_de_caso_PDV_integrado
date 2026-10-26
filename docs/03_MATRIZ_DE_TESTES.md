# Matriz de cenários de teste | PDV integrado ao ABS

**Status de todos os casos:** **propostos e não executados**.  
**Base:** [regras originais](../DOCUMENTACAO_ORIGINAL.md), [especificação funcional](./01_ESPECIFICACAO_FUNCIONAL.md) e [12 critérios de aceitação BDD](./02_HISTORIAS_E_BDD.md).

Esta matriz tem finalidade de demonstração de **planejamento de testes de usuário e rastreabilidade**, sem afirmar a existência de software instalado, uma execução em ambiente de QA, resultados de homologação ou defeitos identificados.

## 1. Cenários de validação funcional

| Teste proposto | Condição de entrada | Resultado esperado | Regra |
| --- | --- | --- | --- |
| CT-01 | Venda finalizada no PDV | Enviar comando de preparo ao ABS | Integração / RF-01 |
| CT-02 | Refrigerante / Coca | Sabor disponível | RN-01 |
| CT-03 | Refrigerante / Guaraná | Sabor disponível | RN-01 |
| CT-04 | Suco / Uva | Sabor disponível | RN-01 |
| CT-05 | Suco / Laranja | Sabor disponível | RN-01 |
| CT-06 | Qualquer refrigerante | Copo de papel | RN-02 |
| CT-07 | Qualquer suco | Copo de plástico | RN-02 |
| CT-08 | Refrigerante com gelo | 6 pedras | RN-03 |
| CT-09 | Suco com gelo | 12 pedras | RN-03 |
| CT-10 | Refrigerante sem gelo | Nenhuma pedra | RN-03 |
| CT-11 | Suco sem gelo | Nenhuma pedra | RN-03 |
| CT-12 | Tamanhos de refrigerante | 300, 500 e 700 ml disponíveis | RN-04 |
| CT-13 | Tamanhos de suco | 300 e 500 ml disponíveis | RN-04 |
| CT-14 | Modalidade Take Out (Delivery) | Tampa sem furo | RN-05 |
| CT-15 | Modalidade Eat In | Tampa com furo para canudo | RN-05 |

**Status:** os itens CT-01 a CT-15 são apenas sugestões de verificação. Nenhum resultado real de teste foi fornecido.

## 2. Casos integrados para exercício de ponta a ponta

| Caso | Pedido fictício | Resultado calculado a partir das regras |
| --- | --- | --- |
| E2E-01 | Coca, 300 ml, com gelo, Eat In | Copo de papel; 6 pedras; tampa com furo |
| E2E-02 | Guaraná, 700 ml, sem gelo, Take Out | Copo de papel; sem gelo; tampa sem furo |
| E2E-03 | Uva, 300 ml, sem gelo, Eat In | Copo de plástico; sem gelo; tampa com furo |
| E2E-04 | Laranja, 500 ml, com gelo, Take Out | Copo de plástico; 12 pedras; tampa sem furo |

A presença desses casos na matriz **não** implica que foram executados.

## 3. Rastreabilidade mínima

| Regra | Requisito documental | História e cenários BDD | Testes planejados |
| --- | --- | --- | --- |
| Finalização da venda e comando ao ABS | RF-01 | HU-01 / 01 | CT-01 |
| RN-01 — Sabores | RF-02 | HU-02 / 02 e 03 | CT-02 a CT-05 |
| RN-02 — Copos | RF-03 | HU-03 / 04 e 05 | CT-06 e CT-07 |
| RN-03 — Gelo | RF-04 | HU-04 / 06 a 08 | CT-08 a CT-11 |
| RN-04 — Tamanhos | RF-05 | HU-05 / 09 e 10 | CT-12 e CT-13 |
| RN-05 — Tampas | RF-06 | HU-06 / 11 e 12 | CT-14 e CT-15 |

## 4. Recomendações para um eventual projeto real

**Para definir somente após levantamento e aprovação de requisitos:**

- Regras para pedido inválido ou tamanho não disponível;
- Pedido com mais de uma bebida;
- Retorno de sucesso/falha da máquina ABS;
- Falha de conexão, duplicidade e reprocessamento;
- Falta de gelo, copos, bebidas ou tampas;
- Cancelamento de pedido e rastreabilidade operacional;
- Tempo de ciclo e medições de desperdício.

Não foram estabelecidos aqui resultados de testes, critérios técnicos de aceite de API ou taxas de desempenho que a fonte não apresenta.

---

**Observação:** as três imagens de origem permanecem no [README principal](../README.md), na mesma ordem. A matriz não substitui o fluxo visual do case.
