# Introdução
## O que é Ciência da Computação?
Ciência da Computação vai além do estudo de computadores — ela trata do **estudo de problemas, suas soluções e dos algoritmos** usados para resolvê-los. Um **algoritmo** é uma sequência finita de passos que, se seguidos corretamente, resolvem um problema.

Nem todos os problemas são solucionáveis; por isso, a Ciência da Computação também estuda **quais problemas são computáveis e quais não são**. A computação envolve **abstrações**, ou seja, a separação entre **como usamos** e **como algo funciona por dentro**.

**Exemplo de abstração:**
- Um **usuário de carro** sabe dirigir, mas não entende o motor.
- Um **mecânico** entende o motor e todos os detalhes internos.
- O mesmo vale para computadores: usuários usam, cientistas da computação entendem o “motor”.

Essa visão abstrata é chamada de **"caixa preta"**, onde nos importamos apenas com a **interface (como usar)** e não com a **implementação interna** (como funciona).

## O que é Programação?
**Programar** é transformar um algoritmo em código utilizando uma **linguagem de programação**, tornando-o executável por um computador.

A programação **não é o foco único** da Ciência da Computação, mas é uma ferramenta essencial para implementar e representar soluções. Para isso, as linguagens oferecem:
- **Construções de controle**: sequência, decisão (if), repetição (loops).
- **Tipos de dados**: interpretam os dados binários (inteiros, reais, etc.).

**Exemplo:**  
O número 23 é armazenado como uma sequência binária na memória, e a linguagem precisa saber que isso representa um **inteiro**.

À medida que os problemas ficam mais complexos, **os recursos simples de linguagem não são suficientes**. É aí que entram as abstrações e estruturas mais sofisticadas.

## Por Que Estudar Estruturas de Dados e Tipos de Dados Abstratos?
Para lidar com a complexidade, usamos **tipos de dados abstratos (ADT)**: eles descrevem **o que os dados representam e como interagimos com eles**, **sem mostrar como são implementados**.

Isso é chamado de **ocultação de informação** ou **encapsulamento**.

**Exemplo de ADT:**  
Você sabe como usar uma **lista** (adicionar, remover, acessar elementos), mas não precisa saber **como ela funciona internamente**.

A implementação física dos ADTs é feita por meio de **estruturas de dados**, como arrays, filas, pilhas, árvores, etc. A grande vantagem disso é a **independência entre a interface e a implementação**, permitindo modificar o interior sem alterar a forma como o usuário interage.

## Por Que Estudar Algoritmos ?
Aprender algoritmos é essencial para resolver novos problemas de forma eficiente. Existem várias maneiras de resolver um mesmo problema, e algumas são melhores que outras em **velocidade** e **uso de memória**.

Ao estudar algoritmos, aprendemos a:
- **Comparar soluções**.
- **Medir desempenho**.
- **Reconhecer padrões**.
- **Identificar problemas que não têm solução prática** (problemas intratáveis).

Saber apenas resolver um problema não é suficiente; precisamos também avaliar **a qualidade da solução**.

## Revisão de Python Básico
Python é uma linguagem **moderna, fácil de aprender e interpretada**, ideal para iniciantes e para trabalhar com algoritmos e estruturas de dados.

Características:
- **Orientada a objetos**.
- **Tipos de dados nativos poderosos** (listas, dicionários, strings, etc.).
- **Controle de fluxo intuitivo** (`if`, `for`, `while`).
- Ambiente interativo com o prompt `>>>` que facilita testes rápidos.

**Exemplo:**
```python
>>> import math
>>> math.sqrt(16)
4.0
```

Esse código usa uma **função da biblioteca math** — outro exemplo de abstração: usamos sem saber como a raiz quadrada é calculada por dentro.

## Primeiros Passos com Dados
O Python, como linguagem orientada a objetos, organiza o processamento de informações com base em _objetos_ — instâncias de _classes_, que descrevem tanto o _estado_ quanto o _comportamento_ de dados.

### Tipos de Dados Atômicos Nativos

#### Tipos Numéricos: `int` e `float`
- `int`: Números inteiros (ex: 1, -5, 1000).
- `float`: Números reais (ex: 3.14, -0.001, 1.0).

**Operadores aritméticos:**
- `+`, `-`, `*`, `/`, `**` (exponenciação)
- `%`: resto da divisão
- `//`: divisão inteira (trunca a parte decimal)

```python
print(2 + 3 * 4)       # 14
print((2 + 3) * 4)     # 20
print(2 ** 10)         # 1024
print(7 / 3)           # 2.333...
print(7 // 3)          # 2
print(7 % 3)           # 1
```

#### Tipo Booleano: `bool`
- Pode armazenar: `True` ou `False`.
- Usado em comparações e lógica condicional.

```python
print(True and False)         # False
print(not (False or True))   # False
print(5 == 10)               # False
print(10 > 5)                # True
print((5 >= 1) and (5 <= 10)) # True
```

**Operadores lógicos:**

| Operador | Significado    |
| -------- | -------------- |
| `and`    | E lógico       |
| `or`     | OU lógico      |
| `not`    | Negação lógica |

**Operadores relacionais:**

|Operador|Significado|
|---|---|
|`<`|menor que|
|`>`|maior que|
|`<=`|menor ou igual|
|`>=`|maior ou igual|
|`==`|igual|
|`!=`|diferente|

#### Identificadores e Atribuição
- Um _identificador_ é o nome de uma variável.
- Deve começar com letra ou `_`, pode ter letras, dígitos e `_`, e é _case-sensitive_. 
- A _atribuição_ (`=`) cria e/ou atualiza variáveis.

```python
theSum = 0
theSum = theSum + 1   # Agora vale 1
theSum = True         # Agora aponta para o valor booleano True
```
**Dinamismo**: O tipo de uma variável pode mudar conforme a atribuição.

### Tipos de Dados Coletivos Nativos

####  Listas (`list`)
- Coleções ordenadas de elementos, delimitadas por colchetes: `[ ]`
- Podem conter tipos mistos (heterogêneas).

```python
minhaLista = [1, 3, True, 6.5]
```

| Operação     | Exemplo           | Efeito                      |
| ------------ | ----------------- | --------------------------- |
| indexação    | `lista[2]`        | Acessa item na posição 2    |
| concatenação | `lista1 + lista2` | Junta as listas             |
| repetição    | `[0] * 6`         | Repete o item               |
| pertinência  | `x in lista`      | Verifica se x está na lista |
| comprimento  | `len(lista)`      | Conta quantos itens há      |
| fatiamento   | `lista[1:3]`      | Sublista do índice 1 até 2  |
> [!WARNING]
> Atenção com **repetição de listas**

```python
minhaLista = [1,2,3,4]
A = [minhaLista]*3
minhaLista[2] = 45
print(A)  # Todas as sublistas apontam para a mesma lista
```
##### Métodos de Lista:
|Método|Uso|Descrição|
|---|---|---|
|`append(item)`|`lista.append(5)`|Adiciona item ao final|
|`insert(i, item)`|`lista.insert(2, "abc")`|Insere item na posição i|
|`pop()`|`lista.pop()`|Remove e retorna o último item|
|`pop(i)`|`lista.pop(2)`|Remove e retorna item da posição i|
|`sort()`|`lista.sort()`|Ordena a lista|
|`reverse()`|`lista.reverse()`|Inverte a ordem dos itens|
|`index(item)`|`lista.index(3)`|Retorna o índice da 1ª ocorrência do item|
|`count(item)`|`lista.count(3)`|Conta quantas vezes o item aparece|
|`remove(item)`|`lista.remove(3)`|Remove a 1ª ocorrência do item|
|`del lista[i]`|`del lista[0]`|Apaga item na posição i|
```python
minhaLista = [1024, 3, True, 6.5]
minhaLista.append(False)
minhaLista.insert(2, 4.5)
print(minhaLista.pop())     # Remove o último (False)
print(minhaLista.pop(1))    # Remove o item na posição 1
minhaLista.sort()           # Ordena (caso possível entre tipos)
minhaLista.reverse()        # Inverte a ordem
print(minhaLista.count(6.5))
print(minhaLista.index(4.5))
minhaLista.remove(6.5)
del minhaLista[0]
```

### Strings, Tuplas, Conjuntos e Dicionários
Além das listas, Python possui outros tipos de coleções com finalidades e comportamentos distintos. Vamos explorar cada um deles.

#### Strings
Strings são **sequências imutáveis** de caracteres. Podem ser definidas com aspas simples (`'texto'`) ou duplas (`"texto"`). Como são sequências, todas as operações mostradas anteriormente (indexação, fatiamento, concatenação, etc.) se aplicam.

```python
s = 'Olá mundo!'
print(s[0])       # Acesso ao primeiro caractere
print(s[4:])      # Fatiamento a partir do índice 4
print(s + '!!!')  # Concatenação
print('mundo' in s)  # Pertinência
```
#### Tuplas
Tuplas são semelhantes às listas, mas **imutáveis**. Uma vez criada, seu conteúdo **não pode ser alterado**.   
São muito usadas para representar **registros** ou **valores fixos**.
Tuplas são ideais quando os dados **não devem ser modificados** por **engano**.

```python
t = (1, 2, 3)
print(t[0])
# t[0] = 4  # Isso causaria um erro
```

#### Conjuntos
Conjuntos (`set`) são coleções não ordenadas de elementos únicos. São úteis para operações de união, interseção e diferença.

```python
A = {1, 2, 3}
B = {3, 4, 5}
print(A | B)  # União
print(A & B)  # Interseção
print(A - B)  # Diferença
```

#### Dicionários
Dicionários (`dict`) são coleções de pares chave-valor. São extremamente úteis para representar **associações**. 

```python
meu_dict = {'nome': 'João', 'idade': 25}
print(meu_dict['nome'])        # Acesso ao valor pela chave
meu_dict['idade'] = 26         # Atualização do valor
meu_dict['email'] = 'joao@email.com'  # Adição de novo par
print(meu_dict)
```

Você pode iterar sobre chaves, valores ou ambos:

```python
for chave, valor in meu_dict.items():
    print(chave, valor)
```

### Conversão entre Tipos
Python permite converter entre tipos de dados usando funções de conversão nativas:
```python
int('123')     # Converte string para inteiro
float('3.14')  # Converte string para ponto flutuante
str(100)       # Converte inteiro para string
list('abc')    # Converte string para lista de caracteres
tuple([1, 2])  # Converte lista para tupla
set([1, 1, 2]) # Converte lista para conjunto (eliminando duplicatas)
```

### Entrada de Dados
A função `input()` é usada para **capturar entrada** do usuário. 
Por padrão, ela retorna uma **string**.

```python
nome = input("Digite seu nome: ")
idade = int(input("Digite sua idade: "))
print(f"Olá, {nome}. Você tem {idade} anos.")
```

### Saída de Dados
Além do básico `print()`, Python permite formatação de saída com `f-strings` (Python 3.6+):

```python
x = 3.14159
print(f"O valor de pi é aproximadamente {x:.2f}")
```

## Entrada e Saída
### Função `input`
- Permite solicitar dados ao usuário via terminal.
- Recebe uma string (prompt) como parâmetro:

```python
umNome = input('Por favor digite o seu nome: ')
```

- Retorna sempre uma **string**.
- Para converter para outros tipos:
```python
raio = float(input("Digite o raio do círculo: "))
``` 

```python
umNome = input('Digite seu nome: ')
print("Seu nome em maiúsculas é", umNome.upper(), "e tem comprimento", len(umNome))
```

### Formatação
Argumentos separados por vírgula:

```python
print("Olá", "Mundo")              # Olá Mundo
print("Olá", "Mundo", sep="***")   # Olá***Mundo
print("Olá", "Mundo", end="***")   # Olá Mundo***
```

Strings de Formatação com `%`
- Usada para controle preciso da saída:

```python
print("%s tem %d anos de idade." % (umNome, anos))
```

Caractere de Conversão (`%`)

| Código   | Tipo de dado                 |
| -------- | ---------------------------- |
| `d`, `i` | Inteiros                     |
| `u`      | Inteiro sem sinal            |
| `f`      | Float (ex: 3.14)             |
| `e`, `E` | Float em notação científica  |
| `g`      | Float com notação adaptativa |
| `c`      | Caractere único              |
| `s`      | String ou objeto convertível |
| `%`      | Insere caractere % literal   |

Modificadores de Formato

| Modificador | Exemplo    | Descrição                            |
| ----------- | ---------- | ------------------------------------ |
| número      | `%10d`     | Campo de 10 caracteres               |
| `-`         | `%-10d`    | Alinhamento à esquerda               |
| `+`         | `%+10d`    | Alinhamento à direita com sinal      |
| `0`         | `%010d`    | Zeros à esquerda                     |
| `.`         | `%10.2f`   | Precisão decimal                     |
| `(nome)`    | `%(nome)d` | Substituição com chave de dicionário |

```python
preço = 24
item = "banana"

print("O preço do kilo de %s é %d reais" % (item, preço))
# O preço do kilo de banana é 24 reais

print("O preço do kilo de %+10s é %10.2f reais" % (item, preço))
# O preço do kilo de     banana é      24.00 reais

dicio = {"item": "banana", "preço": 24}
print("O preço do kilo de %(item)s é %(preço)7.1f reais" % dicio)
# O preço do kilo de banana é    24.0 reais
```

Método `format()` (Alternativa Moderna)
- Python também oferece `str.format()` e f-strings para formatações mais avançadas.

```python
print("O preço do kilo de {} é {:.2f} reais".format(item, preço))
```

## Estruturas de Controle
Algoritmos exigem **estrutura de decisão (seleção)** e **estrutura de repetição (iteração)**. Python oferece recursos simples e poderosos para ambas.

### Estrutura de Repetição
#### `while`
- A instrução `while` repete um bloco de código **enquanto** uma condição for verdadeira.
- A **condição é testada antes** de cada repetição.

```python
>>> contador = 1
>>> while contador <= 5:
...     print("Olá, mundo")
...     contador = contador + 1

Olá, mundo
Olá, mundo
Olá, mundo
Olá, mundo
Olá, mundo
```

> [!NOTE]
**Importante:** O Python **exige identação** correta (normalmente 4 espaços) para definir o bloco dentro do `while`.

##### Condição Composta
- Pode-se usar operadores lógicos para combinar várias condições
```python
while contador <= 10 and not acabou:
    # executa se contador <= 10 e acabou for False
    ...
```

#### `for`
- Itera sobre **qualquer coleção iterável** (listas, strings, tuplas, dicionários, etc.).
```python
>>> for item in [1,3,6,2,5]:
...    print(item)
...
1
3
6
2
5
```

```python
lista_palavras = ['gato','rato','coelho']
lista_letras = [ ]
for palavra in lista_palavras:
    for letra in palavra:
        lista_letras.append(letra)
print(lista_letras)
```

##### Iteração com `range()`
- A função `range()` gera uma sequência de números.
- Pode receber 1, 2 ou 3 argumentos: `range(fim)`, `range(início, fim)`, `range(início, fim, passo)`

```python
for i in range(5):        # 0 a 4
    print(i)

for i in range(1, 6):     # 1 a 5
    print(i)

for i in range(10, 0, -2): # 10, 8, ..., 2
    print(i)
```

```python
>>> for item in range(5):
...    print(item**2)
...
0
1
4
9
16
>>>
```
### Estrutura de Decisão: `if`, `elif`, `else`
Usada para tomar decisões com base em condições booleanas.

```python
if n<0:
   print("Desculpe, o valor é negativo")
else:
   print(math.sqrt(n))
```

#### Operadores em Condições
Você pode usar todos os **operadores relacionais** e **lógicos** vistos anteriormente:

|Operador|Significado|
|---|---|
|`<`|menor que|
|`<=`|menor ou igual|
|`>`|maior que|
|`>=`|maior ou igual|
|`==`|igual|
|`!=`|diferente|
|`and`|E lógico|
|`or`|OU lógico|
|`not`|negação lógica|

```python
if nota >= 90:
   print('A')
else:
   if nota >=80:
      print('B')
   else:
      if nota >= 70:
         print('C')
      else:
         if nota >= 60:
            print('D')
         else:
            print('F')
```

```python
if nota >= 90:
   print('A')
elif nota >=80:
   print('B')
elif nota >= 70:
   print('C')
elif nota >= 60:
   print('D')
else:
   print('F')
```

```python
idade = 20
if idade >= 18 and idade < 65:
    print("Adulto")
```

> [!note]
> **Boas Práticas**
> - Sempre **identar corretamente** os blocos de código.
> - Evite loops infinitos com `while`; garanta que a condição mude em algum momento.
> - Use `for` quando souber **quantas vezes iterar** ou tiver uma **coleção**

#### Comandos Úteis em Laços

| Comando    | Descrição                                  |
| ---------- | ------------------------------------------ |
| `break`    | Encerra o laço imediatamente               |
| `continue` | Pula para a próxima iteração do laço       |
| `pass`     | Não faz nada (usado como espaço reservado) |

```python
>>> for i in range(10):
...    if i == 3:
...        continue  # Pula o 3
...    if i == 7:
...        break     # Encerra o laço
...    print(i)
0
1
2
4
5
6
>>>
```

#### Preenchimento de Lista (_List Comprehension_)
Uma forma alternativa e mais concisa de criar listas em Python é usando o **preenchimento de lista** (_list comprehension_). Essa técnica permite construir listas a partir de iterações e seleções em uma única linha de código.

```python
>>> quadrados=[]
>>> for x in range(1,11):
         quadrados.append(x*x)

>>> quadrados
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
>>>
```

```python
>>> quadrados=[x*x for x in range(1,11)]
>>> quadrados
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
>>>
```

```python
>>> quadrados=[x*x for x in range(1,11) if x%2 != 0]
>>> quadrados
[1, 9, 25, 49, 81]
>>>
```

```python
>>>[c.upper() for c in 'preenchimento' if c not in 'aeiou']
['P', 'R', 'N', 'C', 'H', 'M', 'N', 'T']
>>>
```

## Tratamento de Exceções
### Tipos de Erros 
**1.Erro de Sintaxe**:
- Erro na estrutura do código (ex.: esquecer : em for i in range(10)).
- Impede o **interpretador** Python de processar a instrução.
- Mais comum em iniciantes aprendendo a linguagem.

```python
>>> for i in range(10)
SyntaxError: invalid syntax (<pyshell#61>, line 1)
```

**2.Erro Lógico**:
- Programa executa, mas o resultado está errado (falha no algoritmo ou na implementação).
- Pode causar **exceções** (erros em tempo de execução), como divisão por zero ou acesso a índices inválidos em listas.
### Exceções
Erros em **tempo de execução** que podem **encerrar o programa** se não forem tratados.  
**Tratamento com `try/except`**:
- Usado para capturar exceções e evitar a interrupção do programa.
- *Exemplo:* Se num for negativo, captura ValueError e usa o valor absoluto para continuar.
```python
try:
    print(math.sqrt(num))
except:
    print("Valor impróprio para raiz quadrada")
    print("Usando valor absoluto")
    print(math.sqrt(abs(num)))
```

**Levantando Exceções**:
- Usa-se raise para criar exceções personalizadas.
- Permite ao programador sinalizar erros específicos com mensagens customizadas.
```python
if num < 0:
    raise RuntimeError("Você não pode usar um valor negativo")
else:
    print(math.sqrt(num))
```

## Funções
### Definição de Função
- Funções permitem **esconder os detalhes** da computação e **organizar o código**
- Uma função em Python é definida com `def`, seguida pelo **nome**, **parâmetros** e **corpo**.
- Pode **retornar valores** com a instrução `return`.

```python
def quadrado(n):
    return n**2
>>> quadrado(3)
9
>>> quadrado(quadrado(3))
81
```

### Abstração
- Ao usar funções, não é necessário conhecer a **implementação interna**, apenas o que a função **recebe e retorna**.
- Exemplo: `sqrt` da biblioteca `math` esconde os cálculos internos da raiz quadrada.
### Método de Newton (para raiz quadrada)
- Técnica **iterativa** para calcular raiz quadrada aproximada.
- Fórmula:
$$ nova\_raiz = \frac{1}{2} \left( \text{raiz\_anterior} + \frac{n}{\text{raiz\_anterior}} \right) $$
- Palpite inicial: `n/2`.
- Repete 20 vezes até obter uma aproximação.

```python
def raiz_quadrada(n):
    raiz = n / 2  # chute inicial
    for k in range(20):
        raiz = (1/2) * (raiz + (n / raiz))
    return raiz
>>> raiz_quadrada(9)
3.0
>>> raiz_quadrada(4563)
67.549981495186216
```

## Programação Orientada a Objetos em Python: Definindo Classes