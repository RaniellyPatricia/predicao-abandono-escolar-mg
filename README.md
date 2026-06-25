# Predição do Abandono Escolar em Minas Gerais

Projeto desenvolvido para a disciplina de Ciência de Dados do curso de Sistemas de Informação da Universidade do Estado de Minas Gerais — UEMG, Unidade Frutal.

## Problema de pesquisa

É possível classificar os municípios de Minas Gerais quanto ao risco de abandono escolar utilizando indicadores educacionais públicos disponibilizados pelo INEP?

## Objetivo geral

Construir e comparar modelos de Machine Learning capazes de classificar os municípios de Minas Gerais quanto ao nível de abandono escolar.

## Objetivos específicos

- Integrar diferentes bases públicas do INEP.
- Analisar a distribuição do abandono escolar em Minas Gerais.
- Comparar diferentes algoritmos de classificação.
- Identificar as variáveis mais importantes para os modelos.
- Analisar especificamente o município de Frutal.
- Discutir possíveis aplicações dos resultados na gestão educacional.

## Escopo inicial

A primeira versão do projeto utilizará dados referentes ao ano de 2023, considerando os municípios do estado de Minas Gerais.

- Estado: Minas Gerais;
- Ano: 2023;
- Unidade de análise: município;
- Etapa de ensino: Ensino Fundamental — Anos Finais;
- Tipo de tarefa: classificação;
- Variável-alvo: taxa de abandono escolar;
- Estudo de caso: município de Frutal.

O recorte inicial em Minas Gerais e no ano de 2023 foi definido para permitir a validação da integração, limpeza e modelagem dos dados antes da ampliação da série histórica.

## Dados utilizados

Os dados são provenientes de bases públicas oficiais do Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira — INEP.

### Variável-alvo

- Taxa de Abandono Escolar.

### Variáveis explicativas

- Nível Socioeconômico — INSE;
- Taxa de Distorção Idade-Série — TDI;
- Média de Alunos por Turma — MAT;
- Regularidade do Corpo Docente — RCD.

## Unidade de análise

Cada registro do dataset final representará um município de Minas Gerais em determinado ano.

As principais chaves de integração serão:

- `CO_MUNICIPIO`;
- `ANO`.

## Modelos previstos

Serão aplicados, no mínimo, três algoritmos de classificação:

- Regressão Logística;
- Árvore de Decisão;
- Random Forest.

Opcionalmente, poderá ser utilizado o XGBoost.

## Tecnologias utilizadas

- Python;
- Pandas;
- NumPy;
- Matplotlib;
- Scikit-learn;
- Google Colab;
- Git;
- GitHub.

## Estrutura do repositório

- `data/raw/`: bases originais do INEP;
- `data/interim/`: dados intermediários;
- `data/processed/`: dataset final para modelagem;
- `data/dictionaries/`: dicionários e notas técnicas;
- `notebooks/`: análises realizadas no Google Colab;
- `src/`: funções reutilizáveis;
- `docs/`: documentação metodológica;
- `reports/`: gráficos, tabelas, relatório e apresentação;
- `models/`: modelos treinados;
- `tests/`: testes e validações.

## Etapas do projeto

1. Definição do problema;
2. Coleta e descrição dos dados;
3. Limpeza e tratamento;
4. Análise exploratória;
5. Integração das bases;
6. Engenharia de atributos;
7. Criação da variável-alvo;
8. Treinamento dos modelos;
9. Avaliação e comparação;
10. Interpretação dos resultados;
11. Análise específica de Frutal;
12. Elaboração do relatório e apresentação.

## Situação do projeto

Em desenvolvimento.
