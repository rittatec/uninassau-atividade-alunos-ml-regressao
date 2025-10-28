# 🔧 Etapa 2: Pré-processamento e Feature Engineering

**Prazo de Entrega:** [Data será informada pelo professor]
**Peso:** 25% da nota do projeto (2.5 pontos)
**Entregáveis:**
- `notebooks/02_Preprocessamento.ipynb`
- `data/processed/dataset_clean.csv`
- Apresentação de 10 minutos

---

## 🎯 Objetivos da Etapa

Ao final desta etapa, você deve:

1. **Tratar problemas de qualidade** - Corrigir valores faltantes, outliers, inconsistências
2. **Preparar dados para ML** - Encoding, normalização, seleção de features
3. **Criar novas features** - Feature engineering para melhorar o modelo
4. **Salvar dados limpos** - Dataset processado pronto para modelagem

---

## 📋 O Que Você Vai Entregar

### 1. Notebook Principal
**`notebooks/02_Preprocessamento.ipynb`**

Seções obrigatórias:
1. Importação e Carregamento
2. Tratamento de Valores Faltantes
3. Tratamento de Outliers
4. Encoding de Variáveis Categóricas
5. Normalização/Padronização
6. Feature Engineering (criação de novas features)
7. Seleção de Features
8. Divisão Treino/Validação/Teste
9. Salvamento dos Dados Processados

### 2. Dataset Limpo
**`data/processed/dataset_clean.csv`**
- Dados prontos para modelagem
- Sem valores faltantes
- Features numéricas
- Normalizado/padronizado (se necessário)

### 3. Apresentação (10 minutos) 🎤

**O que apresentar:**
- Principais problemas identificados na Etapa 1
- Decisões de tratamento tomadas e justificativas
- Features criadas e por quê
- Comparação: dataset antes vs depois
- Estatísticas finais do dataset limpo

**Formato:**
- 5-7 slides (PowerPoint, Google Slides, ou PDF)
- Todos os membros do grupo devem participar
- Demonstre visualizações comparativas
- Foque nas decisões técnicas (não leia código!)

**Critérios de avaliação da apresentação:**
- Clareza na comunicação (30%)
- Justificativa técnica das decisões (40%)
- Participação de todos os membros (20%)
- Qualidade visual dos slides (10%)

---

## 🔍 Análises Obrigatórias

### 1. Tratamento de Missing Values

**Decisões a tomar:**
- Qual estratégia usar? (remoção, imputação média/mediana/moda, KNN)
- Por quê essa estratégia?
- Qual o impacto no dataset?

**Código esperado:**
```python
# Exemplo: Imputação
from sklearn.impute import SimpleImputer

# Justifique sua escolha!
imputer = SimpleImputer(strategy='median')
df[numeric_cols] = imputer.fit_transform(df[numeric_cols])
```

### 2. Tratamento de Outliers

**Decisões a tomar:**
- Remover ou manter?
- Winsorization? Capping?
- Justifique!

### 3. Encoding de Categóricas

**Obrigatório:**
- One-Hot Encoding para categóricas nominais
- Label Encoding ou Ordinal Encoding para ordinais
- Explique qual variável recebeu qual tratamento

**Código esperado:**
```python
from sklearn.preprocessing import OneHotEncoder, LabelEncoder

# One-Hot para nominais
encoder = OneHotEncoder(drop='first', sparse_output=False)

# Label para ordinais (se houver)
label_encoder = LabelEncoder()
```

### 4. Normalização/Padronização

**Decisões a tomar:**
- StandardScaler ou MinMaxScaler?
- Aplicar em quais variáveis?
- Por quê?

### 5. Feature Engineering

**Criar pelo menos 3 novas features:**

Exemplos:
- Razões/proporções (ex: `study_efficiency = previous_scores / study_hours_week`)
- Binnings (ex: categorizar idade em faixas)
- Interações (ex: `parental_education * family_income`)
- Agregações

**Importante:** Justifique cada feature criada!

### 6. Seleção de Features

**Análises obrigatórias:**
- Correlação com target
- Variance Threshold (remover features com variância zero)
- Análise de importância (opcional: usar modelo simples)

### 7. Divisão dos Dados

**Obrigatório:**
```python
from sklearn.model_selection import train_test_split

# 70% treino, 15% validação, 15% teste
X_temp, X_test, y_temp, y_test = train_test_split(
    X, y, test_size=0.15, random_state=42
)
X_train, X_val, y_train, y_val = train_test_split(
    X_temp, y_temp, test_size=0.1765, random_state=42  # 0.1765 * 0.85 ≈ 0.15
)
```

---

## ✅ Critérios de Avaliação

| Critério | Peso | O Que Avaliamos |
|----------|:----:|-----------------|
| **Notebook Técnico** | 50% | Código funcional, decisões justificadas, documentação |
| **Dataset Limpo** | 20% | Qualidade do dataset final, pronto para modelagem |
| **Feature Engineering** | 15% | Criatividade, features úteis, justificativas |
| **Apresentação** | 15% | Clareza, participação, visualizações |

---

## 📦 Como Entregar

### 1. Commit e Push
```bash
git add notebooks/02_Preprocessamento.ipynb
git add data/processed/dataset_clean.csv
git commit -m "feat: Completa Etapa 2 - Pré-processamento"
git push origin main
```

### 2. Apresentação
- Upload dos slides em `docs/apresentacao_etapa2.pdf`
- Apresentar na aula marcada pelo professor

---

## 💡 Dicas Importantes

**DO:**
✅ Justifique TODAS as decisões de tratamento
✅ Compare estatísticas antes vs depois
✅ Documente o raciocínio em markdown
✅ Salve transformações (scalers, encoders) para reutilizar
✅ Execute "Restart & Run All" antes de entregar

**DON'T:**
❌ Remover dados sem justificativa
❌ Aplicar tratamentos sem entender o impacto
❌ Esquecer de documentar o processo
❌ Deixar a apresentação para última hora

---

## 🆘 Precisa de Ajuda?

**Dúvidas comuns:**
- Qual imputação usar? → Depende do tipo de missing (MCAR/MAR/MNAR)
- Devo remover outliers? → Só se forem erros de medição
- Quantas features criar? → Pelo menos 3, mas qualidade > quantidade

**Consulte:**
- Scikit-learn docs: https://scikit-learn.org/stable/modules/preprocessing.html
- Material da aula de pré-processamento
- Professor no horário de atendimento

---

**Boa sorte!** 🚀

*Última atualização: Outubro 2027*
