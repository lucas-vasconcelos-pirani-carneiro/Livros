# Recursão

## O que é recursão?
**Recursão** é um método para resolver problemas que envolve **quebrar** o problema em **subproblemas** cada vez menores até atingir um problema **simples**.  
Envolve uma função que **chama ela mesma**. 

## Exemplo : Soma de uma Lista
Imagine que você queira calcular a soma de uma lista de números tal como: [1,3,5,7,9].

### Forma Interativa
A função usa uma **variável acumuladora** (“soma”) que calcula a somatória de **todos os números da lista** começando com 0 e adicionando cada número da lista.

```python
def somalista(numeros):
    soma = 0
    for i in numeros:
        soma += i
    return soma
```

### Forma Recursiva
Imagina que você não tem comandos de repetição como for ou while. Como somar uma lista de números? Um matemático poderia escrever a soma de uma lista como uma expressão recursiva, usando parênteses de forma aninhada.

**Por exemplo** : $((((1+3)+5)+7)+9)$ ou a versão invertida $(1+(3+(5+(7+9))))$.

Essa ideia pode ser aplicada em Python de forma recursiva. A função somalista(numeros) pode ser escrita de forma que a soma de uma lista seja a **soma do primeiro número** da lista com a **soma do restante da lista**.   
A função chama a si mesma para **processar a parte restante da lista**, até que a lista tenha **apenas um número**, que é o *caso base* e encerra a recursão.

```python
def somalista(numeros):
    if len(numeros) == 1:
        return numeros[0]
    else:
        return numeros[0] + somalista(numeros[1:])
```

**Explicação do Código:**  
- Base case (linha 2): A função verifica se a lista tem apenas **um elemento**. Se sim, retorna esse único número.
- Recursão (linha 5): Se a lista tiver mais de um elemento, a **função chama a si** mesma com a lista **menos o primeiro item** (numeros[1:]), somando esse primeiro elemento ao resultado da chamada recursiva.

Cada chamada recursiva resolve uma parte menor do problema, até que o problema seja simples o suficiente para ser resolvido diretamente. A recursão então "volta" resolvendo as somas até que a soma total seja obtida.

![imagem](./img/cap04-imagem01.png)
![imagem1](./img/cap04-imagem02.png)

## Leis da Recursão
