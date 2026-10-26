# Especificação funcional | PDV integrado ao ABS

**Tipo:** estudo de caso fictício de Análise de Negócios.  
**Origem:** [documentação original, preservada](../DOCUMENTACAO_ORIGINAL.md).  
**Escopo:** registrar de maneira estruturada as regras descritas no caso; não se trata de uma especificação de integração implementada.

## 1. Objetivo

Descrever o comportamento esperado na integração de um **Ponto de Venda (PDV)** com uma máquina automatizada de servir bebidas (**ABS**) em uma operação fictícia B2C.

**Evento que inicia o processo:** a **venda é finalizada** no PDV.  
**Interação descrita na fonte:** após a finalização, um **comando é enviado ao ABS** para preparar a bebida conforme regras de negócio.

A fonte **não** define API, formato do comando, mensagens técnicas, retornos, falhas, autenticação, sequência detalhada de movimentação física da máquina ou regras de estoque.

## 2. Escopo do processo

**Incluído no caso:** identificação de tipo/sabor da bebida; tipo de copo; quantidade de gelo e opção sem gelo; tamanho disponível; modalidade de consumo; tipo de tampa; visão de preparação após a venda.

**Não especificado na fonte:** múltiplas bebidas em um mesmo pedido, tempo de preparo, descontos, pagamentos, integração fiscal, estoque de insumos, notificações, sensores físicos, tratamento de falha de comunicação, reenvio de comandos ou processos de cancelamento/reembolso.

Tópicos não especificados devem ser tratados como **questões abertas para um projeto real**, não como regras inventadas.

## 3. Regras de negócio — transcrição estruturada

| ID | Regra | Condição | Resultado esperado |
| --- | --- | --- | --- |
| **RN-01** | Cardápio | Categoria refrigerante | Oferecer **Coca** ou **Guaraná** |
| **RN-01** | Cardápio | Categoria suco | Oferecer **Uva** ou **Laranja** |
| **RN-02** | Recipiente | Refrigerante | Servir em **copo de papel** |
| **RN-02** | Recipiente | Suco | Servir em **copo de plástico** |
| **RN-03** | Gelo padrão | Refrigerante, **com gelo** | **6 pedras de gelo** |
| **RN-03** | Gelo padrão | Suco, **com gelo** | **12 pedras de gelo** |
| **RN-03** | Exceção de gelo | Cliente seleciona **sem gelo** | **Não adicionar gelo** |
| **RN-04** | Tamanho | Refrigerante | **300 ml**, **500 ml** ou **700 ml** |
| **RN-04** | Tamanho | Suco | **300 ml** ou **500 ml** |
| **RN-05** | Modalidade | **Take Out (Delivery)** | **Tampa sem furo** |
| **RN-05** | Modalidade | **Eat In** | **Tampa com furo para canudo** |

**Regra de integração descrita:** ao finalizar a venda, o PDV envia um comando de preparo ao ABS. A fonte não especifica campos, estrutura ou protocolo desse comando.

## 4. Matriz de parâmetros por bebida

| Categoria | Sabor | Copo | Gelo se solicitado | Opção sem gelo | Tamanhos permitidos |
| --- | --- | --- | --- | --- | --- |
| Refrigerante | Coca | Papel | 6 pedras | Sim | 300 / 500 / 700 ml |
| Refrigerante | Guaraná | Papel | 6 pedras | Sim | 300 / 500 / 700 ml |
| Suco | Uva | Plástico | 12 pedras | Sim | 300 / 500 ml |
| Suco | Laranja | Plástico | 12 pedras | Sim | 300 / 500 ml |

A **tampa** é determinada pela modalidade do pedido, independentemente da bebida:

| Modalidade | Tampa |
| --- | --- |
| Take Out (Delivery) | Sem furo |
| Eat In (consumo no restaurante) | Com furo para canudo |

> A matriz apenas consolida informações já existentes. Não define uma lista de combinações efetivamente testadas ou implementadas.

## 5. Fluxo funcional em nível macro

1. O PDV registra a finalização da venda.
2. É enviado ao ABS o comando previsto no estudo.
3. O preparo obedece às **regras de bebida, copo, gelo, tamanho e tampa**.
4. O resultado esperado é uma bebida preparada de acordo com essas condições.

**Importante:** esta sequência é uma síntese textual, não um redesenho do processo. O [fluxograma original](../README.md#fluxograma-original-do-processo) continua sendo o artefato visual de referência.

## 6. Requisitos funcionais derivados — proposta de organização

Esses requisitos formalizam **sem ampliar** o comportamento previsto no estudo:

| ID | Requisito funcional | Origem |
| --- | --- | --- |
| **RF-01** | Considerar a venda finalizada como condição de envio do comando de preparo ao ABS | Descrição do processo |
| **RF-02** | Considerar um dos quatro sabores descritos | RN-01 |
| **RF-03** | Aplicar o tipo de copo associado à categoria | RN-02 |
| **RF-04** | Aplicar o gelo padrão da categoria ou a opção sem gelo | RN-03 |
| **RF-05** | Considerar os tamanhos disponíveis para a categoria | RN-04 |
| **RF-06** | Aplicar o tipo de tampa correspondente a Take Out ou Eat In | RN-05 |

*RF-01 a RF-06 são identificadores adicionados para rastreabilidade documental, não IDs recuperados de Jira, backlog de cliente ou software.*

## 7. Pontos que demandariam refinamento em um projeto real

- Quais informações compõem o comando enviado pelo PDV?
- Como o ABS confirma ou sinaliza a conclusão da preparação?
- Como são tratados pedidos com mais de uma bebida?
- O que deve acontecer se o PDV não conseguir comunicar o comando?
- Como são tratadas falta de insumos, indisponibilidade da máquina e cancelamento?
- Como são tratadas opções fora dos tamanhos definidos no caso?

Essas perguntas **não têm resposta no estudo original**. Estão registradas somente como oportunidades de análise futura e não devem ser confundidas com escopo implementado.

## 8. Rastreabilidade

- [Histórias de usuário e critérios de aceitação propostos](./02_HISTORIAS_E_BDD.md)
- [Cenários de teste sugeridos (não executados)](./03_MATRIZ_DE_TESTES.md)
- [Imagens originais e contexto no README](../README.md)
- [Documento original completo](../DOCUMENTACAO_ORIGINAL.md)
