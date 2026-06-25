# Identificação do problema

## Contextualização

O abandono escolar representa um importante desafio para a educação, pois pode comprometer a formação dos estudantes e ampliar desigualdades sociais e econômicas.

A identificação antecipada de municípios com maior risco de abandono pode auxiliar gestores públicos na elaboração de estratégias de prevenção, acompanhamento e direcionamento de recursos educacionais.

Neste projeto, serão utilizados indicadores educacionais públicos disponibilizados pelo Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira — INEP.

## Problema de pesquisa

É possível classificar os municípios de Minas Gerais quanto ao risco de abandono escolar utilizando indicadores educacionais públicos disponibilizados pelo INEP?

## Objetivo geral

Construir e comparar modelos de Machine Learning capazes de classificar os municípios de Minas Gerais de acordo com o nível de abandono escolar.

## Objetivos específicos

- Coletar e organizar bases educacionais públicas do INEP;
- integrar diferentes indicadores utilizando o código do município e o ano;
- analisar a distribuição da taxa de abandono escolar em Minas Gerais;
- criar classes de risco de abandono escolar;
- treinar e comparar diferentes algoritmos de classificação;
- identificar os indicadores com maior associação com o abandono escolar;
- analisar detalhadamente o município de Frutal;
- interpretar os resultados considerando sua possível aplicação na gestão educacional.

## Tipo de tarefa

O projeto será tratado como uma tarefa de classificação.

A taxa de abandono escolar, originalmente representada por um valor numérico, será transformada em categorias de risco, como:

- baixo risco;
- médio risco;
- alto risco.

Os critérios utilizados para criar essas classes serão definidos após a análise exploratória da distribuição da taxa de abandono.

## Unidade de análise

A unidade de análise será o município.

Cada linha do dataset final deverá representar um município de Minas Gerais em determinado ano.

As principais chaves utilizadas na integração das bases serão:

- `CO_MUNICIPIO`;
- `ANO`.

## Recorte inicial

A primeira versão do projeto utilizará:

- dados de Minas Gerais;
- ano de 2023;
- Ensino Fundamental — Anos Finais;
- município de Frutal como estudo de caso.

Esse recorte será utilizado para validar a limpeza, a integração e a modelagem antes da possível inclusão de outros anos.

## Aplicação esperada

O modelo poderá auxiliar na identificação de municípios que apresentam maior risco de abandono escolar.

Os resultados não devem substituir a análise de especialistas ou gestores educacionais, mas podem funcionar como instrumento de apoio para:

- priorização de municípios;
- investigação de fatores associados;
- planejamento de políticas públicas;
- acompanhamento de indicadores educacionais;
- direcionamento de ações preventivas.
