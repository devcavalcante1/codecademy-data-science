Problema do Aniversário --- Probabilidade e Simulação

O problema do aniversário é um ótimo exemplo para entender
probabilidade em Data Science.

1. A ideia principal

Suponha que você tenha n pessoas em uma sala.

Queremos saber:

Qual é a probabilidade de pelo menos duas pessoas fazerem
aniversário no mesmo dia?

É mais fácil calcular o contrário:

Qual é a probabilidade de ninguém fazer aniversário no mesmo dia?

Depois usamos:

[ P(\text{match}{=tex}) = 1 - P(\text{nenhum match}{=tex}) ]

2. Exemplo com 2 pessoas

Para a primeira pessoa, qualquer dia serve:

[ \frac{365}{365}{=tex} = 1 ]

Para a segunda pessoa não ter o mesmo aniversário:

[ \frac{364}{365}{=tex} ]

Então:

[ P(\text{nenhum match}{=tex}) = \frac{365}{365}{=tex}
\times {=tex}\frac{364}{365}{=tex} ]

[ P(\text{nenhum match}{=tex}) \approx 0.99726{=tex} ]

Logo:

[ P(\text{match}{=tex}) = 1 - 0.99726 ]

[ P(\text{match}{=tex}) \approx 0.00274{=tex} = 0.274% ]

Ou seja, com 2 pessoas, a chance de haver um aniversário em comum é
aproximadamente 0,27%.

3. E com 23 pessoas?

É aqui que o problema fica interessante.

Para 23 pessoas:

[ P(\text{nenhum match}{=tex}) = \frac{365}{365}{=tex}
\times{=tex} \frac{364}{365}{=tex} \times{=tex}
\frac{363}{365}{=tex} \times {=tex}\cdots {=tex}\times{=tex}
\frac{343}{365}{=tex} ]

Então:

[ P(\text{match}{=tex}) = 1 - P(\text{nenhum match}{=tex}) ]

O resultado é:

[ P(\text{match}{=tex}) \approx 50{=tex},73% ]

Com apenas 23 pessoas, já existe mais de 50% de chance de duas pessoas
terem o mesmo aniversário.

4. Como calcular em Python

Podemos calcular a probabilidade usando um for:

n = 23

prob_no_match = 1

for i in range(n):
prob_no_match \*= (365 - i) / 365

prob_match = 1 - prob_no_match

print(prob_match)
print(prob_match \* 100)

Resultado aproximado:

0.507297234
50.7297234

Portanto, a probabilidade é aproximadamente:

50,73%

Observação: não precisamos importar math nesse cálculo.

5. O que o código está fazendo?

A parte principal é:

prob_no_match \*= (365 - i) / 365

Ela calcula, pessoa por pessoa, a probabilidade de não ocorrer uma
coincidência de aniversário.

Por exemplo:

Número de pessoas Probabilidade de match

                2                    0,27%
                5                    2,71%
               10                   11,69%
               20                   41,14%
           **23**               **50,73%**
               30                   70,63%
               40                   89,12%
               50                   97,04%

Quanto maior o número de pessoas, maior a chance de pelo menos duas
compartilharem o mesmo aniversário.

6. E onde entra a simulação?

O exercício provavelmente utiliza uma lógica semelhante a esta:

import random

birthdays = []

for i in range(23):
birthday = random.randint(1, 365)
birthdays.append(birthday)

print(birthdays)

Depois, o programa verifica se existem números repetidos.

Nesse caso, cada número representa um dia do ano:

1 → dia 1

2 → dia 2

...

365 → dia 365

Se aparecer o mesmo número duas vezes, temos um match.

Por exemplo:

[34, 120, 87, 34, 250]

Nesse caso, o número 34 apareceu duas vezes.

Portanto, existe um match.

7. Simulação de Monte Carlo

Quando usamos números aleatórios para repetir um experimento muitas
vezes, estamos fazendo uma simulação de Monte Carlo.

Em vez de calcular somente a probabilidade matematicamente, podemos:

Criar uma sala com várias pessoas.

Atribuir um aniversário aleatório para cada pessoa.

Verificar se houve algum aniversário repetido.

Repetir o experimento milhares de vezes.

Calcular em quantas simulações ocorreu um match.

Por exemplo, imagine 10.000 simulações com 23 pessoas.

Se aproximadamente 5.000 simulações apresentarem um match:

[ \frac{5000}{10000}{=tex} = 0.50 ]

Ou seja:

[ 50% ]

Esse resultado fica próximo da probabilidade teórica de 50,73%.

8. Probabilidade teórica × simulação

Essa comparação é muito importante em Data Science.

Probabilidade teórica

É calculada matematicamente:

[ P(\text{match}{=tex}) \approx 50{=tex},73% ]

Probabilidade experimental

É obtida através da simulação:

[ P(\text{match}{=tex}) =
\frac{\text{número de simulações com match}}{=tex}
{\text{número total de simulações}{=tex}} ]

Por exemplo:

[ \frac{5030}{10000}{=tex} = 50,3% ]

Os valores não precisam ser exatamente iguais, porque a simulação
utiliza números aleatórios.

Entretanto, quanto maior o número de simulações, normalmente mais
próximo o resultado experimental ficará da probabilidade teórica.

9. Por que esse problema é interessante?

À primeira vista, pode parecer que seriam necessárias muitas pessoas
para existir uma chance significativa de aniversário compartilhado.

Mas o resultado é surpreendente:

Com apenas 23 pessoas, a probabilidade já passa de 50%.

Isso acontece porque não estamos comparando apenas uma pessoa com outra.

Com 23 pessoas, existem muitas possíveis combinações de pares:

[ \frac{23 \times 22}{2}{=tex} = 253 ]

Ou seja, existem 253 pares diferentes que poderiam ter o mesmo
aniversário.

É isso que faz a probabilidade crescer rapidamente.

10. Conclusão

O problema do aniversário demonstra três conceitos importantes:

Probabilidade teórica: calculada matematicamente.

Simulação: criação de cenários aleatórios para observar
resultados.

Monte Carlo: repetição de muitas simulações para estimar uma
probabilidade.

Para 23 pessoas:

[ \boxed{P(\text{match}) \approx 50,73\%}{=tex} ]

Portanto, se você executar várias simulações com 23 pessoas, é esperado
que aproximadamente metade delas apresente pelo menos um aniversário
compartilhado.

Esse tipo de raciocínio é muito utilizado em Data Science,
especialmente quando queremos estimar probabilidades e estudar cenários
através de dados simulados.
