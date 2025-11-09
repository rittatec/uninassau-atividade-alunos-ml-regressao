# 📊 Atualização: Suporte a 10 Datasets

**Data:** 28 de Outubro de 2027
**Versão:** 2.2

---

## ✅ Mudanças Realizadas

### 1. Estrutura de Pastas Atualizada

**Antes:**
```
data/
├── raw/
│   ├── students_performance.csv
│   └── README.md (apenas 1 dataset)
└── processed/
```

**Agora:**
```
data/
├── datasets/
│   ├── students_performance.csv      (Dataset 1)
│   ├── ecommerce_sales.csv           (Dataset 2)
│   ├── energy_consumption.csv        (Dataset 3)
│   ├── housing_prices.csv            (Dataset 4)
│   ├── delivery_time.csv             (Dataset 5)
│   ├── salary_prediction.csv         (Dataset 6) ✨ NOVO
│   ├── youtube_views.csv             (Dataset 7) ✨ NOVO
│   ├── restaurant_rating.csv         (Dataset 8) ✨ NOVO
│   ├── used_cars_price.csv           (Dataset 9) ✨ NOVO
│   ├── employee_productivity.csv     (Dataset 10) ✨ NOVO
│   └── README.md                     (⭐ Documentação completa dos 10)
└── processed/
```


## 📊 Datasets Disponíveis

| # | Nome | Prever | Registros | Features | Dificuldade |
|:-:|------|--------|-----------|----------|-------------|
| 1 | 🎓 Desempenho Acadêmico | Nota final (0-100) | 2.510 | 13 | ⭐⭐ |
| 2 | 🛒 Vendas E-commerce | Vendas (R$) | 2.510 | 16 | ⭐⭐⭐ |
| 3 | ⚡ Consumo de Energia | Consumo (kWh) | 2.510 | 16 | ⭐⭐⭐ |
| 4 | 🏠 Preços de Imóveis | Preço (R$) | 2.510 | 17 | ⭐⭐⭐⭐ |
| 5 | 🚚 Tempo de Entrega | Tempo (horas) | 2.510 | 16 | ⭐⭐⭐ |
| 6 | 💼 Salário TI | Salário (R$) | 2.520 | 17 | ⭐⭐⭐ |
| 7 | 📺 YouTube | Visualizações | 2.520 | 21 | ⭐⭐⭐ |
| 8 | 🍽️ Restaurante | Nota (1-5) | 2.520 | 24 | ⭐⭐ |
| 9 | 🚗 Carros Usados | Preço (R$) | 2.520 | 25 | ⭐⭐⭐ |
| 10 | 📊 Produtividade | Horas/semana | 2.520 | 28 | ⭐⭐ |

---

## 📖 Documentação dos Datasets

### Arquivo: `data/datasets/README.md`

Este arquivo contém para CADA um dos 10 datasets:

✅ **Objetivo do problema**
✅ **Características (registros, features)**
✅ **Lista completa de variáveis**
✅ **Aplicação prática**
✅ **Problemas de qualidade dos dados**
✅ **Comparação entre datasets**
✅ **Exemplos de código**

---

## 🎯 Como os Alunos Escolhem o Dataset

### Passo 1: Ler Documentação
Abrir `data/datasets/README.md` e ver descrição de cada um

### Passo 2: Discutir em Grupo
- Qual tema é mais interessante?
- Qual tem mais relevância prática?
- Qual a dificuldade adequada ao grupo?

### Passo 3: Informar o Professor
Comunicar qual dataset foi escolhido na primeira semana

### Passo 4: Trabalhar com Apenas 1
Usar o mesmo dataset em todas as 5 etapas do projeto

---

## 🔍 Onde Está Cada Informação

### Para Alunos:
1. **Visão geral dos 10 datasets:** `README.md` principal (seção "SOBRE OS DATASETS")
2. **Documentação completa:** `data/datasets/README.md`
3. **Arquivos CSV:** `data/datasets/*.csv`
---

## ✅ Validação

### Arquivos Verificados:
- [x] `data/datasets/students_performance.csv` existe (187 KB)
- [x] `data/datasets/ecommerce_sales.csv` existe (258 KB)
- [x] `data/datasets/energy_consumption.csv` existe (180 KB)
- [x] `data/datasets/housing_prices.csv` existe (237 KB)
- [x] `data/datasets/delivery_time.csv` existe (249 KB)
- [x] `data/datasets/salary_prediction.csv` existe ✨ NOVO
- [x] `data/datasets/youtube_views.csv` existe ✨ NOVO
- [x] `data/datasets/restaurant_rating.csv` existe ✨ NOVO
- [x] `data/datasets/used_cars_price.csv` existe ✨ NOVO
- [x] `data/datasets/employee_productivity.csv` existe ✨ NOVO
- [x] `data/datasets/README.md` atualizado com 10 datasets
---


**Dúvidas sobre os datasets:**
- Consulte `data/datasets/README.md`
- Contate o professor

