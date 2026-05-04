# Tech Challenge 1 — NPS Preditivo em E-commerce

Este projeto foi desenvolvido como parte do **Tech Challenge — Fase 1** da pós-graduação em Inteligência Artificial, com o objetivo de analisar fatores operacionais que influenciam a satisfação de clientes em um contexto de e-commerce.

O estudo utiliza uma base histórica com dados de pedidos, entregas, atendimento e satisfação do cliente, tendo como principal variável de análise o `nps_score`.

## 1. Objetivo do Projeto

O objetivo principal deste projeto é compreender quais fatores operacionais estão associados à satisfação dos clientes em um e-commerce, utilizando o **Net Promoter Score (NPS)** como métrica central.

A análise busca responder perguntas como:

- Quais fatores parecem mais críticos para a satisfação do cliente?
- O que mais gera clientes detratores?
- Existe algum ponto de ruptura na experiência do cliente?
- Que tipo de cliente tende a apresentar NPS mais alto ou mais baixo?
- Como um modelo preditivo poderia apoiar a empresa na antecipação da satisfação do cliente?

Além da análise exploratória, o projeto também apresenta uma proposta opcional de modelo preditivo utilizando **Regressão Linear Múltipla** para estimar a nota de NPS e, posteriormente, classificá-la em categorias tradicionais do NPS:

- **Detrator**: notas de 0 a 6;
- **Neutro**: notas de 7 a 8;
- **Promotor**: notas de 9 a 10.

## 2. Contexto do Problema

Em um cenário de crescimento acelerado do e-commerce, empresas passam a lidar com volumes cada vez maiores de pedidos, entregas e interações com clientes.

Apesar de indicadores operacionais semelhantes, alguns clientes tornam-se promotores da marca, enquanto outros se tornam detratores. Essa diferença levanta uma questão importante para o negócio:

> Quais fatores operacionais influenciam a satisfação do cliente e como a empresa pode agir de forma proativa para melhorar a experiência antes mesmo da aplicação da pesquisa de NPS?

Atualmente, o NPS é coletado após a jornada de compra. Isso limita a capacidade da empresa de antecipar problemas e agir preventivamente. Por isso, a proposta deste projeto é transformar dados operacionais em insights acionáveis para áreas como logística, atendimento, produto e estratégia.

## 3. Descrição da Base de Dados

A base utilizada contém informações históricas de pedidos, entregas, atendimento ao cliente e indicadores de satisfação.

### Dicionário de Dados

| Variável | Descrição |
|---|---|
| `customer_id` | Identificador único do cliente. |
| `order_id` | Identificador único do pedido. |
| `customer_age` | Idade do cliente. |
| `customer_region` | Região geográfica do cliente. |
| `customer_tenure_months` | Tempo de relacionamento do cliente com a empresa, em meses. |
| `order_value` | Valor total do pedido. |
| `items_quantity` | Quantidade de itens no pedido. |
| `discount_value` | Valor de desconto aplicado ao pedido. |
| `payment_installments` | Número de parcelas do pagamento. |
| `delivery_time_days` | Tempo total de entrega, em dias. |
| `delivery_delay_days` | Quantidade de dias de atraso na entrega. |
| `freight_value` | Valor do frete. |
| `delivery_attempts` | Número de tentativas de entrega. |
| `customer_service_contacts` | Número de contatos do cliente com o atendimento. |
| `resolution_time_days` | Tempo para resolução de problemas, em dias. |
| `complaints_count` | Número de reclamações registradas pelo cliente. |
| `repeat_purchase_30d` | Indica se houve recompra em até 30 dias após o pedido: `0 = não`, `1 = sim`. |
| `csat_internal_score` | Score interno de satisfação do cliente. |
| `nps_score` | Nota de satisfação do cliente, variando de 0 a 10, coletada após a experiência de compra. |

## 4. Estrutura do Projeto

```text
tech-challenge-1-nps-preditivo/
│
├── data/
│   ├── raw/
│   │   └── desafio_nps_fase_1.csv
│   ├── processed/
│   │   └── base_nps_tratada.csv
│
├── models/
│   ├── modelo_classificacao_nps.pkl
│   ├── modelo_regressao_linear_multipla_nps.pkl
│
├── notebooks/
│   ├── 01_entendimento_negocio_e_target.ipynb
│   ├── 02_eda_nps.ipynb
│   └── 03_modelo_preditivo_opcional.ipynb
│
├── reports/
│   ├── figures/
│   └── slides/
│
├── README.md
├── requirements.txt
└── LICENSE
```

## 5. Metodologia Utilizada

O projeto foi dividido em três grandes etapas analíticas e uma etapa opcional de modelagem.

### 5.1 Entendimento do Negócio e Definição da Target

No primeiro notebook, o foco está na compreensão conceitual do problema. São discutidos:

- problema de negócio resolvido;
- importância do NPS para o e-commerce;
- áreas beneficiadas pelos insights;
- impacto do NPS em recompra, boca a boca e market share;
- definição da variável alvo;
- riscos e limitações do uso do `nps_score`.

A variável alvo escolhida foi:

```text
nps_score
```

Ela representa a nota de satisfação do cliente, em uma escala de 0 a 10, coletada após a experiência de compra.

---

### 5.2 Análise Exploratória dos Dados

No segundo notebook, é realizada uma análise exploratória com foco em negócio. O objetivo não é apenas descrever estatísticas, mas transformar os dados em interpretações úteis para tomada de decisão.

Foram utilizadas análises como:

- distribuição geral do NPS;
- classificação dos clientes em detratores, neutros e promotores;
- análise de NPS por região;
- análise de NPS por atraso na entrega;
- análise de NPS por contatos com atendimento;
- análise de NPS por reclamações;
- análise de recompra em até 30 dias;
- matriz de correlação entre variáveis numéricas.

Os principais recursos visuais utilizados foram:

- tabelas;
- histogramas;
- gráficos de barras;
- gráfico de correlação.

---

### 5.3 Modelo Preditivo Opcional

No terceiro notebook, é apresentada uma proposta simples de modelo preditivo utilizando **Regressão Linear Múltipla**.

A escolha desse modelo foi feita por dois motivos:

1. É um modelo interpretável e adequado para uma primeira abordagem preditiva;
2. Permite estimar a nota de NPS em uma escala contínua de 0 a 10.

Após prever a nota de NPS, a previsão é convertida em uma categoria gerencial:

| Faixa da nota prevista | Categoria |
|---|---|
| 0 a 6 | Detrator |
| 7 a 8 | Neutro |
| 9 a 10 | Promotor |

Essa abordagem permite conectar o resultado quantitativo do modelo com a lógica tradicional do NPS.

---

## 6. Tecnologias Utilizadas

O projeto foi desenvolvido em Python, utilizando principalmente as seguintes bibliotecas:

```text
pandas
numpy
matplotlib
scikit-learn
jupyter
notebook
```

---

## 7. Como Reproduzir os Resultados

### 7.1 Clonar o repositório

```bash
git clone https://github.com/SEU-USUARIO/tech-challenge-1-nps-preditivo.git
```

Acesse a pasta do projeto:

```bash
cd tech-challenge-1-nps-preditivo
```

---

### 7.2 Criar um ambiente virtual

No Windows, usando Git Bash ou terminal:

```bash
python -m venv .venv
```

Ative o ambiente virtual:

```bash
source .venv/Scripts/activate
```

No Linux ou macOS:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

---

### 7.3 Instalar as dependências

```bash
pip install -r requirements.txt
```

---

### 7.4 Conferir a base de dados

A base de dados deve estar no seguinte caminho:

```text
data/raw/desafio_nps_fase_1.csv
```

Os notebooks utilizam caminhos relativos a partir da pasta `notebooks/`. Portanto, o caminho de leitura da base é:

```python
../data/raw/desafio_nps_fase_1.csv
```

---

### 7.5 Executar os notebooks

Abra o Jupyter Notebook:

```bash
jupyter notebook
```

Depois execute os notebooks na seguinte ordem:

```text
1. notebooks/01_entendimento_negocio_e_target.ipynb
2. notebooks/02_eda_nps.ipynb
3. notebooks/03_modelo_preditivo_opcional.ipynb
```

## 8. Resultados Esperados

Ao reproduzir o projeto, espera-se obter:

- entendimento estruturado do problema de negócio;
- definição clara da variável alvo;
- análise exploratória dos principais fatores associados ao NPS;
- identificação de possíveis fatores geradores de detratores;
- gráficos e tabelas para apoiar a apresentação executiva;
- proposta de modelo preditivo simples para antecipação da satisfação do cliente.

## 9. Material de Apresentação

Além dos notebooks, o projeto inclui uma pasta destinada ao material executivo:

```text
reports/slides/
```

Essa pasta pode conter:

- apresentação em PowerPoint;
- versão em PDF da apresentação;
- materiais auxiliares usados no vídeo executivo.

A apresentação é voltada a um público não técnico, com foco em storytelling, principais insights, recomendações práticas e limitações da análise.

## 10. Limitações

Este projeto possui algumas limitações importantes:

- O NPS é coletado apenas após a experiência de compra;
- A análise identifica associações, mas não necessariamente causalidade;
- O modelo preditivo é uma primeira abordagem simplificada;
- Variáveis externas, como concorrência, sazonalidade e campanhas comerciais, não foram consideradas;
- A interpretação dos resultados deve ser feita em conjunto com o conhecimento das áreas de negócio.

## 11. Autor

Projeto desenvolvido por **Vinicius Rio** como parte do Tech Challenge da pós-graduação em Inteligência Artificial.
