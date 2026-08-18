# 📊 Visualização de Dados com Matplotlib — Time Series

Este projeto faz parte dos estudos de **Python para Data Science**, utilizando a biblioteca **Matplotlib** para criar e personalizar um gráfico de série temporal.

O objetivo do exercício é visualizar a quantidade de usuários da Codecademy ao longo das 24 horas de um dia e adicionar uma **faixa de variação de ±15%** em torno dos valores observados.

---

## 🎯 Objetivos

Neste exercício são praticados os seguintes conceitos:

- Importação de bibliotecas Python
- Criação e manipulação de listas
- `range()`
- Gráficos com Matplotlib
- Gráficos de linha com `plt.plot()`
- Título e nomes dos eixos
- Legendas
- Personalização de gráficos
- Configuração de `ticks`
- List Comprehension
- Cálculo percentual
- `plt.fill_between()`
- Transparência com `alpha`
- Visualização de uma faixa de variação

---

# 🧰 Bibliotecas utilizadas

```python
import codecademylib3_seaborn
from matplotlib import pyplot as plt
import numpy as np
import pandas as pd
```

## `codecademylib3_seaborn`

É uma biblioteca utilizada pelo ambiente da Codecademy para configurar recursos relacionados à visualização.

Em um projeto Python comum, ela normalmente não é necessária.

---

## Matplotlib

```python
from matplotlib import pyplot as plt
```

Importa o módulo `pyplot` da biblioteca Matplotlib e cria o apelido `plt`.

O Matplotlib é uma das principais bibliotecas Python utilizadas para **visualização de dados**.

O apelido `plt` permite utilizar comandos como:

```python
plt.plot()
plt.title()
plt.xlabel()
plt.ylabel()
plt.show()
```

---

## NumPy

```python
import numpy as np
```

Importa a biblioteca NumPy com o apelido `np`.

O NumPy é muito utilizado para:

- cálculos matemáticos;
- operações com arrays;
- álgebra linear;
- manipulação numérica.

Neste exercício, o NumPy foi importado, mas não é utilizado diretamente.

---

## Pandas

```python
import pandas as pd
```

Importa o Pandas com o apelido `pd`.

O Pandas é muito utilizado em Data Science para:

- carregar dados;
- trabalhar com tabelas;
- analisar DataFrames;
- limpar dados;
- manipular séries temporais.

Também não é utilizado diretamente neste código.

---

# 🕐 Criando as horas

```python
hour = range(24)
```

`range(24)` cria uma sequência de números de `0` até `23`.

Isso representa as 24 horas de um dia:

```text
0  → 00:00
1  → 01:00
2  → 02:00
...
12 → 12:00
...
23 → 23:00
```

Portanto:

```python
hour
```

será utilizado como o **eixo X** do gráfico.

---

# 👥 Dados de visualizações

```python
viewers_hour = [
    30, 17, 34, 29, 19, 14,
    3, 2, 4, 9, 5, 48,
    62, 58, 40, 51, 69, 55,
    76, 81, 102, 120, 71, 63
]
```

Essa lista contém a quantidade de espectadores em cada hora.

Existe uma correspondência entre `hour` e `viewers_hour`.

| Hora | Viewers |
| ---: | ------: |
|    0 |      30 |
|    1 |      17 |
|    2 |      34 |
|    3 |      29 |
|    4 |      19 |
|    5 |      14 |
|    6 |       3 |
|    7 |       2 |
|    8 |       4 |
|    9 |       9 |
|   10 |       5 |
|   11 |      48 |
|   12 |      62 |
|   13 |      58 |
|   14 |      40 |
|   15 |      51 |
|   16 |      69 |
|   17 |      55 |
|   18 |      76 |
|   19 |      81 |
|   20 |     102 |
|   21 |     120 |
|   22 |      71 |
|   23 |      63 |

Por exemplo:

```python
hour[21] = 21
viewers_hour[21] = 120
```

Isso significa que às **21h havia 120 espectadores**.

---

# 📈 Criando o título

```python
plt.title("Codecademy Learners Time Series")
```

Define o título do gráfico.

O termo **Time Series** significa **série temporal**.

Uma série temporal é um conjunto de dados organizados de acordo com o tempo.

Neste caso:

> quantidade de espectadores × hora do dia.

---

# ➡️ Nomeando o eixo X

```python
plt.xlabel("Hour")
```

Define o nome do eixo horizontal:

```text
Hour
```

Portanto:

**Eixo X = hora**

---

# ⬆️ Nomeando o eixo Y

```python
plt.ylabel("Viewers")
```

Define o nome do eixo vertical:

```text
Viewers
```

Portanto:

**Eixo Y = número de espectadores**

---

# 📉 Criando o gráfico de linha

```python
plt.plot(hour, viewers_hour)
```

Essa é uma das principais funções do Matplotlib.

A estrutura básica é:

```python
plt.plot(x, y)
```

Neste caso:

```python
plt.plot(hour, viewers_hour)
```

Portanto:

```text
X → hour
Y → viewers_hour
```

O Matplotlib cria pontos como:

```text
(0, 30)
(1, 17)
(2, 34)
...
(21, 120)
...
(23, 63)
```

e conecta esses pontos formando uma linha.

---

# 🏷️ Criando uma legenda

```python
plt.legend(['2015-01-01'])
```

Adiciona uma legenda ao gráfico.

Neste exercício, a legenda indica que os dados correspondem à data:

```text
2015-01-01
```

Em um gráfico com várias datas, cada linha poderia representar um dia diferente.

Por exemplo:

```text
2015-01-01
2015-01-02
2015-01-03
```

---

# 🖼️ Criando o objeto Axes

```python
ax = plt.subplot()
```

Cria uma área de gráfico e armazena essa área na variável:

```python
ax
```

A partir disso, podemos personalizar o gráfico utilizando:

```python
ax.set_facecolor()
ax.set_xticks()
ax.set_yticks()
```

---

# 🎨 Alterando a cor do fundo

```python
ax.set_facecolor('seashell')
```

Define a cor de fundo da área do gráfico.

`seashell` é um nome de cor reconhecido pelo Matplotlib.

Essa linha é apenas uma **personalização visual**.

---

# 📏 Configurando o eixo X

```python
ax.set_xticks(hour)
```

Define quais valores aparecerão como marcações no eixo X.

Como `hour` contém:

```text
0, 1, 2, 3, ..., 23
```

todas as 24 horas serão mostradas no eixo.

---

# 📏 Configurando o eixo Y

```python
ax.set_yticks([0, 20, 40, 60, 80, 100, 120])
```

Define manualmente as marcações do eixo Y.

O gráfico terá:

```text
0
20
40
60
80
100
120
```

Isso facilita a leitura dos valores.

---

# 📊 Criando uma faixa superior de variação

```python
y_upper = [i + (i * 0.15) for i in viewers_hour]
```

Essa linha utiliza uma **List Comprehension**.

Ela significa:

> Para cada valor `i` em `viewers_hour`, calcular um valor 15% maior.

Por exemplo:

```text
Valor = 100

15% de 100 = 15

100 + 15 = 115
```

Portanto:

```python
100 → 115
```

Se tivermos:

```python
viewers_hour = [100, 200, 300]
```

teremos:

```python
y_upper = [115, 230, 345]
```

---

# 📉 Criando uma faixa inferior de variação

```python
y_lower = [i - (i * 0.15) for i in viewers_hour]
```

Agora fazemos o contrário.

Para cada valor, calculamos um número **15% menor**.

Por exemplo:

```text
Valor = 100

15% de 100 = 15

100 - 15 = 85
```

Portanto:

```python
100 → 85
```

Para:

```python
viewers_hour = [100, 200, 300]
```

teremos:

```python
y_lower = [85, 170, 255]
```

---

# 🌫️ Criando a área sombreada

```python
plt.fill_between(hour, y_lower, y_upper, alpha=0.2)
```

Essa função preenche a região existente entre:

```text
y_lower
```

e:

```text
y_upper
```

A ideia é criar uma **faixa de variação de ±15%** em torno dos valores reais.

Visualmente:

```text
        y_upper (+15%)
             ▲
             │
      ░░░░░░░░░░░
      ░░░░░░░░░░░
      ─────●─────  ← viewers_hour
      ░░░░░░░░░░░
      ░░░░░░░░░░░
             │
             ▼
        y_lower (-15%)
```

---

# 🔍 Por que utilizar uma faixa de variação?

A faixa ajuda a representar visualmente uma **margem ao redor dos dados**.

Por exemplo, se temos:

```text
Valor real = 100
```

e utilizamos ±15%:

```text
Limite inferior = 85
Valor central = 100
Limite superior = 115
```

Então podemos visualizar:

```text
85 ───────── limite inferior
          │
100 ──────●────── valor observado
          │
115 ───────── limite superior
```

Em projetos reais de Data Science, uma faixa como essa pode representar diferentes conceitos, dependendo do contexto:

- intervalo de confiança;
- intervalo de previsão;
- erro de medição;
- desvio padrão;
- margem de erro;
- faixa esperada de valores.

**Importante:** neste exercício, o ±15% é uma faixa ilustrativa. Não significa necessariamente que exista uma incerteza estatística real de 15%.

---

# 👀 Por que a faixa quase desaparece entre 6h e 10h?

Entre 6h e 10h os valores são muito baixos:

```text
6h  → 3
7h  → 2
8h  → 4
9h  → 9
10h → 5
```

Por exemplo, às 7h:

```text
Valor = 2

15% = 0,3

Limite inferior = 1,7
Limite superior = 2,3
```

A diferença entre `1,7` e `2,3` é muito pequena.

Como o eixo Y chega até aproximadamente 120, essa faixa fica praticamente invisível.

Isso não significa que `fill_between()` não esteja funcionando.

A faixa está lá, mas é pequena em relação à escala do gráfico.

---

# 🎚️ Transparência

O parâmetro:

```python
alpha=0.2
```

define a transparência da área preenchida.

O `alpha` varia normalmente entre:

```text
0 → totalmente transparente

1 → totalmente opaco
```

Exemplos:

```python
alpha=0.1
```

→ muito transparente

```python
alpha=0.5
```

→ transparência intermediária

```python
alpha=1
```

→ totalmente sólido

---

# 🖥️ Exibindo o gráfico

```python
plt.show()
```

Finalmente, `plt.show()` manda o Matplotlib exibir o gráfico.

---

# 🧠 Conceitos principais

O fluxo do programa pode ser resumido assim:

```text
Dados
  ↓
hour
  ↓
viewers_hour
  ↓
plt.plot()
  ↓
Gráfico de linha
  ↓
Calcula +15%
  ↓
y_upper
  ↓
Calcula -15%
  ↓
y_lower
  ↓
plt.fill_between()
  ↓
Faixa de variação
  ↓
plt.show()
```

---

# 📌 Código completo

```python
import codecademylib3_seaborn
from matplotlib import pyplot as plt
import numpy as np
import pandas as pd

hour = range(24)

viewers_hour = [
    30, 17, 34, 29, 19, 14,
    3, 2, 4, 9, 5, 48,
    62, 58, 40, 51, 69, 55,
    76, 81, 102, 120, 71, 63
]

plt.title("Codecademy Learners Time Series")

plt.xlabel("Hour")
plt.ylabel("Viewers")

plt.plot(hour, viewers_hour)

plt.legend(['2015-01-01'])

ax = plt.subplot()

ax.set_facecolor('seashell')

ax.set_xticks(hour)
ax.set_yticks([0, 20, 40, 60, 80, 100, 120])

y_upper = [i + (i * 0.15) for i in viewers_hour]
y_lower = [i - (i * 0.15) for i in viewers_hour]

plt.fill_between(hour, y_lower, y_upper, alpha=0.2)

plt.show()
```

---

# 🚀 O que este exercício ensina para Data Science?

Este exercício é um primeiro contato com uma etapa fundamental de Data Science:

**Transformar dados em informação visual.**

O processo pode ser entendido como:

```text
Dados
  ↓
Organização
  ↓
Análise
  ↓
Visualização
  ↓
Interpretação
```

Neste caso, os dados são simplesmente:

> quantidade de usuários por hora.

A visualização permite identificar rapidamente padrões, como:

- baixo número de usuários pela manhã;
- aumento de usuários durante o dia;
- crescimento significativo no período da noite;
- pico de aproximadamente **120 usuários às 21h**.

Esse tipo de análise visual é fundamental antes de avançar para análises estatísticas e Machine Learning.
