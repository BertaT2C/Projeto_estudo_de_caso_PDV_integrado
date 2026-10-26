# Projeto de estudo de caso — PDV integrado à máquina automatizada de bebidas

![Captura_de_tela_2024-02-02_144113-removebg-preview](https://github.com/BertaT2C/Projeto_estudo_de_caso_PDV_integrado/assets/99225701/bb933a64-5495-432f-9881-e877394c7f53)

## 🚨 Aviso importante

**Este projeto é um estudo de caso inteiramente fictício.** Não se refere a nenhuma empresa, cliente, produto ou serviço real. Os dados, as regras e os cenários foram definidos exclusivamente para demonstrar competências de **Análise de Negócios, modelagem de processos e especificação funcional de uma integração entre sistemas**.

Qualquer semelhança com organizações ou situações reais é mera coincidência. As melhorias descritas representam **benefícios esperados**, não resultados medidos em produção.

## Projeto com estudo de caso de empresa B2C — integração de máquinas

### Contexto do negócio e funcionamento

O cenário simula a integração entre um **PDV (Ponto de Venda)** e o **ABS**, um sistema automatizado para servir bebidas. **Após a finalização da venda**, o PDV envia um comando ao ABS para que a bebida seja preparada de acordo com as características do pedido e as regras de negócio abaixo.

O objetivo do processo é descrever o funcionamento da máquina de bebidas, considerando o tipo de bebida, o recipiente, a quantidade de gelo, o tamanho selecionado e a modalidade de consumo.

### Regras de negócio do ABS

1. **Sabores disponíveis:** o ABS oferece **4 sabores** de bebida, sendo **2 refrigerantes** (Coca e Guaraná) e **2 sucos** (Uva e Laranja).
2. **Tipo de copo:** os **refrigerantes** são servidos em **copos de papel**, enquanto os **sucos** são servidos em **copos de plástico**.
3. **Quantidade de gelo:** os refrigerantes recebem **6 pedras de gelo** e os sucos recebem **12 pedras de gelo**. Também existe a opção de servir **sem gelo**.
4. **Tamanhos disponíveis:** os refrigerantes possuem **3 opções** (**300 ml, 500 ml e 700 ml**), enquanto os sucos possuem **2 opções** (**300 ml e 500 ml**).
5. **Tipo de tampa:** pedidos **Take Out (Delivery)** recebem **tampa sem furo**; pedidos **Eat In** (consumo no restaurante) recebem **tampa com furo para canudo**.

Essas regras definem as condições funcionais para a preparação da bebida após a conclusão da venda no PDV.

## Benefícios esperados

- **Automatizar a saída de bebidas**, buscando eliminar desperdícios.
- **Reduzir o tempo de ciclo**, aumentando a eficiência do processo.
- **Eliminar atividades desnecessárias** na operação.
- **Permitir a visualização do processo de ponta a ponta**, do fechamento da venda à preparação da bebida.

### Fluxograma original do processo

![Fluxograma ABS maquina de bebidas](https://github.com/BertaT2C/Projeto_estudo_de_caso_PDV_integrado/assets/99225701/c843fa92-faa8-44c2-9f5d-efd83dba38a7)

### Imagem complementar original

![download](https://github.com/BertaT2C/Projeto_estudo_de_caso_PDV_integrado/assets/99225701/c10eeef1-63e2-4f2a-9738-b51b450fd9ca)

---

## Visão funcional para Análise de Negócios

A sequência abaixo é uma **leitura textual das regras do estudo de caso**. Ela complementa as imagens existentes, sem substituir ou alterar o fluxograma original.

| Etapa | Entrada ou condição | Comportamento previsto |
| --- | --- | --- |
| **1. Venda no PDV** | Venda finalizada | Enviar comando de preparo ao ABS |
| **2. Identificação da bebida** | Refrigerante ou suco, conforme o pedido | Selecionar as regras correspondentes à bebida |
| **3. Definição do recipiente** | Refrigerante / suco | Utilizar copo de papel / plástico, respectivamente |
| **4. Definição do gelo** | Tipo de bebida e opção sem gelo | Aplicar 6 ou 12 pedras, ou não adicionar gelo |
| **5. Verificação do tamanho** | Tamanho escolhido no pedido | Considerar apenas os tamanhos disponíveis para o tipo de bebida |
| **6. Finalização do preparo** | Take Out ou Eat In | Aplicar a tampa correspondente à modalidade de consumo |

### Exemplos de critérios de aceitação derivados das regras

*Exemplos de especificação funcional, elaborados a partir do cenário fictício; não são evidência de testes já executados.*

**Cenário 1 — Refrigerante com gelo**

- **Dado** um pedido de refrigerante em tamanho disponível, com gelo e na modalidade *Take Out*;
- **Quando** a venda for finalizada e o comando de preparo for enviado ao ABS;
- **Então** o preparo deverá utilizar **copo de papel**, **6 pedras de gelo** e **tampa sem furo**.

**Cenário 2 — Suco sem gelo**

- **Dado** um pedido de suco em tamanho disponível, com a opção **sem gelo** e na modalidade *Eat In*;
- **Quando** a venda for finalizada e o comando de preparo for enviado ao ABS;
- **Então** o preparo deverá utilizar **copo de plástico**, **sem gelo** e **tampa com furo**.

**Cenário 3 — Restrições de tamanho**

- **Dado** que a bebida selecionada seja **refrigerante**;
- **Quando** o tamanho do pedido for considerado para o preparo;
- **Então** os tamanhos previstos serão **300 ml, 500 ml e 700 ml**.

- **Dado** que a bebida selecionada seja **suco**;
- **Quando** o tamanho do pedido for considerado para o preparo;
- **Então** os tamanhos previstos serão **300 ml e 500 ml**.

> **Escopo do estudo:** a documentação original não define retorno de erros do ABS, protocolo técnico de integração, autenticação, monitoramento ou regras para falha de comunicação. Esses aspectos não foram inventados nesta apresentação.

## Competências evidenciadas pelo estudo

**Análise de Negócios · Levantamento e documentação de requisitos · Regras de negócio · Mapeamento de processos · Integração entre sistemas · Especificação funcional · Critérios de aceitação · Visão ponta a ponta · Melhoria contínua**

**Fonte do material:** [README original preservado](./DOCUMENTACAO_ORIGINAL.md). As três imagens e os dados do case permanecem nos mesmos arquivos e na mesma sequência de apresentação.
