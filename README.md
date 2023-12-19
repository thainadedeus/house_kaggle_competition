# House kaggle

O desafio House Kaggle realiza a previsão de preços de imóveis, indo além das expectativas convencionais de um comprador ao descrever a casa dos sonhos. O conjunto de dados, composto por 79 variáveis explicativas que descrevem praticamente todos os aspectos de residências em Ames, Iowa, prevê o preço final de cada casa. Diferentemente das preferências comuns, como o número de quartos ou a presença de uma cerca branca, este conjunto de dados contém outros elementos que podem influenciar no preço da casa, como a altura do teto do porão ou a proximidade de uma ferrovia leste-oeste. A avaliação dos modelos submetidos baseia-se no Root-Mean-Squared-Error (RMSE), calculado entre o logaritmo do valor previsto e o logaritmo do preço observado de vendas. Essa abordagem logarítmica equaliza os impactos de erros na previsão de casas caras e baratas.

## Descrição das bases

train.csv - conjunto de treinamento

test.csv - conjunto de teste

data_description.txt - descrição completa de cada coluna, originalmente preparada por Dean De Cock, mas levemente editada para corresponder aos nomes das colunas usados aqui

sample_submission.csv - uma submissão de referência a partir de uma regressão linear sobre o ano e mês da venda, área do lote em pés quadrados e número de quartos

Campos das bases de dados:

SalePrice - preço de venda da propriedade em dólares. Esta é a variável alvo que você está tentando prever.

MSSubClass: Classe da construção

MSZoning: Classificação geral de zoneamento

LotFrontage: Pés lineares de rua conectados à propriedade

LotArea: Tamanho do lote em pés quadrados

Street: Tipo de acesso à estrada

Alley: Tipo de acesso à viela

LotShape: Formato geral da propriedade

LandContour: Planura da propriedade

Utilities: Tipo de utilidades disponíveis

LotConfig: Configuração do lote

LandSlope: Inclinação da propriedade

Neighborhood: Localizações físicas dentro dos limites da cidade de Ames

Condition1: Proximidade da estrada principal ou ferrovia

Condition2: Proximidade da estrada principal ou ferrovia (se houver uma segunda)

BldgType: Tipo de moradia

HouseStyle: Estilo da moradia

OverallQual: Qualidade geral de material e acabamento

OverallCond: Classificação geral de condição

YearBuilt: Data original de construção

YearRemodAdd: Data de remodelação

RoofStyle: Tipo de telhado

RoofMatl: Material do telhado

Exterior1st: Revestimento externo da casa

Exterior2nd: Segundo revestimento externo da casa (se houver mais de um material)

MasVnrType: Tipo de revestimento de alvenaria

MasVnrArea: Área de revestimento de alvenaria em pés quadrados

ExterQual: Qualidade do material externo

ExterCond: Condição atual do material externo

Foundation: Tipo de fundação

BsmtQual: Altura do porão

BsmtCond: Condição geral do porão

BsmtExposure: Paredes do porão ao nível do solo ou do jardim

BsmtFinType1: Qualidade da área acabada do porão

BsmtFinSF1: Pés quadrados acabados do Tipo 1

BsmtFinType2: Qualidade da segunda área acabada (se presente)

BsmtFinSF2: Pés quadrados acabados do Tipo 2

BsmtUnfSF: Pés quadrados não acabados da área do porão

TotalBsmtSF: Pés quadrados totais da área do porão

Heating: Tipo de aquecimento

HeatingQC: Qualidade e condição do aquecimento

CentralAir: Ar-condicionado central

Electrical: Sistema elétrico

1stFlrSF: Pés quadrados do primeiro andar

2ndFlrSF: Pés quadrados do segundo andar

LowQualFinSF: Pés quadrados acabados de baixa qualidade (todos os andares)

GrLivArea: Pés quadrados da área de vida acima do solo (térreo)

BsmtFullBath: Banheiros completos no porão

BsmtHalfBath: Banheiros parciais no porão

FullBath: Banheiros completos acima do solo

HalfBath: Meio banheiros acima do solo

Bedroom: Número de quartos acima do nível do porão

Kitchen: Número de cozinhas

KitchenQual: Qualidade da cozinha

TotRmsAbvGrd: Total de quartos acima do solo (não inclui banheiros)

Functional: Classificação de funcionalidade da casa

Fireplaces: Número de lareiras

FireplaceQu: Qualidade da lareira

GarageType: Localização da garagem

GarageYrBlt: Ano de construção da garagem

GarageFinish: Acabamento interno da garagem

GarageCars: Tamanho da garagem em capacidade de carros

GarageArea: Tamanho da garagem em pés quadrados

GarageQual: Qualidade da garagem

GarageCond: Condição da garagem

PavedDrive: Driveway pavimentado

WoodDeckSF: Área de deck de madeira em pés quadrados

OpenPorchSF: Área de varanda aberta em pés quadrados

EnclosedPorch: Área de varanda fechada em pés quadrados

3SsnPorch: Área da varanda de três estações em pés quadrados

ScreenPorch: Área da varanda de tela em pés quadrados

PoolArea: Área da piscina em pés quadrados

PoolQC: Qualidade da piscina

Fence: Qualidade da cerca

MiscFeature: Característica diversa não coberta em outras categorias

MiscVal: Valor da característica diversa em dólares

MoSold: Mês de venda

YrSold: Ano de venda

SaleType: Tipo de venda

SaleCondition: Condição de venda

## Estrutura de pastas

A fim de desenvolver o desafio, a estrutura de pastas correspondente e que comporta as necessidades do desenvolvedor:

1. data: Esta pasta contém os conjuntos de dados necessários para o desafio. Os arquivos houses_test_raw.csv e houses_train_raw.csv são os dados brutos de teste e treinamento.
2. houses_trainer_package: Essa pasta possue scripts e arquivos relacionados ao treinamento do modelo. Alguns arquivos incluídos são:
    - __init__.py: Um arquivo Python usado para inicializar o pacote.
    - pipeline.py: Etapas de pré-processamento e modelagem.
    - preprocessors.py: Transformações específicas dos dados.
    - trainer.py: Usado para treinar o modelo.
3. .ipynb_checkpoints: Essa pasta é gerada automaticamente e armazena os estados salvos dos notebooks Jupyter.
4. tests: Contém scripts de teste e arquivos pickle associados à avaliação do modelo e validação dos resultados.
5. .gitignore: Um arquivo usado para especificar quais arquivos ou tipos de arquivo devem ser ignorados pelo Git.
6. autotest.sh: Um script shell que é usado para automatizar testes.

## Arquivos de execução

O arquivo preprocessors contém funções que desempenham um papel essencial no pré-processamento de dados. As funções definem transformações específicas para variáveis ordinais, numéricas e nominais, preparando os dados para serem utilizados no treinamento do modelo. Utiliza-se o *OrdinalEncoder* para transformar as variáveis ordinais em números, respeitando a ordem especificada. O pipeline resultante inclui imputação de valores faltantes, codificação ordinal e a aplicação da escala Min-Max. Por sua vez, a função *create_preproc_numerical* concentra-se em variáveis numéricas, empregando um pipeline que realiza imputação de valores faltantes usando KNNImputer e aplica a escala Min-Max.

A função *create_preproc_nominal* lida com variáveis nominais, empregando um pipeline que realiza imputação de valores faltantes usando a estratégia "most_frequent" e aplica a codificação one-hot com OneHotEncoder. Esses pré-processadores são posteriormente integrados ao pipeline principal, conforme definido no arquivo pipeline.

O arquivo trainer apresenta uma classe chamada Trainer responsável por treinar e avaliar um modelo de regressão. Além da utilização de funções de pré-processamento, destaca-se a realização da validação cruzada para avaliar o desempenho do modelo, calculando a raiz quadrada do erro médio quadrático (RMSLE) como métrica de avaliação. O método imprime a média e o desvio padrão do RMSLE para as dobras de validação cruzada.A instância é criada, os dados brutos são carregados, o pipeline é construído aplicando o pré-processamento e a modelagem, e, por fim, é realizada a validação cruzada para avaliar o desempenho do modelo.

Analisa-se o arquivo pipeline, pois, o pré-processamento e modelagem de dados em um contexto de aprendizado de máquina está sendo realizado.  A função *create_preproc* desempenha um papel crucial na definição de etapas de pré-processamento, utilizando pré-processadores para variáveis ordinais, numéricas e nominais. A função *create_mode*l é responsável pela criação de modelos de regressão, incluindo Gradient Boosting Regressor, Ridge Regression, Support Vector Machine Regressor e AdaBoost Regressor com Decision Tree como estimador base. Por fim, a função o pré-processamento é unificado ao modelo em um único pipeline usando a função *make_pipeline*. Esse pipeline completo facilita o treinamento e a avaliação de modelos em conjuntos de dados específicos, fornecendo uma abordagem organizada e eficiente para lidar com tarefas de aprendizado de máquina.

Já na pasta de tests, os testes fornecidos na classe TestSubmissionBaseline são destinados a avaliar diferentes aspectos da submissão de previsões de preços de casas no contexto de um desafio Kaggle, utilizando a biblioteca nbresult para comparar os resultados obtidos com os resultados esperados, armazenados em arquivos pickle.

- test_score_baseline: Verifica se a pontuação do modelo, armazenada no arquivo pickle, é menor que 0.23. Este teste estabelece um critério mínimo de desempenho para o modelo.
- test_submission_shape: Avalia se o formato da submissão, armazenado no arquivo pickle, é igual a (1459, 2). Este teste verifica se a submissão tem o número correto de linhas e colunas.
- test_submission_columns: Verifica se as colunas da submissão, armazenadas no arquivo pickle, são ['Id', 'SalePrice']. Este teste assegura que as colunas na submissão estão corretas.
- test_submission_dtypes: Avalia se os tipos de dados das colunas na submissão, armazenados no arquivo pickle, são iguais a "[dtype('int64'), dtype('float64')]". Este teste confirma se os tipos de dados esperados nas colunas da submissão estão corretos.

## Modelos

1. **Ridge Regression:**
    - *Descrição:* A Ridge Regression é uma técnica de regularização que aborda a multicolinearidade em conjuntos de dados com muitas variáveis, através da adição de um termo de penalidade.
    - *Soluções de Ajuste:* Alfa (parâmetro de regularização) otimizado usando GridSearchCV: 2.0.
2. **K-Nearest Neighbors (KNN):**
    - *Descrição:* O KNN é um algoritmo de aprendizado supervisionado que faz previsões com base na média dos rótulos dos k vizinhos mais próximos no espaço de recursos.
    - *Soluções de Ajuste:* Número de vizinhos (n_neighbors) otimizado usando GridSearchCV: 6.
3. **Support Vector Machine - Radial Basis Function (SVM-RBF):**
    - *Descrição:* O SVM-RBF é uma máquina de vetores de suporte que utiliza uma função de base radial como função do kernel.
    - *Soluções de Ajuste:* Parâmetros C e epsilon otimizados usando GridSearchCV: C=1, epsilon=0.05.
4. **Decision Tree:**
    - *Descrição:* Uma árvore de decisão divide os dados em partições com base nas características dos dados.
    - *Soluções de Ajuste:* Profundidade máxima: 50, número mínimo de amostras em folhas: 20.
5. **Random Forest:**
    - *Descrição:* Uma floresta aleatória é uma coleção de árvores de decisão treinadas em amostras aleatórias dos dados.
    - *Soluções de Ajuste:* Profundidade máxima: 50, número mínimo de amostras em folhas: 20.

**Modelos de Ensemble:**

1. **AdaBoost Regressor:**
    - *Descrição:* O AdaBoost é um algoritmo de boosting que combina vários modelos de aprendizado fracos.
    - *Soluções de Ajuste:* Decision Tree como modelo base.
2. **Gradient Boosting Regressor:**
    - *Descrição:* O Gradient Boosting constrói árvores de decisão sequencialmente, corrigindo os erros dos modelos anteriores.
    - *Soluções de Ajuste:* 100 estimadores.
3. **Voting Regressor:**
    - *Descrição:* O Voting Regressor combina as previsões de vários modelos de regressão.
    - *Soluções de Ajuste:* Ensemble de Gradient Boosting, AdaBoost, Ridge e SVM-RBF.
4. **Stacking Regressor:**
    - *Descrição:* O Stacking Regressor empilha vários modelos de regressão.
    - *Soluções de Ajuste:* Ensemble semelhante ao Voting Regressor.
5. **XGBoost (Extreme Gradient Boosting):**
    - *Descrição:* XGBoost é um algoritmo de gradient boosting eficiente e escalável.
    - *Soluções de Ajuste:* Max_depth=10, n_estimators=300, learning_rate=0.1.

**Comparação dos Resultados:**

- A métrica de avaliação foi o RMSE.
- Modelos mais complexos (Gradient Boosting, Voting Regressor, Stacking Regressor) apresentaram RMSE mais baixo.
- XGBoost demonstrou desempenho robusto.
- Modelos como Ridge, KNN e SVM-RBF tiveram desempenho competitivo.
- A escolha do modelo final depende de vários fatores, incluindo a natureza dos dados e recursos computacionais.

**Possíveis Modificações:**

1. **Feature Engineering:**
    - *Proposta:* Explorar técnicas avançadas de engenharia de características para criar novos atributos relevantes.
2. **Ajuste de Hiperparâmetros Adicional:**
    - *Proposta:* Realizar ajuste de hiperparâmetros mais detalhado, explorando uma gama mais ampla de valores.
3. **Tratamento de Outliers:**
    - *Proposta:* Investigar e tratar outliers, especialmente em modelos sensíveis como SVM.
4. **Avaliação de Sensibilidade:**
    - *Proposta:* Realizar análises de sensibilidade para identificar parâmetros críticos que necessitam de ajustes mais precisos.
5. **Validação Cruzada Estratificada:**
    - *Proposta:* Implementar validação cruzada estratificada, especialmente se houver desequilíbrio nas classes do conjunto de dados. Isso pode melhorar a representatividade das amostras em cada fold.
6. **Transformação de Variáveis:**
    - *Proposta:* Avaliar a necessidade de transformações em variáveis, como normalização, padronização ou aplicação de log, para garantir que os modelos se beneficiem de distribuições mais adequadas.