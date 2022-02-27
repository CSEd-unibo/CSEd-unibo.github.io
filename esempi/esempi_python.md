## Alcuni esempi didattici in python

Questa pagina contiene alcuni esempi didattici di codice Python

### Divisori
Esempio sui divisori. Il primo programma ha uno stile Pascal o C:
```python
#!/usr/bin/env python3

def divisori(x):
    s=[]
    for i in range(2,x):
        if x%i == 0:
            s.append(i)
    return s;

def primo(x):
    if divisori(x):
        return False
    else:
        return True

def divisoriprimi(x):
    s=[]
    for i in divisori(x):
        if (primo(i)):
            s.append(i)
    return s

if __name__ == '__main__':
    n=int(input("dammi n "))
    if primo(n):
        print(n ,"è primo")
    else:
        print("i divisori di ", n, "sono", divisori(n))
        print("i divisori primi di ", n, "sono", divisoriprimi(n))
```

Ma il Python ha anche il tipo insieme (set) che è meglio indicato per questo esempio:

```python
#!/usr/bin/env python3

def divisori(x):
    s=set()
    for i in range(2,x):
        if x%i == 0:
            s.add(i)
    return s;

def primo(x):
    if divisori(x):
        return False
    else:
        return True

def divisoriprimi(x):
    s=set()
    for i in divisori(x):
        if (primo(i)):
            s.add(i)
    return s

if __name__ == '__main__':
    n=int(input("dammi n "))
    if primo(n):
        print(n ,"è primo")
    else:
        print("i divisori di ", n, "sono", divisori(n))
        print("i divisori primi di ", n, "sono", divisoriprimi(n))
```

Lo stesso esempio con la Set Comprehension (come si traduce? si traduce?):

```python
#!/usr/bin/env python3

def divisori(x):
    return {y for y in range(2,x) if x%y == 0}

def primo(x):
    return not divisori(x)

def divisoriprimi(x):
    return {y for y in divisori(x) if primo(y)}

if __name__ == '__main__':
    n=int(input("dammi n "))
    if primo(n):
        print(n ,"è primo")
    else:
        print("i divisori di ", n, "sono", divisori(n))
        print("i divisori primi di ", n, "sono", divisoriprimi(n))
```

Il primo è più ''algoritmico, passo a passo'', ma anche più contorto. Il secondo è più elegante ma può apparire ''magico-misterioso''.

### Fattorizzazione, mcm e MCD

Il metodo migliore per calcolare il massimo comun divisore è l'algoritmo di Euclide:
```python
def gcd(x, y):
  while True:
    if x < y:
      x, y = y, x
    x -= y
    if x == 0:
      return y

def lcm(x, y):
  return x * y // gcd(x, y)
```

### Coda/Pila e programmazione a oggetti

Le code e le pile (queue e stack) possono essere implementate a partire dalle liste. Le funzioni enqueue/dequeue per le code e push/pop per le pile possono essere implementate cosi':
```python
def enqueue(s,x):
    s.append(x)

def dequeue(s):
    return s.pop(0)

def push(s,x):
    s.append(x)

def pop(s):
    return s.pop()
```

Passando alla programmazione a oggetti,
la versione migliore è quella con un attributo nascosto "lista", perché una coda ''ha'' una lista, non ''&egrave; '' una lista
```python
class queue:
    def __init__(self):
        self._list=[]

    def enqueue(self, x):
        self._list.append(x)

    def dequeue(self):
        return self._list.pop(0)

    def empty(self):
        return not self._list

    def head(self):
        return self._list[0]

    def __str__(self):
        return str(self._list)

class stack:
    def __init__(self):
        self._list=[]

    def push(self, x):
        self._list.append(x)

    def pop(self):
        return self._list.pop()

    def empty(self):
        return not self._list

    def __str__(self):
        return str(self._list)
```

### Il setaccio di Eratostene

Ai miei tempi si chiamava ''crivello''!

Può essere interessante per introdurre gli insiemi in Python. La definizione appare naturale e descrittiva.
```python
def sieve(n):
    sv={x for x in range(1,n)}
    for i in range(2,n//2):
        if i in sv:
            sv -= {x for x in range(2*i,n,i)}
    return [x for x in range(n) if x in sv]
```

### Ordinamento

Ecco una carrellata di funzioni per l'ordinamento...
Le prime sono funzioni per l'ordinamento di vettori/liste sul posto, modificando la sequenza degli elementi.

Sort per selezione:
```python
def selection_sort(v):
    for i in range(len(v)):
        for j in range(i+1,len(v)):
            if v[j] < v[i]:
                v[i],v[j]=v[j],v[i]
```

Sort per inserzione:
```python
def insertion_sort(v):
    for i in range(1,len(v)):
        for j in range(i):
            if v[j] > v[i]:
                v.insert(j, v.pop(i))
```

Bubblesort:
```python
def bubblesort(v):
    for i in range(1,len(v)):
        for j in range(len(v)-i):
            if v[j+1] < v[j]:
                v[j+1],v[j]=v[j],v[j+1]
```

Una implementazione del quicksort molto compatta e elegante si ottiene con la List Comprehension (copia il vettore come il metodo standard ''sorted''):
```python
def rqsorted(v):
    if v:
        pivot=v[0]
        lesser=[x for x in v[1:] if x <= pivot]
        greater=[x for x in v[1:] if x > pivot]
        return rqsorted(lesser) + [pivot] + rqsorted(greater)
    else:
        return []
```

Il mergesort è un po' più macchinoso. La prima versione prevede l'ordinamento del vettore stesso, vengono copiati temporaneamente i vettori parziali e poi le sequenze vengono reinserite nel vettore originale:
```python
def merge(v1,v2):
    v=[]
    while True:
        if not v1:
            return v+v2
        elif not v2:
            return v+v1
        else:
            if v1[0] < v2[0]:
                v.append(v1.pop(0))
            else:
                v.append(v2.pop(0))

def mergesort(v):
    lv=len(v)
    ls=1;
    while v[ls:]:
        for i in range(0,lv,2*ls):
            v[i:i+2*ls]=merge(v[i:i+ls],v[i+ls:i+2*ls])
        ls *= 2
```

La seconda versione del mergesort copia il vettore. Anche la funzione rmerge è ricorsiva.
```python
def rmerge(v1,v2):
    if not v1:
        return v2
    elif not v2:
        return v1
    elif v1[0] < v2[0]:
        return v1[0:1]+rmerge(v1[1:],v2)
    else:
        return v2[0:1]+rmerge(v1,v2[1:])

def rmergesorted(v):
    half=len(v)//2
    if half == 0:
        return v
    else:
        return rmerge(rmergesorted(v[:half]),rmergesorted(v[half:]))
```
Le definizioni delle funzioni ''merge'' e ''rmerge'' non sono state inserite nella definizione delle funzioni ''mergesort'' e ''rmergesorted'' (rispettivamente) perché hanno una funzionalità specifica di fusione di vettori ordinati e possono essere usate anche indipendentemente dal mergesort.

