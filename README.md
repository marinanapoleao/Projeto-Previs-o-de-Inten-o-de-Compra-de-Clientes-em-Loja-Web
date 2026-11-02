# Previsão de Intenção de Compra de Clientes em Loja Web

<img width="480" height="480" alt="1773664259238" src="https://github.com/user-attachments/assets/9cf563e1-be18-4da4-8807-53aa17674bfd" />

## 📌 Sobre o Projeto

Projeto acadêmico desenvolvido durante a formação em Ciência de Dados da EBAC, com foco na construção de um modelo preditivo para identificar clientes com maior propensão a realizar compras em um site de e-commerce.

O projeto utiliza informações demográficas, renda familiar, histórico de consumo e comportamento de compra dos clientes para identificar padrões associados às compras realizadas pela internet.

Foram desenvolvidos e comparados dois modelos de classificação: Regressão Logística e Random Forest. Após a comparação, o modelo Random Forest foi selecionado e submetido à otimização de hiperparâmetros.

## 🎯 Objetivo

Desenvolver um modelo de Machine Learning capaz de identificar clientes com maior probabilidade de realizar compras online, utilizando características demográficas e informações sobre seus comportamentos de consumo anteriores.

O objetivo é permitir que a empresa antecipe o comportamento dos clientes e direcione suas estratégias de marketing de maneira mais eficiente, identificando oportunidades de conversão.

##  <img width="30" height="30" alt="image" src="https://github.com/user-attachments/assets/261dec9b-a66e-44f1-8dc0-694ad8625ff7" />  Problema de Negócio / Pergunta de Pesquisa

*"É possível identificar clientes com maior propensão a realizar compras em uma loja virtual a partir de suas características demográficas, renda e histórico de consumo?"*

Empresas de e-commerce precisam compreender o comportamento dos consumidores para direcionar suas ações comerciais e de marketing.

A identificação de clientes com maior propensão à compra pode ajudar a empresa a:

- Direcionar campanhas de marketing para públicos com maior potencial de conversão.

- Desenvolver ofertas personalizadas de acordo com o perfil de consumo.

- Identificar oportunidades de conversão de visitantes em compradores.

- Melhorar a eficiência das estratégias comerciais.

## 📊 Fonte de Dados

Base de dados marketing_campaign.csv, utilizada no projeto para analisar informações demográficas e comportamentais de clientes.

Características da base original:

- 2.240 registros de clientes.

- 16 variáveis.

- Após o tratamento e a exclusão de três registros, foram mantidos 2.237 registros.

*Variável ——————————	Descrição*

Year_Birth —————————	Ano de nascimento

Education —————————	Escolaridade

Marital_Status ———————	Estado civil

Income ——————————	Renda anual famiar

Kidhome —————————	Número de crianças na residência

Recency —————————	Dias desde a última compra

MntWines ————————	Gastos com vinhos

MntFruits ————————	Gastos com frutas

MntMeatProducts ———— Gastos com carnes

MntFishProducts —————	Gastos com peixes

MntSweetProducts ————	Gastos com doces

MntGoldProds ——————	Gastos com produtos de ouro

NumStorePurchases ————	Compras realizadas em lojas físicas

NumWebVisitsMonth ————	Visitas ao site no último mês

Complain —————————	Registro de reclamação

WebPurchases ——————— Indicador utilizado para identificar compras online

## 🛠️ LINGUAGENS E BIBLIOTECAS

*Tecnologia ———————	Aplicação*

Python ————————	Desenvolvimento do projeto

Pandas ————————	Manipulação e tratamento dos dados

NumPy ————————	Operações numéricas

Matplotlib ———————	Visualização dos dados

Seaborn ————————	Análise exploratória e gráficos estatísticos

Plotly —————————	Visualizações interativas

Scikit-learn ——————	Construção, treinamento e avaliação dos modelos

Imbalanced-learn ———	Balanceamento das classes com SMOTE

Jupyter Notebook ———	Ambiente de desenvolvimento


*Principais algoritmos e recursos utilizados:*

- Logistic Regression (Regressão Logística).

- Random Forest Classifier.

- SMOTE para balanceamento das classes.

- StandardScaler para padronização.

- StratifiedKFold para validação cruzada.

- GridSearchCV para otimização de hiperparâmetros.

- Matriz de confusão e métricas de classificação.

## 🔍 Metodologia

#### *Etapa 1 — Preparação e análise exploratória dos dados*

- Carregamento e exploração da base de dados.
- Verificação dos tipos de variáveis e identificação de valores ausentes.
- Tratamento de 24 valores ausentes na variável Income, utilizando a mediana (51.381,50).
- Identificação de outliers utilizando o método do intervalo interquartil (IQR).
- Exclusão de três registros na variável Year_Birth, correspondentes a idades irreais entre 125 e 132 anos.
- Manutenção dos oito outliers identificados em Income, por representarem possíveis clientes de alta renda.
- Análise do comportamento dos clientes, distribuição de renda, reclamações, consumo e compras realizadas pela internet e em lojas físicas.

#### *Etapa 2 — Pré-processamento*

- Análise de correlação entre as variáveis numéricas.
- Codificação das variáveis categóricas Education e Marital_Status utilizando One-Hot Encoding.
- Separação das variáveis independentes (X) e da variável dependente (Y).
- Definição de WebPurchases como variável-alvo.
- Divisão dos dados em treinamento (70%) e teste (30%), utilizando random_state=42 e estratificação.
- Organização da padronização dentro do Pipeline da Regressão Logística, evitando ajustar o StandardScaler previamente sobre os dados completos.

#### *Etapa 3 — Modelagem*

Foram desenvolvidos dois modelos de classificação:
1. Regressão Logística: modelo utilizado como primeira abordagem para identificar a probabilidade de ocorrência da classe positiva.
2. Random Forest: modelo baseado em conjunto de árvores de decisão, utilizado para identificar padrões mais complexos nos dados.
Foi utilizado SMOTE dentro dos pipelines para lidar com o desbalanceamento das classes.

Os modelos foram avaliados por meio de validação cruzada estratificada com cinco divisões (5-Fold Stratified Cross-Validation).

#### *Etapa 4 — Avaliação e otimização*

Após identificar o Random Forest como modelo de melhor desempenho, foi realizada a otimização dos hiperparâmetros utilizando GridSearchCV.

Foram avaliadas diferentes combinações de parâmetros, como:
- Número de árvores (n_estimators).
- Profundidade máxima (max_depth).
- Número mínimo de amostras para divisão (min_samples_split).
- Número mínimo de amostras por folha (min_samples_leaf).
- Quantidade de variáveis consideradas em cada divisão (max_features).
- Peso das classes (class_weight).

O melhor modelo foi avaliado no conjunto de teste utilizando acurácia, precisão, recall, F1-score e matriz de confusão.


## 📈  Resultados e Métricas

A principal métrica utilizada na comparação foi o Recall, pois o objetivo era identificar o maior número possível de clientes pertencentes à classe positiva.

*Modelo ——————————	Recall médio (validação cruzada)*

Regressão ————————— Logística	0,8164

Random Forest ———————	0,9477

*O Random Forest apresentou melhor desempenho, sendo escolhido para a etapa de otimização.*

*Parâmetro ———————		Melhor configuração*

n_estimators ———————		200

max_depth ————————		10

min_samples_split —————		5

*Avaliação final do Random Forest*

Após a otimização, o modelo apresentou os seguintes resultados no conjunto de teste:

Acurácia:	90,33%

Precisão (classe 1):	87%

Recall (classe 1):	95%

F1-score (classe 1):	91%

Matriz de confusão:

————— Previsto: 0	————— Previsto: 1

Real 0 ————	286 ———————	47

Real 1 ————	18 ———————	321

Interpretação:
- 321 verdadeiros positivos: clientes da classe positiva identificados corretamente.
- 286 verdadeiros negativos: clientes da classe negativa identificados corretamente.
- 18 falsos negativos: clientes da classe positiva que o modelo não identificou.
- 47 falsos positivos: clientes da classe negativa classificados como positivos.

## 💡 Principais Insights e Implicações

A análise exploratória e a modelagem permitiram identificar alguns padrões relevantes no comportamento dos consumidores.

### *1. Relação entre renda e comportamento de consumo*

Clientes com maior renda apresentaram associações positivas com os gastos em determinadas categorias de produtos.

Por exemplo:
- Renda e gastos com vinhos: correlação de 0,58.
- Renda e gastos com peixes: correlação de 0,58.
- Renda e compras em lojas físicas: correlação de 0,53.
Isso pode ajudar empresas a compreender diferentes perfis de consumo e desenvolver estratégias comerciais mais direcionadas.

### *2. Acessos ao site nem sempre resultam em compras*

A análise do comportamento dos clientes identificou que visitas ao site não necessariamente se convertem em compras.

Esse padrão indica uma oportunidade para investigar possíveis dificuldades na jornada de compra, melhorar a experiência digital e desenvolver campanhas de conversão.

### *3. Existência de diferentes perfis de consumo*

Foram identificadas associações entre determinadas categorias de produtos.

Por exemplo:
- Gastos com frutas e peixes: correlação de 0,59.
- Gastos com vinhos e carnes: correlação de 0,56.
Essas relações sugerem comportamentos de consumo que podem contribuir para estratégias de segmentação e personalização de ofertas.

### *4. O Random Forest apresentou melhor capacidade de identificação dos clientes da classe positiva*

O modelo apresentou Recall superior ao da Regressão Logística, demonstrando maior capacidade de identificar os clientes classificados como compradores online.

Essa característica pode ser relevante para estratégias de marketing nas quais é importante reduzir a quantidade de potenciais compradores que deixam de ser identificados.

### *5. Aplicação estratégica no negócio*

O modelo pode servir como ferramenta de apoio para:
- Segmentação de clientes.
- Campanhas de marketing direcionadas.
- Personalização de ofertas.
- Identificação de oportunidades de conversão.
- Planejamento de estratégias comerciais baseadas no comportamento dos consumidores.

Essas são aplicações potenciais dos resultados, não impactos financeiros efetivamente mensurados no projeto.

## 👩‍💻 Sobre a Autora

Desenvolvido por Marina Napoleão — Cientista de Dados / Analista de Dados. 
### LinkedIn <https://www.linkedin.com/in/marina-napoleao/>
### GitHub <https://github.com/marinanapoleao> 
