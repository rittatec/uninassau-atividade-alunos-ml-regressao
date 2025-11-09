# 🤖 Etapa 3: Modelos de Machine Learning

**Prazo de Entrega:** [Data será informada pelo professor]
**Peso:** 25% da nota do projeto (2.5 pontos)
**Entregáveis:**
- `notebooks/03_Modelagem.ipynb`
- Apresentação de 15 minutos

---

## 🎯 Objetivos da Etapa

Ao final desta etapa, você deve:

1. **Treinar múltiplos modelos** - Testar pelo menos 5 algoritmos diferentes
2. **Avaliar desempenho** - Comparar modelos usando métricas apropriadas
3. **Validar corretamente** - Usar validação cruzada e conjunto de validação
4. **Selecionar melhor modelo** - Escolher modelo com melhor desempenho

---

## 📋 O Que Você Vai Entregar

### 1. Notebook Principal
**`notebooks/03_Modelagem.ipynb`**

Seções obrigatórias:
1. Importação e Carregamento dos Dados Processados
2. Definição de Métricas de Avaliação
3. Modelo Baseline (Regressão Linear)
4. Modelos Avançados (pelo menos 5 algoritmos)
5. Validação Cruzada
6. Comparação de Modelos
7. Análise de Erros
8. Conclusões e Seleção do Melhor Modelo

### 2. Apresentação (15 minutos) 🎤

**O que apresentar:**
- Modelos testados e por quê escolheu cada um
- Métricas utilizadas e justificativa
- Comparação de desempenho (gráficos!)
- Melhor modelo e suas características
- Análise de erros do melhor modelo
- Próximos passos (Etapa 4)

**Formato:**
- 8-10 slides
- Todos os membros do grupo devem participar
- Inclua gráficos comparativos (barras, boxplots)
- Demonstre 1-2 exemplos de predição

**Critérios de avaliação da apresentação:**
- Clareza técnica (30%)
- Análise comparativa (30%)
- Visualizações de resultados (20%)
- Participação de todos (20%)

---

## 🔍 Modelos Obrigatórios

### Modelo Baseline
**Regressão Linear Simples**

Pesquise como implementar regressão linear usando scikit-learn. Este será seu modelo de referência para comparar os demais.

**Recursos:**
- Documentação: `sklearn.linear_model.LinearRegression`
- Tutorial de regressão linear

### Modelos Avançados (escolha pelo menos 5)

**Obrigatório testar:**
1. **Ridge Regression** ou **Lasso Regression**
2. **Decision Tree Regressor**
3. **Random Forest Regressor**
4. **Gradient Boosting** (XGBoost, LightGBM, ou CatBoost)
5. **Support Vector Regressor** ou **KNN Regressor** ou **Elastic Net**

**Pesquise:**
- Como instalar e importar cada biblioteca
- Diferenças entre cada modelo
- Hiperparâmetros padrão de cada um
- Como criar um dicionário de modelos para treinar em loop

---

## 📊 Métricas Obrigatórias

Para **regressão**, calcule:

1. **MAE** (Mean Absolute Error)
2. **MSE** (Mean Squared Error)
3. **RMSE** (Root Mean Squared Error)
4. **R²** (R-squared)
5. **MAPE** (Mean Absolute Percentage Error) - opcional

**Pesquise:**
- Documentação do `sklearn.metrics`
- Como calcular cada métrica
- Como interpretar cada uma
- Qual métrica é mais importante para regressão

---

## 🔬 Análises Obrigatórias

### 1. Treinamento de Todos os Modelos

**Objetivo:** Treinar todos os modelos e armazenar resultados.

**Pesquise:**
- Como fazer loop em um dicionário de modelos
- Como treinar modelos (.fit)
- Como fazer predições (.predict)
- Como armazenar resultados em dicionário ou DataFrame

### 2. Validação Cruzada

**Obrigatório:** Usar validação cruzada com 5 folds.

**Pesquise:**
- Documentação do `sklearn.model_selection.cross_val_score`
- O que é k-fold cross-validation
- Como escolher o scoring apropriado
- Como interpretar média e desvio padrão dos scores

### 3. Comparação Visual

**Crie gráficos:**

#### Gráfico de Barras - Comparação de MAE
Pesquise como criar gráfico de barras horizontal comparando MAE de todos os modelos.

**Recursos:**
- `matplotlib.pyplot.barh`
- Como ordenar modelos por performance

#### Scatter Plot - Predito vs Real
Pesquise como criar scatter plot mostrando valores preditos vs valores reais, com linha diagonal de referência (predição perfeita).

**Recursos:**
- `matplotlib.pyplot.scatter`
- Como adicionar linha de referência diagonal

### 4. Análise de Erros

**Obrigatório:** Calcular resíduos e criar gráficos de diagnóstico.

**Pesquise:**
- O que são resíduos (erro = real - predito)
- Como criar histograma de resíduos
- O que é Q-Q Plot e como interpretar
- Documentação do `scipy.stats.probplot`

### 5. Feature Importance (para modelos tree-based)

**Se usar Random Forest ou XGBoost:** Extraia e visualize a importância das features.

**Pesquise:**
- Atributo `.feature_importances_` de modelos tree-based
- Como ordenar features por importância
- Como criar gráfico de barras mostrando top 10 features
- Interpretação da importância de features

---

## ✅ Critérios de Avaliação

| Critério | Peso | O Que Avaliamos |
|----------|:----:|-----------------|
| **Variedade de Modelos** | 20% | Pelo menos 5 modelos diferentes testados |
| **Métricas e Avaliação** | 25% | Métricas corretas, validação cruzada |
| **Análise Comparativa** | 25% | Comparação clara, visualizações, interpretações |
| **Documentação** | 15% | Markdown explicativo, decisões justificadas |
| **Apresentação** | 15% | Clareza, participação, visualizações |

---

## 📦 Como Entregar

### 1. Commit e Push
```bash
git add notebooks/03_Modelagem.ipynb
git commit -m "feat: Completa Etapa 3 - Modelagem"
git push origin main
```

### 2. Apresentação
- Upload dos slides em `docs/apresentacao_etapa3.pdf`
- Apresentar na aula marcada pelo professor

---

## 💡 Dicas Importantes

**DO:**
✅ Teste TODOS os modelos com os mesmos dados
✅ Use validação cruzada para confirmar resultados
✅ Interprete as métricas (não apenas calcule!)
✅ Analise ONDE o modelo erra (não só QUANTO erra)
✅ Documente hiperparâmetros usados

**DON'T:**
❌ Treinar no conjunto de teste (data leakage!)
❌ Comparar modelos com métricas diferentes
❌ Escolher modelo só pelo R² (veja outras métricas!)
❌ Esquecer de normalizar dados (se necessário)

---

## 🎯 Checklist Antes de Entregar

- [ ] Pelo menos 5 modelos diferentes treinados
- [ ] Validação cruzada executada
- [ ] Métricas calculadas (MAE, RMSE, R²)
- [ ] Gráficos comparativos criados
- [ ] Análise de resíduos feita
- [ ] Melhor modelo identificado e justificado
- [ ] Notebook executa "Restart & Run All" sem erros
- [ ] Apresentação preparada (8-10 slides)
- [ ] Todos os membros do grupo participam da apresentação

---

## 🆘 Precisa de Ajuda?

**Dúvidas comuns:**
- Qual modelo usar? → Teste vários! Não dá para saber a priori
- R² negativo? → Modelo muito ruim ou erro na implementação
- Overfitting? → Etapa 4 vai tratar isso (regularização e tuning)

**Consulte:**
- Scikit-learn model selection: https://scikit-learn.org/stable/model_selection.html
- XGBoost docs: https://xgboost.readthedocs.io/
- Material da aula de modelagem

---

**Boa modelagem!** 🤖

*Última atualização: Outubro 2027*
