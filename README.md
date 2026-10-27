Estudo de caso | PDV integrado à máquina automatizada de bebidas (ABS)

**Análise de Negócios · Regras de Negócio · Integração de Sistemas · Modelagem de Processos · BDD**

![Imagem de apresentação do estudo de caso](https://github.com/BertaT2C/Projeto_estudo_de_caso_PDV_integrado/assets/99225701/bb933a64-5495-432f-9881-e877394c7f53)

## 🚨 Aviso importante

Este é um **estudo de caso inteiramente fictício**, desenvolvido para demonstrar competências de análise de negócios, estruturação de requisitos e modelagem de sistemas. Não representa empresa, cliente, produto, implantação ou resultado operacional real.

Os cenários, regras e imagens fazem parte de uma simulação. **Os benefícios são esperados, não resultados medidos.**

## Projeto com estudo de caso de empresa B2C — integração de máquinas

### Contexto do negócio

O cenário apresenta um **Ponto de Venda (PDV)** integrado a um sistema automatizado de servir bebidas, identificado como **ABS**.

**Evento principal:** depois que a venda é finalizada, o PDV envia um comando ao ABS para a preparação da bebida de acordo com as regras do pedido.

O objetivo é **descrever o funcionamento da máquina de bebidas** e deixar claro como diferentes combinações de bebida, copo, gelo, tamanho e modalidade de consumo influenciam o preparo.

### Regras de negócio originais

As cinco regras abaixo preservam os dados e as condições definidos para o ABS:

1. **Sabores:** são **4 sabores**, sendo **2 refrigerantes** (**Coca e Guaraná**) e **2 sucos** (**Uva e Laranja**).
2. **Copos:** os **refrigerantes** são servidos em **copos de papel** e os **sucos**, em **copos de plástico**.
3. **Gelo:** refrigerantes recebem **6 pedras de gelo** e sucos recebem **12 pedras de gelo**. O pedido também pode ser preparado **sem gelo**.
4. **Tamanhos:** refrigerantes possuem **300 ml, 500 ml e 700 ml**; sucos possuem **300 ml e 500 ml**.
5. **Tampas:** pedidos **Take Out (Delivery)** recebem **tampa sem furo**; pedidos **Eat In** (consumo no restaurante) recebem **tampa com furo para o canudo**.

Essas regras são a base do processo e dos exemplos funcionais complementares. Nenhuma regra foi adicionada sobre validações, falhas técnicas ou tratamento de pedidos que não constem na fonte.

## Benefícios esperados

- **Automação da saída de bebidas**, com potencial para eliminar desperdícios;
- **Redução do tempo de ciclo**, buscando maior eficiência operacional;
- **Eliminação de atividades desnecessárias** ao longo da operação;
- **Visibilidade do processo de ponta a ponta**, desde a finalização da venda até o preparo.

**Importante:** não há dados de linha de base ou resultados antes/depois neste estudo; portanto, não foram estimados percentuais de ganho, economia ou produtividade.

### Fluxograma original do processo

![Fluxograma original do ABS — máquina de bebidas](https://github.com/BertaT2C/Projeto_estudo_de_caso_PDV_integrado/assets/99225701/c843fa92-faa8-44c2-9f5d-efd83dba38a7)


---

## Visão funcional e lógica de integração

A representação abaixo é uma **leitura textual** da lógica já descrita. O fluxograma acima permanece como evidência visual original.

| Momento | Informação considerada | Comportamento esperado |
| --- | --- | --- |
| Venda concluída no PDV | Finalização da venda | Envio do comando de preparo ao ABS |
| Identificação da bebida | Coca, Guaraná, Uva ou Laranja | Aplicação das regras da categoria |
| Escolha do copo | Refrigerante ou suco | Papel ou plástico, respectivamente |
| Definição do gelo | Categoria e opção sem gelo | 6 pedras, 12 pedras ou nenhuma |
| Definição do tamanho | Categoria da bebida | Refrigerante: 300/500/700 ml; suco: 300/500 ml |
| Modalidade do pedido | Take Out ou Eat In | Tampa sem furo ou com furo para canudo |

### Como a documentação do projeto está organizada

| Material | O que demonstra | Acesso |
| --- | --- | --- |
| **Especificação funcional** | Objetivo, escopo, matriz com **5 regras** e requisitos rastreáveis | [Consultar](./docs/01_ESPECIFICACAO_FUNCIONAL.md) |
| **Histórias de usuário e BDD** | **6 histórias** e **12 cenários** construídos a partir das regras fictícias | [Consultar](./docs/02_HISTORIAS_E_BDD.md) |
| **Matriz de testes** | **15 verificações sugeridas**, 4 exemplos integrados e rastreabilidade | [Consultar](./docs/03_MATRIZ_DE_TESTES.md) |
| **Documentação original** | Texto completo anterior a esta reorganização | [Consultar](./DOCUMENTACAO_ORIGINAL.md) |

> **Rastreabilidade:** RF, HU, BDD e CT são identificadores documentais criados para apresentar o estudo. Eles **não** indicam tarefas reais de Jira, homologações realizadas ou funcionalidades implantadas.

## Exemplos de critérios de aceitação

Os exemplos abaixo resultam **diretamente das regras**. São ilustrações de comportamento esperado, e não testes executados.

**Cenário A — Refrigerante, com gelo, Take Out**

- **Dado** um pedido de refrigerante em um tamanho disponível, com gelo e na modalidade Take Out;
- **Quando** a venda for finalizada e o comando de preparo enviado ao ABS;
- **Então** a bebida deverá usar **copo de papel**, **6 pedras de gelo** e **tampa sem furo**.

**Cenário B — Suco, sem gelo, Eat In**

- **Dado** um pedido de suco em um tamanho disponível, sem gelo e na modalidade Eat In;
- **Quando** a venda for finalizada e o comando de preparo enviado ao ABS;
- **Então** a bebida deverá usar **copo de plástico**, **sem gelo** e **tampa com furo para canudo**.

Mais exemplos e as condições de tamanhos estão em [Histórias e BDD](./docs/02_HISTORIAS_E_BDD.md).

## Competências evidenciadas

**Business Analysis | Análise de Requisitos | Regras de Negócio | Especificação Funcional | Mapeamento de Processos | Integração de Sistemas | User Stories | BDD | Critérios de Aceitação | Testes de Usuário (planejamento) | Melhoria Contínua**

### Limites do estudo

A fonte não descreve API ou formato do comando, autenticação, resultados da máquina, falhas de comunicação, cancelamento, estoque ou controle físico dos insumos. Essas questões estão identificadas como **pontos de refinamento futuro**, não como comportamento implementado.

