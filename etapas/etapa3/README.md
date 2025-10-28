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
```python
from sklearn.linear_model import LinearRegression

baseline = LinearRegression()
baseline.fit(X_train, y_train)
```

### Modelos Avançados (escolha pelo menos 5)

**Obrigatório testar:**
1. **Ridge Regression** ou **Lasso Regression**
2. **Decision Tree Regressor**
3. **Random Forest Regressor**
4. **Gradient Boosting** (XGBoost, LightGBM, ou CatBoost)
5. **Support Vector Regressor** ou **KNN Regressor** ou **Elastic Net**

**Exemplo de código:**
```python
from sklearn.ensemble import RandomForestRegressor
from xgboost import XGBRegressor
from sklearn.tree import DecisionTreeRegressor

models = {
    'Linear Regression': LinearRegression(),
    'Random Forest': RandomForestRegressor(random_state=42),
    'XGBoost': XGBRegressor(random_state=42),
    'Decision Tree': DecisionTreeRegressor(random_state=42),
    # ... adicione mais 2
}
```

---

## 📊 Métricas Obrigatórias

Para **regressão**, calcule:

1. **MAE** (Mean Absolute Error)
2. **MSE** (Mean Squared Error)
3. **RMSE** (Root Mean Squared Error)
4. **R²** (R-squared)
5. **MAPE** (Mean Absolute Percentage Error) - opcional

**Código esperado:**
```python
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import numpy as np

mae = mean_absolute_error(y_true, y_pred)
mse = mean_squared_error(y_true, y_pred)
rmse = np.sqrt(mse)
r2 = r2_score(y_true, y_pred)

print(f"MAE: {mae:.2f}")
print(f"RMSE: {rmse:.2f}")
print(f"R²: {r2:.4f}")
```

---

## 🔬 Análises Obrigatórias

### 1. Treinamento de Todos os Modelos

Loop pelos modelos:
```python
results = {}

for name, model in models.items():
    # Treinar
    model.fit(X_train, y_train)

    # Predizer no conjunto de validação
    y_pred = model.predict(X_val)

    # Calcular métricas
    mae = mean_absolute_error(y_val, y_pred)
    rmse = np.sqrt(mean_squared_error(y_val, y_pred))
    r2 = r2_score(y_val, y_pred)

    results[name] = {'MAE': mae, 'RMSE': rmse, 'R²': r2}
```

### 2. Validação Cruzada

**Obrigatório:**
```python
from sklearn.model_selection import cross_val_score

for name, model in models.items():
    scores = cross_val_score(
        model, X_train, y_train,
        cv=5,  # 5-fold cross-validation
        scoring='neg_mean_absolute_error'
    )
    print(f"{name} - CV MAE: {-scores.mean():.2f} (+/- {scores.std():.2f})")
```

### 3. Comparação Visual

**Crie gráficos:**

#### Gráfico de Barras - Comparação de MAE
```python
import matplotlib.pyplot as plt

models_names = list(results.keys())
mae_values = [results[m]['MAE'] for m in models_names]

plt.figure(figsize=(10, 6))
plt.barh(models_names, mae_values)
plt.xlabel('MAE (menor é melhor)')
plt.title('Comparação de Modelos - MAE')
plt.show()
```

#### Scatter Plot - Predito vs Real
```python
# Para o melhor modelo
plt.figure(figsize=(8, 8))
plt.scatter(y_val, y_pred, alpha=0.5)
plt.plot([y_val.min(), y_val.max()], [y_val.min(), y_val.max()], 'r--', lw=2)
plt.xlabel('Valores Reais')
plt.ylabel('Valores Preditos')
plt.title('Predito vs Real - [Nome do Modelo]')
plt.show()
```

### 4. Análise de Erros

**Obrigatório:**
```python
# Resíduos
residuals = y_val - y_pred

# Histograma dos resíduos
plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.hist(residuals, bins=30, edgecolor='black')
plt.xlabel('Resíduo (Real - Predito)')
plt.title('Distribuição dos Resíduos')

# Q-Q Plot
plt.subplot(1, 2, 2)
from scipy import stats
stats.probplot(residuals, plot=plt)
plt.title('Q-Q Plot dos Resíduos')
plt.tight_layout()
plt.show()
```

### 5. Feature Importance (para modelos tree-based)

**Se usar Random Forest ou XGBoost:**
```python
# Feature importance
importances = model.feature_importances_
feature_names = X_train.columns

# Ordenar
indices = np.argsort(importances)[::-1][:10]  # Top 10

plt.figure(figsize=(10, 6))
plt.barh(range(10), importances[indices])
plt.yticks(range(10), [feature_names[i] for i in indices])
plt.xlabel('Importância')
plt.title('Top 10 Features Mais Importantes')
plt.show()
```

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
