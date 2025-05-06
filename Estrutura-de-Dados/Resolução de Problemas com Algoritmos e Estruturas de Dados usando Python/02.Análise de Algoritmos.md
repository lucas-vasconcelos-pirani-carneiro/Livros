# Análise de Algoritmos
## 02.1. Objetivos
- Entender porque a análise de algoritmos é importante 
- Utilizar a “Notação O” para descrever o **tempo de execução**
	- Operações sobre listas e dicionários

## 02.2. O que é Análise de Algoritmos
#### Algoritmos x Programas
- **Algoritmo:** É uma lista passo a passo genérica de instruções para resolver um problema. 
- **Programa:** É um algoritmo que foi codificado em alguma linguagem de programação.
- Pode haver diversos programas para o mesmo algoritmo, dependendo do programador e da linguagem de programação utilizada.
- A análise de algoritmos se preocupa com a *comparação de algoritmos* baseada na quantidade de **recursos computacionais** que cada algoritmo usa
#### Recursos Computacionais: 
- Quantidade de **espaço ou memória** que um algoritmo necessita para resolver o problema
- Quantidade de **tempo** que necessitam para ser executados

*Exemplo:* Soma de dos n primeiros inteiros
```python
import time

def somaDeN2(n):
   inicio = time.time()

   aSoma = 0
   for i in range(1,n+1):
      aSoma = aSoma + i

   fim = time.time()

   return aSoma,fim-inicio
```

```bash
# n = 10000
>>> for i in range(5):
       print("A soma é %d demorou %10.7f segundos"%somaDeN2(10000))
A soma é 50005000 demorou  0.0018950 segundos
A soma é 50005000 demorou  0.0018620 segundos
A soma é 50005000 demorou  0.0019171 segundos
A soma é 50005000 demorou  0.0019162 segundos
A soma é 50005000 demorou  0.0019360 segundos
# n = 100000
>>> for i in range(5):
       print("A soma é %d demorou %10.7f segundos"%somaDeN2(100000))
A soma é 5000050000 demorou  0.0199420 segundos
A soma é 5000050000 demorou  0.0180972 segundos
A soma é 5000050000 demorou  0.0194821 segundos
A soma é 5000050000 demorou  0.0178988 segundos
A soma é 5000050000 demorou  0.0188949 segundos
# n = 1000000
>>> for i in range(5):
       print("A soma é %d demorou %10.7f segundos"%somaDeN2(1000000))
A soma é 500000500000 demorou  0.1948988 segundos
A soma é 500000500000 demorou  0.1850290 segundos
A soma é 500000500000 demorou  0.1809771 segundos
A soma é 500000500000 demorou  0.1729250 segundos
A soma é 500000500000 demorou  0.1646299 segundos
```
- O tempo se manteve consistente em cada um dos casos 
- Contudo,podemos usar uma outra maneira para resolver essa soma(Soma de Gauss)
$$
S = \sum_{k=1}^{n} k = \frac{n(n+1)}{2}
$$

```python
def somaDeN3(n):
   return (n*(n+1))/2

print(somaDeN3(10))
```

```bash
A soma é 50005000 demorou 0.00000095 segundos
A soma é 5000050000 demorou 0.00000191 segundos
A soma é 500000500000 demorou 0.00000095 segundos
A soma é 50000005000000 demorou 0.00000095 segundos
A soma é 5000000050000000 demorou 0.00000119 segundos
```

- Observações:
1. Os tempos obtidos acima são mais **curtos** do que qualquer um dos exemplos anteriores
2. São bastantes consistentes **independente** do valor de `n`.`somaDeN3` mal é impactada pelo número de inteiros sendo somados. 
- Intuitivamente,as soluções iterativas parecem fazer mais trabalho, uma vez que alguns passos do programa são repetidos demorando mais no tempo de execução 
- O tempo necessário para a solução iterativa parece aumentar conforme aumentamos o valor de `n`. 
- Entretanto, se executarmos a mesma função em **computadores diferentes** ou usarmos uma **linguagem de programação diferente**, provavelmente obteríamos resultados diferentes.  
- **Resumo:** A técnica de aferição(tempo de execução) não nos fornece uma medida necessariamente útil visto que ela depende de diversos fatores.
	- máquina, programa, hora do dia, compilador e linguagem de programação particulares

## 02.3. Notação $O$

### Unidades Básicas de Computação
- Para avaliar a eficiência de um algoritmo, medimos o **número de passos** (ou operações) realizados, e não o tempo real em segundos. Isso independe da **máquina** ou **linguagem** usada.

> **Exemplo:**  
> A função `sumOfN()` soma os `n` primeiros números naturais e realiza `1 + n` instruções de atribuição.  
> Assim:  
> ```math
> T(n) = 1 + n
> ```
> Onde `T(n)` representa o número total de passos e `n` é o **tamanho do problema**.

### Big-O e Ordem de Grandeza
- A **notação Big-O (O-grande)** nos ajuda a entender **como o algoritmo cresce** em função do tamanho da entrada, ignorando constantes e termos menores.
###  Exemplos:
- Para $T(n) = 1 + n$, a parte dominante é `n` → $O(n)$
- Para $T(n) = 5n^2 + 27n + 1005$, a parte dominante é $n^2$ → $O(n^2)$
### Casos de Análise
Alguns algoritmos variam de desempenho dependendo dos dados de entrada. Por isso, analisamos:
- **Melhor caso:** entrada mais favorável.
- **Pior caso:** entrada mais desfavorável.
- **Caso médio:** desempenho esperado na média das execuções.
### Tabela: Ordens de Grandeza Comuns

| Notação Big-O             | Nome         | Crescimento                    |
| ------------------------- | ------------ | ------------------------------ |
| $\Theta(1)$               | Constante    | Não depende de `n`             |
| $\Theta(log(n))$          | Logarítmica  | Cresce lentamente              |
| $\Theta(n)$               | Linear       | Cresce proporcional a `n`      |
| $\Theta(n \times log(n))$ | Linearítmica | Comum em algoritmos eficientes |
| $\Theta(n^2)$             | Quadrática   | Cresce rápido                  |
| $\Theta(n^3)$             | Cúbica       | Cresce mais ainda              |
| $\Theta(2^n)$             | Exponencial  | Crescimento explosivo          |
| $\Theta(n!)$              | Fatorial     | Impraticável para grandes `n`  |

![../_images/newplot.png](https://panda.ime.usp.br/pythonds/static/pythonds_pt/_images/newplot.png)

### Como examinar um código e analisar o seu desempenho ?
```python
a=5
b=6
c=10
for i in range(n):
   for j in range(n):
      x = i * i
      y = j * j
      z = i * j
for k in range(n):
   w = a*k + 45
   v = b*b
d = 33
```

- O número de operações de atribuição é a **soma** de **quatro** termos
- 1º Termo: $3$

```python
a=5
b=6
c=10
```

- 2º Termo: $3n^2$
	- três fragmentos que são executados $n^2$ vezes devido as **iterações aninhadas**

```python
for i in range(n):
   for j in range(n):
      x = i * i
      y = j * j
      z = i * j
```

- 3º Termo: $2n$
	- dois comandos **iterados** $n$ vezes

```python
for k in range(n):
   w = a*k + 45
   v = b*b
```

- 4º Termo: $1$
	- representa o último comando de atribuição

```python
d = 33
```

Logo, $T(n) = 3 + 3n^2 +2n + 1 = 3n^2 + 2n + 4$
Analisando os termos:
- Termo dominante: `3n²`
- Termos menores e constantes são **ignorados** para análise assintótica
Portanto, a **complexidade assintótica** é: $T(n) = O(n^2)$

## 02.4.Exemplos
- **Detecção de anagramas** para strings
- Uma string é um anagrama de outra se a segunda é simplesmente um **rearranjo** da primeira
- *Exemplos:* `amor` e `roma`, `socorram` e `marrocos`
### 02.4.1.Solução 01: Marcação
- Verificar se **cada carácter** da **primeira** string realmente ocorre na **segunda**.
 - A **marcação de um caractere** será realizada substituindo-o pelo valor especial em Python `None`. 
 - Entretanto, como strings em Python são **imutáveis**, o primeiro passo do processo será **converter a segunda string** em uma **lista**. 
 - Cada caractere da primeira string será buscado entre os caracteres da segunda lista e, caso encontrado, será marcado por substituição

```python
def solucaoAnagrama1(s1,s2):
    umalista = list(s2)

    pos1 = 0
    aindaOK = True

    while pos1 < len(s1) and aindaOK:
        pos2 = 0
        encontrado = False
        while pos2 < len(umalista) and not encontrado:
            if s1[pos1] == umalista[pos2]:
                encontrado = True
            else:
                pos2 = pos2 + 1

        if encontrado:
            umalista[pos2] = None
        else:
            aindaOK = False

        pos1 = pos1 + 1

    return aindaOK

print(solucaoAnagrama1('abcd','dcba'))
```
- Cada um dos _n_ caracteres em `s1` causará uma iteração por até _n_ caracteres na lista de `s2`.
- Cada uma das _n_ posições na lista será visitada uma vez para marcar um caractere de `s1`
- O número de visitas: Soma dos inteiros entre 1 e _n_.
$$
S = \sum_{k=1}^{n} k = \frac{n(n+1)}{2} = \frac{n^2 + n}{2}
$$

- **Complexidade Assintótica**: $O(n^2)$
### 02.4.2. Ordenar e Comparar
- Anagramas possuem exatamente os **mesmos caracteres**
- Se **ordenarmos** cada string **alfabeticamente**, de a a z, implica que as duas strings precisariam ser iguais
- Converter as Strings em listas e usar o método `sort`
```python
def solucaoAnagrama2(s1,s2):
    umalista1 = list(s1)
    umalista2 = list(s2)

    umalista1.sort()
    umalista2.sort()

    pos = 0
    iguais = True

    while pos < len(s1) and iguais:
        if umalista1[pos]==umalista2[pos]:
            pos = pos + 1
        else:
            iguais = False

    return iguais

print(solucaoAnagrama2('abcde','edcba'))
```
- Aparenta ser $O(n)$ visto que apresenta somente uma interação para comparar os n caracteres depois da ordenação
- Entretanto, é preciso analisar o custo do método de ordenação `sort`.
	- $O(n^2)$ ou $O(n*log(n))$
- Assim, as operações de ordenação dominam sobre a interação.Logo, o algoritmo terá a mesma ordem de magnitude do processo de ordenação
### 02.4.3. Força Bruta
- Tenta todas as possibilidades à exaustão
- Neste caso, podemos simplesmente gerar uma lista com todas as strings possíveis usando os caracteres de `s1` e verificar se `s2` ocorre
- Contudo, analisando a quantidade de possibilidades teríamos o seguinte:
	- 1º Posição: *n* possibilidades
	- 2º Posição: n - 1 possibilidades
	- 3º Posição: n - 2 possibilidades, e assim por diante
- Ou seja, o total de possibilidades = $n!$ possibilidades
- Logo, para um $n$ muito grande ficaria completamente inviável

### 02.4.4. Contar e Comparar
- Utilizar o fato de que quaisquer dois anagramas terão o mesmo número de a’s, o mesmo número de b’s, o mesmo número de c’s e assim por diante.
- Contar o número de vezes que cada carácter aparece.
- 26 caracteres = lista de 26 contadores (um para cada caractere possível)
- Cada vez que encontramos um caractere em particular, incrementamos o seu contador naquela posição
- Se as duas listas de contadores são idênticas, as strings são anagramas
```python
def solucaoAnagrama4(s1,s2):
    c1 = [0]*26
    c2 = [0]*26

    for i in range(len(s1)):
        pos = ord(s1[i])-ord('a')
        c1[pos] = c1[pos] + 1

    for i in range(len(s2)):
        pos = ord(s2[i])-ord('a')
        c2[pos] = c2[pos] + 1

    j = 0
    aindaOK = True
    while j<26 and aindaOK:
        if c1[j] == c2[j]:
            j = j + 1
        else:
            aindaOK = False

    return aindaOK

print(solucaoAnagrama4('marrocos','socorram'))
```
- As duas primeiras iterações utilizadas para contar os caracteres são ambas baseadas em _n_ (tamanho da string)
- A terceira iteração comparando as duas listas de contadores, sempre demoram 26 passos,já que há somente 26 possíveis caracteres nas strings
- Logo, $T(n)=2n+26 \text{ passos} => O(n)$
- Contudo, esse algoritmo utiliza memória adicional para armazenar as duas listas de contadores de caracteres.
- Sacrificou espaço para ganhar tempo.

## 02.5.Listas
#### Operações Comuns e Complexidade

| Operação                  | Complexidade |
| ------------------------- | ------------ |
| Acesso por índice ([])    | O(1)         |
| Atribuição por índice     | O(1)         |
| append()                  | O(1)         |
| pop() --> fim             | O(1)         |
| pop(i) --> início/meio    | O(n)         |
| insert(i, item)           | O(n)         |
| del, fatiamento           | O(n)         |
| Iteração (for)            | O(n)         |
| Verificação com **in**    | O(n)         |
| **Concatenar** listas (+) | O(k)         |
| reverse()                 | O(n)         |
| **Ordenar** --> sort()    | O(n * log n) |
| **Multiplicação** (*)     | O(nk)        |

#### Testando Performance com `timeit`
- criar uma lista de 0 a 999
```python
def teste1():
    l = []
    for i in range(1000):
        l = l + [i]   # concatenação (ineficiente)

def teste2():
    l = []
    for i in range(1000):
        l.append(i)   # append (eficiente)

def teste3():
    l = [i for i in range(1000)]  # list comprehension

def teste4():
    l = list(range(1000))         # construtor com range
```

| Método        | Tempo (ms) |
| ------------- | ---------- |
| Concatenação  | 6.54       |
| append()      | 0.30       |
| Comprehension | 0.15       |
| list(range()) | 0.06       |

- **Conclusão**: `list(range())` é o mais rápido. `append()` é muito mais eficiente que concatenação com `+`.
#### Diferença entre `pop()` e `pop(0)`
- Teste com lista de 2.000.000 elementos:
```python
x = list(range(2000000))
popfim.timeit(number=1000)     # 0.0003 ms
popzero.timeit(number=1000)    # 4.82 ms
```
- Quando removemos o **primeiro elemento** de uma lista, todos os outros elementos da lista precisam ser movidos para a **esquerda**.
## 02.6.Dicionários
- Acessa os itens através de uma **chave** ao invés de uma posição

| Operação             | Complexidade |
| -------------------- | ------------ |
| **copy**             | O(n)         |
| acessar item         | O(1)         |
| atribuir item        | O(1)         |
| remover item         | O(1)         |
| Verificar com **in** | O(1)         |
| iterar               | O(n)         |

- Em situações raras, acessar ou verificar a existência de um item em um dicionário pode levar até $O(n)$
#### `in` em listas vs dicionários
- Listas: $O(n)$
- Dicionários:$O(1)$
```python
import timeit
import random

for i in range(10000, 1000001, 20000):
    t = timeit.Timer("random.randrange(%d) in x" % i,
                     "from __main__ import random, x")
    x = list(range(i))
    tempo_lista = t.timeit(number=1000)
    x = {j: None for j in range(i)}
    tempo_dic = t.timeit(number=1000)
    print("%d,%10.3f,%10.3f" % (i, tempo_lista, tempo_dic))
```
- Resultado: Dicionário dominou
	- Para uma lista com 10.000 elementos, o dicionário foi cerca de **89 vezes mais rápido**.
	- Para 990.000 elementos, a diferença cresceu para mais de **11.000 vezes**!