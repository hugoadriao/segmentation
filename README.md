# Análise de Cluster com PCA - Projeto Acadêmico

## Descrição do Projeto

Este projeto foi desenvolvido como parte da disciplina de **Visualização e Relatório de Segmentos** do Instituto Infnet, tendo como objetivo principal a aplicação de técnicas de análise multivariada para segmentação de dados utilizando **Análise de Componentes Principais (PCA)** e **algoritmo K-Médias**.

## Base de Dados

O estudo utiliza o dataset **Wine Recognition Data** disponível no UCI Machine Learning Repository, que contém:
- **178 amostras** de vinhos italianos
- **13 variáveis químicas** quantitativas
- **3 classes** naturais de vinho (cultivares diferentes)

A escolha desta base de dados foi motivada por suas características ideais para aprendizado:
- Tamanho adequado para análise exploratória completa
- Presença de variáveis correlacionadas (ideal para PCA)
- Grupos naturais conhecidos para validação dos resultados

## Metodologia

### 1. Análise Exploratória
- **Correlograma**: Identificação de correlações entre variáveis químicas
- Descoberta de correlações fortes (>0.7) entre:
  - Total_phenols ↔ Flavanoids (r = 0.86)
  - OD280_OD315 ↔ Flavanoids (r = 0.79)
  - OD280_OD315 ↔ Total_phenols (r = 0.70)

### 2. Análise de Componentes Principais (PCA)
- **Normalização** dos dados usando função `scale()`
- **Redução dimensional**: 13 variáveis → 4 componentes principais
- **Variância explicada**: 73.60% com apenas 4 componentes
- **Interpretação química** dos componentes:
  - PC1 (36.20%): Componente fenólico
  - PC2 (19.23%): Intensidade e álcool
  - PC3 (11.61%): Minerais (cinzas)
  - PC4 (6.56%): Acidez málica e matiz

### 3. Clustering K-Médias
- **Aplicação** nas 4 componentes principais selecionadas
- **Determinação do k ótimo** usando Índice de Silhueta (k = 2 a 8)
- **Resultado**: k = 3 clusters (Silhueta = 0.274)
- **Validação**: Alta correspondência com as 3 classes originais

### 4. Análise Comparativa
Comparação entre duas abordagens:
- **Com pré-processamento**: PCA + normalização + Índice de Silhueta
- **Sem pré-processamento**: Dados originais + k arbitrário

## Principais Resultados

### Eficácia do PCA
- **Redução de 69%** na dimensionalidade mantendo 73.60% da informação
- **Eliminação de redundâncias** identificadas no correlograma
- **Agrupamento natural** de características químicas relacionadas

### Qualidade do Clustering
- **Pureza elevada**: Boa correspondência com classes reais
- **Separação clara** no espaço das componentes principais
- **Distribuição balanceada** entre os 3 clusters identificados

### Validação Científica
- **Coerência com o domínio**: 3 clusters = 3 cultivares de vinho
- **Interpretabilidade química**: Componentes relacionados a grupos de compostos
- **Robustez metodológica**: Critério objetivo para escolha de parâmetros

## Ferramentas e Tecnologias

- **Linguagem**: R
- **IDE**: Visual Studio Code com extensões R
- **Pacotes principais**:
  - `prcomp()` para PCA
  - `corrplot` para visualização de correlações
  - `cluster` para análise de silhueta
  - `ggplot2` para visualizações
  - `rmarkdown` para relatório reproduzível

## Visualizações

O projeto inclui diversas visualizações científicas:
- **Correlograma** das variáveis químicas
- **Scree Plot** para seleção de componentes
- **Gráfico de Silhueta** para determinação do k ótimo
- **Scatter plots** dos clusters nas componentes principais
- **Comparações visuais** entre métodos

## Dashboard Interativo

Complementando a análise, foi desenvolvido um dashboard interativo no **Tableau Public** para exploração visual dos segmentos identificados no espaço PC1 × PC2.

## Estrutura do Projeto

```
├── cluster.Rmd          # Análise principal em R Markdown
├── cluster.pdf          # Relatório final gerado
├── data/
│   └── wine.data        # Dataset original
├── assets/              # Imagens e evidências
│   ├── vscode_r.png
│   ├── rmarkdown_version.png
│   ├── factoextra_factoMineR_version.png
│   └── tableau_public.png
└── README.md           # Este arquivo
```

## Conclusões Acadêmicas

Este projeto demonstra a **eficácia da combinação PCA + K-Médias** para análise de segmentação, evidenciando como o pré-processamento adequado e a escolha criteriosa de parâmetros resultam em:

1. **Maior interpretabilidade** dos resultados
2. **Redução significativa** da complexidade dimensional
3. **Validação objetiva** através de métricas de qualidade
4. **Correspondência com a realidade** do domínio estudado

A abordagem metodológica rigorosa, com justificativas estatísticas para cada decisão, exemplifica as melhores práticas em análise de dados multivariados e mineração de dados.

---

**Autor**: Hugo Victor dos Santos Silva  
**Instituição**: Instituto Infnet  
**Disciplina**: Visualização e Relatório de Segmentos