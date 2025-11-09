
# 📊 Semana 1: Análise Exploratória de Dados (EDA)

**Prazo de Entrega:** [Data será informada pelo professor]
**Peso:** 25% da nota do projeto (1.0 ponto)
**Entregável:** `notebooks/01_EDA.ipynb`

---

## 🎯 Objetivos da Semana

Ao final desta semana, você deve:

1. **Conhecer profundamente o dataset** - Entender cada variável, seus valores e significados
2. **Identificar problemas de qualidade** - Encontrar valores faltantes, outliers, inconsistências
3. **Explorar relações entre variáveis** - Descobrir correlações e padrões
4. **Comunicar descobertas** - Documentar tudo em um notebook claro e organizado

**⚠️ IMPORTANTE:** Esta etapa é APENAS análise. **NÃO** trate/corrija problemas ainda!

---

## 📋 O Que Você Vai Entregar

### Arquivo Principal
- **`notebooks/01_EDA.ipynb`** - Notebook Jupyter com toda a análise exploratória

### Conteúdo Obrigatório do Notebook


O notebook deve conter as seguintes seções (use headers markdown):

1. Importação de Bibliotecas
2. Carregamento dos Dados
3. Visão Geral do Dataset
4. Análise de Valores Faltantes
5. Análise da Variável Alvo (final_grade)
6. Análise Univariada - Variáveis Numéricas
7. Análise Univariada - Variáveis Categóricas
8. Análise de Correlações
9. Análise Bivariada (Features vs Target)
10. Identificação de Outliers
11. Conclusões e Descobertas Principais

**Dica:** Sempre que houver atualização ou nova versão deste roteiro, apenas ajuste as orientações e exemplos, mantendo a estrutura das seções. Assim, o arquivo permanece útil para futuras edições.

---

## 🔍 Análises Obrigatórias



### 1. Importação de Bibliotecas

Pesquise quais bibliotecas são necessárias para análise exploratória de dados em Python (ex: pandas, numpy, matplotlib, seaborn, scipy). Importe-as no notebook e explique, em uma célula markdown, para que serve cada uma.

---


### 2. Carregamento dos Dados


Utilize pandas para carregar o dataset. Descubra como visualizar as primeiras e últimas linhas, dimensões, tipos de dados e estatísticas descritivas. Consulte a documentação do pandas para cada etapa.

**📝 Documente:** Quantas linhas e colunas o dataset possui? O que você observa nas primeiras linhas?

---


### 3. Visão Geral do Dataset


Separe as variáveis do dataset em numéricas e categóricas. Pesquise como identificar os tipos de variáveis usando pandas. Liste todas as variáveis de cada tipo, identifique a variável alvo (`final_grade`) e variáveis de identificação (ex: `student_id`).

**📝 Documente:** Qual é a variável alvo? Quais são as features?

---


### 4. Análise de Valores Faltantes


Pesquise como identificar e quantificar valores faltantes em cada variável. Descubra como criar visualizações (ex: gráfico de barras) para mostrar o percentual de missing. Investigue se há padrão nos valores faltantes (aleatório ou sistemático?).

**📝 Documente:**
- Qual variável tem mais missing?
- Os valores faltantes parecem aleatórios ou seguem algum padrão?
- Sugira possíveis tratamentos (não implemente ainda).

---


### 5. Análise da Variável Alvo: final_grade


Pesquise como calcular estatísticas descritivas (média, mediana, desvio padrão, mínimo, máximo, skewness, kurtosis) para a variável alvo. Descubra como criar histogramas, boxplots e Q-Q plots para analisar a distribuição. Investigue como realizar o teste de normalidade (ex: Shapiro-Wilk) e interpretar o resultado.

**📝 Documente:**
- A distribuição é normal?
- Há assimetria? Para qual lado?
- Existem outliers? Quantos?
- Qual a faixa de valores mais comum?

---


### 6. Análise Univariada - Variáveis Numéricas


Para cada variável numérica (exceto student_id e final_grade), pesquise como calcular estatísticas descritivas, criar histogramas e boxplots, e identificar outliers usando o método IQR. Explique cada passo no seu notebook e documente as principais descobertas.

**📝 Documente para cada variável:**
- Faixa de valores (min, max)
- Distribuição (normal, assimétrica, bimodal?)
- Presença de outliers
- Valores impossíveis ou suspeitos

---


### 7. Análise Univariada - Variáveis Categóricas


Para cada variável categórica, pesquise como contar valores únicos, calcular frequências, criar gráficos de barras e identificar problemas de formatação ou categorias inesperadas. Documente suas descobertas e explique possíveis desbalanceamentos.

**📝 Documente:**
- Há desbalanceamento entre categorias?
- Existem problemas de formatação (espaços, maiúsculas)?
- Alguma categoria inesperada?

---


### 8. Análise de Correlações


Pesquise como calcular a matriz de correlação entre variáveis numéricas e como visualizar usando heatmap. Descubra como identificar a correlação de cada feature com a variável alvo e como detectar multicolinearidade. Documente suas interpretações e possíveis correlações inesperadas.

**📝 Documente:**
- Qual feature tem maior correlação com final_grade?
- Há multicolinearidade?
- Alguma correlação surpreendente?

---


### 9. Análise Bivariada


Para cada variável categórica, pesquise como analisar a relação entre as categorias e a variável final_grade. Descubra como calcular estatísticas por categoria, criar boxplots e interpretar diferenças de desempenho. Documente suas conclusões.

**📝 Documente:**
- Quais categorias têm melhor desempenho?
- As diferenças são significativas?
- Há sobreposição entre distribuições?

---


### 10. Identificação de Outliers


Pesquise como identificar outliers em variáveis numéricas usando o método IQR. Resuma a quantidade e o percentual de outliers em cada variável e discuta se são legítimos ou possíveis erros.

**📝 Documente:**
- Quais variáveis têm mais outliers?
- Os outliers parecem legítimos ou são erros?
- Existem valores impossíveis?

---


### 11. Conclusões e Descobertas


Escreva um resumo executivo da sua análise em células markdown, respondendo:

1. Principais características do dataset (tamanho, tipos de variáveis, qualidade geral)
2. Problemas identificados (valores faltantes, outliers, inconsistências, formatação)
3. Descobertas sobre a variável alvo
4. Features mais importantes
5. Próximos passos sugeridos

**Dica:** Sempre adapte esta seção para refletir as descobertas do seu grupo, sem copiar exemplos prontos.

---

## ✅ Critérios de Avaliação

Seu notebook será avaliado pelos seguintes critérios:

| Critério | Peso | Descrição |
|----------|:----:|-----------|
| **Completude** | 30% | Todas as análises obrigatórias foram feitas? |
| **Visualizações** | 20% | Gráficos claros, com títulos, labels e legendas? |
| **Documentação** | 25% | Interpretações em markdown? Descobertas explicadas? |
| **Qualidade Técnica** | 15% | Código funciona? Sem erros? Organizado? |
| **Insights** | 10% | Identificou padrões interessantes? Conclusões válidas? |

### Detalhamento:

**Completude (30%):**
- ✅ Todas as 11 seções estão presentes
- ✅ Análises obrigatórias realizadas
- ✅ Todas as variáveis analisadas

**Visualizações (20%):**
- ✅ Mínimo 4 gráficos
- ✅ Títulos descritivos
- ✅ Labels nos eixos
- ✅ Legendas quando necessário
- ✅ Tamanho apropriado (figsize)

**Documentação (25%):**
- ✅ Células markdown explicando cada análise
- ✅ Interpretação dos resultados
- ✅ Conclusões em seção final
- ✅ Código comentado (quando complexo)

**Qualidade Técnica (15%):**
- ✅ Notebook executa do início ao fim ("Restart & Run All")
- ✅ Sem erros
- ✅ Código organizado e limpo
- ✅ Nomes de variáveis descritivos

**Insights (10%):**
- ✅ Descobertas interessantes
- ✅ Padrões identificados
- ✅ Recomendações para próximas etapas

---

## 🚫 Erros Comuns a Evitar

### ❌ NÃO FAÇA:

1. **Tratar dados nesta etapa**
   - NÃO preencha valores faltantes
   - NÃO remova outliers
   - NÃO faça encoding de categóricas
   - **Esta etapa é APENAS análise!**

2. **Visualizações sem contexto**
   - NÃO crie gráficos sem título
   - NÃO esqueça labels nos eixos
   - NÃO use cores confusas

3. **Código sem documentação**
   - NÃO deixe apenas código
   - NÃO esqueça de interpretar resultados
   - NÃO omita conclusões

4. **Análise superficial**
   - NÃO faça apenas o mínimo
   - NÃO ignore variáveis
   - NÃO copie código sem entender

---

## 💡 Dicas de Sucesso

### 🎯 Organização

1. **Use headers markdown** para separar seções
2. **Adicione índice** no início do notebook
3. **Numere suas descobertas** para facilitar referência
4. **Use cores consistentes** nas visualizações

### 🔍 Exploração Profunda

- Vá **além do obrigatório**
- Teste **hipóteses** sobre os dados
- Procure **padrões interessantes**
- Seja **curioso**!

### 🧪 Antes de Entregar

**Checklist final:**
- [ ] Execute "Restart Kernel & Run All Cells"
- [ ] Verifique que não há erros
- [ ] Todas as visualizações aparecem
- [ ] Markdown sem erros de digitação
- [ ] Conclusões escritas
- [ ] Commit e push realizados

---

## 📦 Como Entregar

### 1. Certifique-se de que está na branch correta

```bash
# Ver branch atual
git branch

# Se não estiver na main, volte
git checkout main
```

### 2. Salve e teste o notebook

- Salve o notebook
- Verifique que tudo funciona

### 3. Commit e Push

```bash
git add notebooks/01_EDA.ipynb
git commit -m "feat: Adiciona análise exploratória completa (Semana 1)

- Análise de valores faltantes
- Análise univariada de todas as variáveis
- Matriz de correlação
- Análise bivariada
- Identificação de outliers
- Conclusões e descobertas"

git push origin main
```

### 4. Verifique no GitHub

- Acesse seu repositório no GitHub
- Confirme que o arquivo aparece
- Teste se o notebook renderiza corretamente

---

## ⏰ Gestão de Tempo Sugerida


<!-- Cronograma removido para deixar o roteiro atemporal e mais flexível. -->

---

**Boa análise! Descubra os segredos escondidos nos dados!** 🔍🚀

