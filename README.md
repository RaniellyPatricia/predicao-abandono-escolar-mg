# Predição do Abandono Escolar nos Municípios de Minas Gerais

Projeto final da disciplina de **Ciência de Dados** do curso de **Sistemas de Informação — UEMG Frutal**.

Este projeto tem como objetivo aplicar um fluxo completo de Ciência de Dados para analisar e prever o nível de risco de abandono escolar nos municípios de Minas Gerais, utilizando dados públicos oficiais do INEP.

---

## Problema de pesquisa

É possível prever o nível de abandono escolar dos municípios de Minas Gerais utilizando indicadores educacionais públicos disponibilizados pelo INEP?

Além da predição, o projeto busca identificar quais fatores apresentam maior associação com o abandono escolar, com destaque para a análise do município de Frutal.

---

## Objetivo do projeto

Construir e avaliar modelos de Machine Learning capazes de classificar municípios mineiros em diferentes níveis de risco de abandono escolar nos Anos Finais do Ensino Fundamental.

A tarefa desenvolvida é de **classificação multiclasse**, com três categorias:

- Baixo risco
- Médio risco
- Alto risco

---

## Fonte dos dados

Foram utilizadas bases públicas oficiais do **Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira — INEP**.

Bases utilizadas:

| Base | Uso no projeto |
|---|---|
| Taxas de Rendimento Escolar | Base-alvo para criação da taxa de abandono |
| Indicador de Nível Socioeconômico — INSE | Variável explicativa |
| Taxa de Distorção Idade-Série | Variável explicativa |
| Média de Alunos por Turma | Variável explicativa |
| Regularidade do Corpo Docente | Variável explicativa |

---

## Recorte da análise

- Ano: 2023
- Estado: Minas Gerais
- Unidade de análise: município
- Etapa: Anos Finais do Ensino Fundamental, quando disponível
- Rede: pública
- Estudo de caso: município de Frutal
- Recorte regional: Região Geográfica Intermediária de Uberaba

---

## Dataset final

Após o tratamento e a integração das bases, o dataset final possui:

- 853 municípios de Minas Gerais
- 13 colunas na versão com classes
- 0 valores ausentes nas variáveis selecionadas
- Integração por `CO_MUNICIPIO` e `ANO`

A variável numérica `TAXA_ABANDONO_ANOS_FINAIS` foi transformada na variável categórica `CLASSE_ABANDONO`.

As classes foram criadas com base nos quartis da taxa de abandono:

| Classe | Regra |
|---|---|
| Baixo risco | Taxa de abandono até 0,4% |
| Médio risco | Taxa de abandono maior que 0,4% e até 2,1% |
| Alto risco | Taxa de abandono maior que 2,1% |

---

## Variáveis utilizadas na modelagem

Variáveis explicativas:

- `QTD_ALUNOS_INSE`
- `MEDIA_INSE`
- `TDI_ANOS_FINAIS`
- `MEDIA_ALUNOS_TURMA_ANOS_FINAIS`
- `PERC_ESCOLAS_BAIXA_REGULARIDADE_DOCENTE`
- `PERC_ESCOLAS_MEDIA_BAIXA_REGULARIDADE_DOCENTE`
- `PERC_ESCOLAS_MEDIA_ALTA_REGULARIDADE_DOCENTE`
- `PERC_ESCOLAS_ALTA_REGULARIDADE_DOCENTE`

Variável-alvo:

- `CLASSE_ABANDONO`

A variável `TAXA_ABANDONO_ANOS_FINAIS` não foi utilizada como variável explicativa, pois a classe de abandono foi criada a partir dela. Utilizá-la no treinamento causaria vazamento de informação.

---

## Modelos avaliados

Foram comparados os seguintes modelos de classificação:

- Regressão Logística
- Árvore de Decisão
- Random Forest
- Regressão Logística Balanceada
- Árvore de Decisão Balanceada
- Random Forest Balanceado

Também foi criado um modelo base com `DummyClassifier`, que sempre previa a classe mais frequente, para servir como referência mínima de comparação.

---

## Resultados principais

O melhor modelo foi o **Random Forest Balanceado**.

| Modelo | Acurácia | Precisão macro | Recall macro | F1-score macro |
|---|---:|---:|---:|---:|
| Random Forest Balanceado | 0,523 | 0,531 | 0,555 | 0,521 |

O modelo apresentou desempenho moderado, mas foi o mais equilibrado entre as classes e teve melhor capacidade de identificar municípios de alto risco.

Na matriz de confusão, o Random Forest Balanceado identificou corretamente 47 dos 64 municípios classificados como alto risco no conjunto de teste.

---

## Importância das variáveis

A variável mais importante para o modelo foi:

- `TDI_ANOS_FINAIS`

Isso indica que a **Taxa de Distorção Idade-Série** foi o principal indicador associado à classificação do risco de abandono escolar.

Ranking das principais variáveis:

| Variável | Importância |
|---|---:|
| TDI_ANOS_FINAIS | 0,2772 |
| QTD_ALUNOS_INSE | 0,1621 |
| MEDIA_ALUNOS_TURMA_ANOS_FINAIS | 0,1607 |
| MEDIA_INSE | 0,1194 |

---

## Estudo de caso: Frutal

Frutal apresentou:

- Taxa de abandono: 1,5%
- Classe real: Médio risco
- Classe prevista pelo modelo: Alto risco

Probabilidades atribuídas pelo modelo:

| Classe | Probabilidade |
|---|---:|
| Alto risco | 43,01% |
| Médio risco | 34,81% |
| Baixo risco | 22,18% |

A predição de alto risco foi interpretada como um alerta complementar, pois Frutal possui indicadores que merecem acompanhamento, especialmente:

- TDI de 13,4%
- Média de alunos por turma de 26,2

---

## Estrutura do repositório

```text
predicao-abandono-escolar-mg/
├── data/
│   ├── raw/
│   ├── interim/
│   ├── processed/
│   └── dictionaries/
├── docs/
├── notebooks/
├── reports/
│   ├── figures/
│   ├── final/
│   └── slides/
├── src/
├── models/
├── tests/
├── README.md
├── requirements.txt
├── .gitignore
└── LICENSE
```

---

## Notebooks

| Notebook | Descrição |
|---|---|
| `01_coleta_e_descricao.ipynb` | Leitura, inspeção e tratamento inicial das bases |
| `02_integracao_das_bases.ipynb` | Integração das bases tratadas |
| `03_analise_exploratoria.ipynb` | Análise exploratória, Frutal, região e criação das classes |
| `04_modelagem.ipynb` | Treinamento, avaliação e comparação dos modelos |

---

## Relatórios e apresentação

A pasta `reports/` reúne os materiais finais do projeto:

| Pasta | Conteúdo |
|---|---|
| `reports/final/` | Relatório final em PDF e versão editável |
| `reports/figures/` | Gráficos utilizados no relatório e apresentação |
| `reports/slides/` | Slides da apresentação |

---

## Tecnologias utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Google Colab
- GitHub

---

## Situação do projeto

Projeto finalizado para entrega acadêmica.

Foram concluídas as etapas de:

- coleta dos dados;
- limpeza e tratamento das bases;
- integração dos dados;
- análise exploratória;
- criação da variável-alvo;
- modelagem preditiva;
- avaliação dos modelos;
- interpretação dos resultados;
- estudo de caso de Frutal;
- relatório final.

---

## Limitações

O projeto possui algumas limitações importantes:

- análise restrita ao ano de 2023;
- unidade de análise municipal, sem granularidade por escola ou estudante;
- ausência de variáveis externas, como renda, transporte escolar, ruralidade e infraestrutura;
- desempenho moderado dos modelos;
- resultados interpretados como apoio exploratório e preditivo, não como explicação causal.

---

## Possíveis melhorias futuras

- Incorporar dados de outros anos;
- Criar uma base histórica com 2020 a 2024;
- Adicionar variáveis socioeconômicas do IBGE;
- Incluir indicadores de infraestrutura escolar;
- Testar outros modelos, como XGBoost;
- Aplicar validação temporal;
- Construir dashboard em Power BI ou Looker Studio;
- Salvar modelos treinados em `models/`;
- Criar testes automatizados em `tests/`.

---

## Pasta `tests/`

A pasta `tests/` foi mantida como espaço reservado para versões futuras do projeto.

Em uma evolução do repositório, essa pasta poderá conter testes automatizados para validar:

- leitura dos arquivos;
- existência das colunas esperadas;
- ausência de valores ausentes;
- consistência do número de municípios;
- padronização dos nomes das variáveis;
- funcionamento das funções de tratamento;
- funcionamento dos modelos de classificação.

---

## Autoria

Discente: **Ranielly Patrícia Resende de Almeida**  
Curso: **Sistemas de Informação**  
Disciplina: **Ciência de Dados**  
Docente: **Ivan José dos Reis Filho**  
Instituição: **Universidade do Estado de Minas Gerais — UEMG Frutal**
