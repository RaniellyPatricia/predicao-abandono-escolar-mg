# Registro de decisões do projeto

Este documento registra as principais decisões metodológicas tomadas durante o desenvolvimento do projeto.

## 1. Recorte geográfico

Foi definido que a primeira versão do projeto utilizará apenas dados dos municípios de Minas Gerais.

### Justificativa

Esse recorte reduz a complexidade inicial da integração das bases e permite uma análise mais detalhada do contexto estadual.

Além disso, o município de Frutal será utilizado como estudo de caso, atendendo ao foco regional do trabalho.

## 2. Recorte temporal

Inicialmente serão utilizados dados referentes ao ano de 2023.

### Justificativa

A utilização de um único ano permite validar:

- a estrutura das bases;
- a padronização das variáveis;
- a integração por município;
- a criação do dataset final;
- o funcionamento dos modelos.

Após essa validação, poderão ser incorporados dados de outros anos, como 2021, 2022 e 2024.

## 3. Unidade de análise

A unidade de análise será o município.

Cada linha do dataset final representará um município de Minas Gerais em determinado ano.

### Chaves de integração

- `CO_MUNICIPIO`;
- `ANO`.

## 4. Etapa de ensino

O recorte inicial será o Ensino Fundamental — Anos Finais.

### Justificativa

A escolha de uma única etapa evita misturar realidades educacionais diferentes, como Anos Iniciais, Anos Finais e Ensino Médio.

Esse recorte também facilita a comparação entre os indicadores.

## 5. Tipo de problema

O projeto será tratado como uma tarefa de classificação.

A taxa de abandono, originalmente numérica, será transformada em categorias de risco.

### Classes previstas

- baixo risco;
- médio risco;
- alto risco.

Os critérios de separação das classes serão definidos após a análise exploratória da distribuição da taxa de abandono.

## 6. Variável-alvo

A variável-alvo será a Taxa de Abandono Escolar.

Ela será obtida na base de Taxas de Rendimento Escolar do INEP.

## 7. Variáveis explicativas

Inicialmente serão utilizadas:

- Nível Socioeconômico — INSE;
- Taxa de Distorção Idade-Série — TDI;
- Média de Alunos por Turma — MAT;
- Regularidade do Corpo Docente — RCD.

Outros indicadores poderão ser adicionados caso haja compatibilidade entre as bases.

## 8. Modelos previstos

Serão comparados, no mínimo, três algoritmos:

- Regressão Logística;
- Árvore de Decisão;
- Random Forest.

O XGBoost poderá ser incluído como modelo opcional.

## 9. Estratégia de desenvolvimento

O projeto será desenvolvido em etapas:

1. organização das bases;
2. verificação dos dicionários;
3. limpeza individual de cada dataset;
4. agregação por município;
5. integração das bases;
6. análise exploratória;
7. criação da variável-alvo;
8. treinamento dos modelos;
9. avaliação;
10. interpretação dos resultados.

## 10. Decisões pendentes

Ainda precisam ser definidas:

- os códigos oficiais de rede e localização;
- as colunas correspondentes aos Anos Finais;
- a estratégia de agregação de cada base;
- o tratamento de dados ausentes;
- os limites das classes de abandono;
- a estratégia de divisão entre treino e teste;
- as métricas principais de avaliação;
- a inclusão ou não de outros anos.
