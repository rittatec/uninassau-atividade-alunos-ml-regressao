# ⚡ Etapa 4: Otimização e Tuning de Hiperparâmetros

**Prazo de Entrega:** [Data será informada pelo professor]
**Peso:** 25% da nota do projeto (2.5 pontos)
**Entregáveis:**
- `notebooks/04_Otimizacao.ipynb`
- Modelo final salvo
- Apresentação de 15 minutos

---

## 🎯 Objetivos da Etapa

Ao final desta etapa, você deve:

1. **Otimizar hiperparâmetros** - Tuning do melhor modelo da Etapa 3
2. **Evitar overfitting** - Técnicas de regularização e validação
3. **Avaliar no conjunto de teste** - Desempenho final do modelo
4. **Salvar modelo final** - Modelo treinado pronto para produção

---

## 📋 O Que Você Vai Entregar

### 1. Notebook Principal
**`notebooks/04_Otimizacao.ipynb`**

Seções obrigatórias:
1. Recapitulação dos Resultados da Etapa 3
2. Seleção do Modelo para Otimização
3. Grid Search ou Random Search
4. Análise dos Melhores Hiperparâmetros
5. Treinamento do Modelo Final
6. Avaliação no Conjunto de Teste
7. Análise de Erros Detalhada
8. Salvamento do Modelo
9. Conclusões Finais

### 2. Modelo Treinado
**`models/modelo_final.pkl`** (ou `.joblib`)
- Modelo otimizado e treinado
- Pronto para fazer predições

### 3. Apresentação (15 minutos) 🎤

**O que apresentar:**
- Recapitulação: melhor modelo da Etapa 3
- Processo de otimização de hiperparâmetros
- Hiperparâmetros testados vs selecionados
- Comparação: modelo antes vs depois da otimização
- Desempenho final no conjunto de teste
- Análise de erros e limitações
- Possíveis melhorias futuras

**Formato:**
- 8-12 slides
- Todos os membros do grupo devem participar
- Inclua gráficos de comparação
- Mostre exemplos de predições

**Critérios de avaliação da apresentação:**
- Profundidade técnica (35%)
- Análise crítica do modelo (25%)
- Visualizações e clareza (20%)
- Participação de todos (20%)

---

## 🔍 Análises Obrigatórias

### 1. Otimização de Hiperparâmetros

**Escolha uma técnica:**

#### Opção A: Grid Search (Busca Exaustiva)
```python
from sklearn.model_selection import GridSearchCV

# Definir grid de hiperparâmetros
param_grid = {
    'n_estimators': [100, 200, 300],
    'max_depth': [10, 20, 30, None],
    'min_samples_split': [2, 5, 10],
    'min_samples_leaf': [1, 2, 4]
}

# Grid Search
grid_search = GridSearchCV(
    estimator=RandomForestRegressor(random_state=42),
    param_grid=param_grid,
    cv=5,  # 5-fold cross-validation
    scoring='neg_mean_absolute_error',
    n_jobs=-1,  # usar todos os processadores
    verbose=2
)

grid_search.fit(X_train, y_train)

print("Melhores hiperparâmetros:", grid_search.best_params_)
print("Melhor score:", -grid_search.best_score_)
```

#### Opção B: Random Search (Mais Rápido)
```python
from sklearn.model_selection import RandomizedSearchCV
import numpy as np

# Distribuições de hiperparâmetros
param_distributions = {
    'n_estimators': [100, 200, 300, 400, 500],
    'max_depth': [10, 20, 30, 40, 50, None],
    'min_samples_split': [2, 5, 10, 15],
    'min_samples_leaf': [1, 2, 4, 6],
    'max_features': ['auto', 'sqrt', 'log2']
}

random_search = RandomizedSearchCV(
    estimator=RandomForestRegressor(random_state=42),
    param_distributions=param_distributions,
    n_iter=50,  # 50 combinações aleatórias
    cv=5,
    scoring='neg_mean_absolute_error',
    n_jobs=-1,
    verbose=2,
    random_state=42
)

random_search.fit(X_train, y_train)

print("Melhores hiperparâmetros:", random_search.best_params_)
```

### 2. Análise dos Resultados do Tuning

**Visualizar o processo:**
```python
# Converter resultados em DataFrame
results_df = pd.DataFrame(grid_search.cv_results_)

# Top 10 melhores combinações
top_10 = results_df.nsmallest(10, 'rank_test_score')[
    ['params', 'mean_test_score', 'std_test_score']
]
print(top_10)

# Gráfico de comparação
plt.figure(figsize=(12, 6))
plt.errorbar(
    range(len(top_10)),
    -top_10['mean_test_score'],
    yerr=top_10['std_test_score'],
    fmt='o-'
)
plt.xlabel('Configuração')
plt.ylabel('MAE')
plt.title('Top 10 Configurações de Hiperparâmetros')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

### 3. Treinamento do Modelo Final

**Treinar com melhores hiperparâmetros:**
```python
# Obter melhor modelo
best_model = grid_search.best_estimator_

# OU treinar manualmente com os melhores parâmetros
final_model = RandomForestRegressor(
    n_estimators=200,
    max_depth=20,
    min_samples_split=5,
    # ... outros parâmetros
    random_state=42
)

# Treinar no conjunto de TREINO + VALIDAÇÃO
X_train_full = pd.concat([X_train, X_val])
y_train_full = pd.concat([y_train, y_val])

final_model.fit(X_train_full, y_train_full)
```

### 4. Avaliação Final no Conjunto de Teste

**⚠️ IMPORTANTE:** Só use o conjunto de teste UMA VEZ!

```python
# Predições no conjunto de teste
y_test_pred = final_model.predict(X_test)

# Calcular métricas finais
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import numpy as np

mae_test = mean_absolute_error(y_test, y_test_pred)
rmse_test = np.sqrt(mean_squared_error(y_test, y_test_pred))
r2_test = r2_score(y_test, y_test_pred)

print("="*50)
print("DESEMPENHO FINAL NO CONJUNTO DE TESTE")
print("="*50)
print(f"MAE:  {mae_test:.2f}")
print(f"RMSE: {rmse_test:.2f}")
print(f"R²:   {r2_test:.4f}")
print("="*50)
```

### 5. Comparação: Antes vs Depois da Otimização

**Crie tabela comparativa:**
```python
comparison = pd.DataFrame({
    'Métrica': ['MAE', 'RMSE', 'R²'],
    'Antes (Etapa 3)': [mae_antes, rmse_antes, r2_antes],
    'Depois (Etapa 4)': [mae_test, rmse_test, r2_test],
    'Melhoria (%)': [
        ((mae_antes - mae_test) / mae_antes) * 100,
        ((rmse_antes - rmse_test) / rmse_antes) * 100,
        ((r2_test - r2_antes) / r2_antes) * 100
    ]
})

print(comparison)
```

### 6. Análise de Erros Detalhada

**Gráficos obrigatórios:**

#### Scatter: Predito vs Real
```python
plt.figure(figsize=(10, 6))
plt.scatter(y_test, y_test_pred, alpha=0.5)
plt.plot([y_test.min(), y_test.max()], [y_test.min(), y_test.max()],
         'r--', lw=2, label='Predição Perfeita')
plt.xlabel('Valores Reais')
plt.ylabel('Valores Preditos')
plt.title('Predições vs Valores Reais - Conjunto de Teste')
plt.legend()
plt.show()
```

#### Distribuição dos Resíduos
```python
residuals = y_test - y_test_pred

fig, axes = plt.subplots(1, 2, figsize=(14, 5))

# Histograma
axes[0].hist(residuals, bins=30, edgecolor='black')
axes[0].axvline(0, color='r', linestyle='--', linewidth=2)
axes[0].set_xlabel('Resíduo')
axes[0].set_ylabel('Frequência')
axes[0].set_title('Distribuição dos Resíduos')

# Resíduos vs Predições
axes[1].scatter(y_test_pred, residuals, alpha=0.5)
axes[1].axhline(0, color='r', linestyle='--', linewidth=2)
axes[1].set_xlabel('Valores Preditos')
axes[1].set_ylabel('Resíduos')
axes[1].set_title('Resíduos vs Predições')

plt.tight_layout()
plt.show()
```

#### Análise de Casos Extremos
```python
# Identificar piores predições
errors = np.abs(residuals)
worst_indices = errors.nlargest(10).index

print("10 PIORES PREDIÇÕES:")
print(pd.DataFrame({
    'Real': y_test.iloc[worst_indices],
    'Predito': y_test_pred[worst_indices],
    'Erro Absoluto': errors.iloc[worst_indices]
}))
```

### 7. Salvamento do Modelo

**Salvar modelo treinado:**
```python
import joblib

# Criar pasta models (se não existir)
import os
os.makedirs('models', exist_ok=True)

# Salvar modelo
joblib.dump(final_model, 'models/modelo_final.joblib')

print("✅ Modelo salvo com sucesso!")

# Testar carregamento
loaded_model = joblib.load('models/modelo_final.joblib')
print("✅ Modelo carregado com sucesso!")

# Verificar se funciona
test_prediction = loaded_model.predict(X_test[:5])
print("Predições de teste:", test_prediction)
```

---

## ✅ Critérios de Avaliação

| Critério | Peso | O Que Avaliamos |
|----------|:----:|-----------------|
| **Otimização de Hiperparâmetros** | 30% | Grid/Random Search executado, melhores params identificados |
| **Avaliação Final** | 25% | Métricas no teste, comparação antes/depois |
| **Análise de Erros** | 20% | Resíduos, casos extremos, interpretação |
| **Documentação** | 10% | Markdown claro, decisões justificadas |
| **Apresentação** | 15% | Clareza, participação, profundidade técnica |

---

## 📦 Como Entregar

### 1. Commit e Push
```bash
# Criar pasta models
mkdir -p models

git add notebooks/04_Otimizacao.ipynb
git add models/modelo_final.joblib
git commit -m "feat: Completa Etapa 4 - Otimização e modelo final"
git push origin main
```

### 2. Apresentação
- Upload dos slides em `docs/apresentacao_etapa4.pdf`
- Apresentar na aula marcada pelo professor

---

## 💡 Dicas Importantes

**DO:**
✅ Documente TODOS os hiperparâmetros testados
✅ Use validação cruzada durante o tuning
✅ Analise POR QUE o modelo erra (não só QUANTO)
✅ Compare antes vs depois da otimização
✅ Teste o modelo salvo para garantir que funciona

**DON'T:**
❌ Usar o conjunto de teste durante o tuning (data leakage!)
❌ Fazer tuning sem validação cruzada
❌ Testar hiperparâmetros aleatoriamente sem critério
❌ Esquecer de salvar o modelo final
❌ Ignorar análise de erros

---

## 🎯 Checklist Antes de Entregar

- [ ] Grid Search ou Random Search executado
- [ ] Melhores hiperparâmetros identificados
- [ ] Modelo final treinado com TREINO + VALIDAÇÃO
- [ ] Avaliação no conjunto de TESTE (uma única vez)
- [ ] Comparação antes vs depois criada
- [ ] Análise de resíduos completa
- [ ] Casos extremos (piores erros) analisados
- [ ] Modelo salvo em `models/modelo_final.joblib`
- [ ] Notebook executa "Restart & Run All" sem erros
- [ ] Apresentação preparada (8-12 slides)

---

## 🆘 Precisa de Ajuda?

**Dúvidas comuns:**
- Grid Search vs Random Search? → Grid = exaustivo mas lento; Random = mais rápido
- Quantos hiperparâmetros testar? → Comece com 3-4 principais
- Overfitting após tuning? → Verifique validação cruzada, pode precisar regularização

**Consulte:**
- Scikit-learn hyperparameter tuning: https://scikit-learn.org/stable/modules/grid_search.html
- XGBoost tuning guide: https://xgboost.readthedocs.io/en/stable/tutorials/param_tuning.html
- Material da aula de otimização

---

**Ótima otimização!** ⚡

*Última atualização: Outubro 2027*
