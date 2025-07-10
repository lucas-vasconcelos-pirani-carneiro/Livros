# Árvore Binária de Busca

## Implementação
```python []
class No:
    def __init__(self, d):
        self.dado = d
        self.esq = None
        self.dir = None

    def __str__(self):
        return str(self.dado)

class ArvoreBinaria:
    def __init__(self, d):
        self.raiz = No(d)

    def imprimir(self):
         def imprimirRec(no,nivel,lado):
              if no:
                 print(lado,"-"*nivel,no.dado)
                 imprimirRec(no.esq,nivel+1,'E')
                 imprimirRec(no.dir,nivel+1, 'D')
         imprimirRec(self.raiz,0,'R')

class ArvoreBinariaBusca(ArvoreBinaria):
    def __init__(self, d):
        super().__init__(d)
```

### Métodos - Árvore Binária de Busca

I. Inseir um Elemento  

**Recursivo:** 
1. Compara o valor com o nó atual.
2. Se for menor, vai para a subárvore esquerda.
3. Se for maior ou igual, vai para a subárvore direita.
4. Se o ponteiro (`esq` ou `dir`) for `None`, insere o novo nó ali.

```python []
def insereRec(self, d):
    def insereRecIn(atual, d):
        if atual.dado > d:  # Vai para a esquerda
            if atual.esq:
                insereRecIn(atual.esq, d)
            else:
                atual.esq = No(d)
        else:  # Vai para a direita
            if atual.dir:
                insereRecIn(atual.dir, d)
            else:
                atual.dir = No(d)
    
    if self.raiz:
        insereRecIn(self.raiz, d)
    else:
        self.raiz = No(d)
```

**Interativo:**
1. Começa a partir da raiz.
2. Enquanto não inserir:
    - Se for menor, anda para a esquerda.
    - Se for maior ou igual, anda para a direita.
    - Se encontrar posição livre (`None`), insere o novo nó ali.

```python []
def insereIt(self, d):
    if self.raiz:
        atual = self.raiz
        inseriu = False
        while not inseriu:
            if atual.dado > d:  # Esquerda
                if atual.esq:
                    atual = atual.esq
                else:
                    atual.esq = No(d)
                    inseriu = True
            else:  # Direita
                if atual.dir:
                    atual = atual.dir
                else:
                    atual.dir = No(d)
                    inseriu = True
    else:
        self.raiz = No(d)
```

II. Buscar um Elemento
1. Começa a partir da raiz.
2. Se o valor for menor, anda para a esquerda.
3. Se for maior, anda para a direita.
4. Se for igual, retorna o nó.
5. Se encontrar `None`, o valor não está na árvore.

```python []
def busca(self, d):
    atual = self.raiz
    while atual:
        if atual.dado > d:
            atual = atual.esq
        elif atual.dado < d:
            atual = atual.dir
        else:
            return atual  # Encontrado
    return None  # Não encontrado
```

III. Deletar um Elemento
- **Caso 1**: Nó é folha $\rightarrow$ remover diretamente.
- **Caso 2**: Nó tem um filho $\rightarrow$ substituir pelo filho.
- **Caso 3**: Nó tem dois filhos $\rightarrow$ substituir pelo sucessor ou antecessor.


1. Comece procurando o valor na árvore (`dado == d`).
2. Se `d < atual.dado`, vá para a subárvore **esquerda**.
3. Se `d > atual.dado`, vá para a subárvore **direita**.
4. Quando `d == atual.dado`, então:
    - **Caso 1** (sem filhos): retorne `None`.
    - **Caso 2** (um filho): retorne o filho que não é `None`.
    - **Caso 3** (dois filhos):
        - Encontre o menor valor na subárvore direita (**sucessor**).
        - Substitua o valor atual por esse sucessor.
        - Remova recursivamente o sucessor.

```python []
def remove(self, d):
    def removeRec(no, d):
        if not no:
            return None

        if d < no.dado:
            no.esq = removeRec(no.esq, d)
        elif d > no.dado:
            no.dir = removeRec(no.dir, d)
        else:
            # Encontrou o nó a ser removido
            if not no.esq and not no.dir:  # Caso 1: sem filhos
                return None
            elif not no.esq:  # Caso 2: só tem filho à direita
                return no.dir
            elif not no.dir:  # Caso 2: só tem filho à esquerda
                return no.esq
            else:
                # Caso 3: dois filhos
                sucessor = no.dir
                while sucessor.esq:
                    sucessor = sucessor.esq
                no.dado = sucessor.dado  # Copia o valor do sucessor
                no.dir = removeRec(no.dir, sucessor.dado)  # Remove o sucessor
        return no

    self.raiz = removeRec(self.raiz, d)
```

IV. Balanceamento com Lista Ordenada - Método do Vetor

>  - Este é um **método estático de balanceamento** que não depende da estrutura atual da árvore.
> - A ideia é **ordenar os dados** e criar uma nova árvore binária de busca (BST) balanceada a partir deles.

1. Escolha o elemento do **meio da lista** como a **raiz**.
2. Recursivamente:
    - Aplique o mesmo processo **à metade esquerda da lista** para construir a subárvore esquerda.
    - Aplique o mesmo processo **à metade direita da lista** para construir a subárvore direita.
3. O processo termina quando a sublista está vazia (`[]`).

```python
def montaABBB(l):
    def montaABBB_rec(sublista):
        if not sublista:
            return None
        meio = len(sublista) // 2
        raiz = No(sublista[meio])
        raiz.esq = montaABBB_rec(sublista[:meio])
        raiz.dir = montaABBB_rec(sublista[meio + 1:])
        return raiz
    return montaABBB_rec(l)
```
