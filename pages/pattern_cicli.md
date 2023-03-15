# Pattern elementari per la scansione di sequenze o collezioni

Un _pattern_ (uno "schema") può essere definito come _"una soluzione progettuale generale ad un problema ricorrente"_ [3].

Un _pattern elementare_ è un pattern adatto ai novizi per aiutarli ad apprendere concetti fondamentali di programmazione [4].

Gli studenti, tramite la lettura, il tracciamento, il completamento, o la risoluzione di svariate istanze di diversi e variegati problemi accomunati da uno schema risolutivo comune, possono imparare questi pattern e applicarli poi in contesti nuovi ma risolubili con lo stesso schema di soluzione.

Non si tratta tanto di insegnare il pattern in astratto, quanto di farlo osservare (e "nominarlo") esplicitamente in istanze concrete di sua applicazione.

## Scansioni lineari

Si tratta di scansioni in cui processiamo *tutti* gli elementi di una collezione, avendo modo di sapere a priori (possibilmente in tempo costante) quanti elementi ci sono o quando siamo arrivati alla fine.

Dunque possono essere utilizzati su collezioni iterabili (es. `for e in s: print(e)`) o su collezioni indicizzabili (es. `for i in range(len(s)): print(s[i])`

### Scansione lineare *semplice*
Si tratta di scansioni in cui le singole iterazioni forniscono parti del risultato.

Con iteratore
```
per (ogni) e in c:
   processa e
```

Con indici
```
per i che varia tra i valori estremi degli indici di c: # (es tra 0 e len(c))
   processa c[i]
   incrementa o decrementa i
```

Con indici e while
```
i = uno dei valori estremi di c
finché i minore di uno dei valori estremi degli indici di c: # (es tra 0 e len(c))
   processa c[i]
   incrementa o decrementa i
```

_Esempio._ Scrivere una funzione che _stampa a video_, su linee separate, tutti gli elementi di una collezione


```python
#con iteratore
def stampa_it(c):
  for e in c:
    print(e)

l = [1, 3, 5]
stampa_it(l)
t = ('M', 'F', 'X')
stampa_it(t)
d = {'Michael', 'Stefano', 'Simone', 'Elisa'}
stampa_it(d) #notare che non è ordinato ma posso enumerarlo e quindi iterarlo

#con indice
def stampa_in(c):
  for i in range(len(c)):
    print(c[i])

stampa_in(l)
stampa_in(t)
#stampa_in(d) #insiemi non sono ordinati e non indicizzabili
```

_Esempio._ Scrivere una funzione che _stampa a video_, su linee separate, **le lettere** di una stringa passata come parametro in ordine inverso.




```python
def inversione(s):
  for i in range(len(s), 0, -1): # i varia tra len(s) (compreso) e 0 (escluso): [len(s), 0[
    print(s[i-1]) #mentre gli indici del vettore variano tra ]len(s), 0], per questo devo fare i-1

inversione('ciao')
```

_Esempio._ Scrivere una funzione Python che *stampa a video*, su linee separate, **le vocali** di una stringa passata come parametro.


```python
def stampa_vocale(s):
  vocali = 'aeiouAEIOU'
  for l in s:
    if l in vocali:
      print(l)

stampa_vocale('ciao')
```

Python permette di iterare sugli elementi di una stringa con il costrutto for (`for c in s`). 
In alternativa possiamo accedere a ciascun carattere con il suo indice


```python
def stampa_vocale(s):
  vocali = 'aeiouAEIOU'
  for i in range(len(s)): #range(len(s)) indica [0, len(s)[
    if s[i] in vocali:
      print(s[i])

stampa_vocale('ciao')
```

### Scansione lineare con accumulo
Si tratta di una scansione in cui iterare serve a preparare approssimazioni successive del risultato.



```
accumulatore = elemento neutro #(es. 0 se somma, 1 se prodotto, collezione vuota se collezione, stringa vuota, True o False...)
per ogni e in c:
   se e soddisfa un requisito: #(potrebbe anche non servire)
      accumulatore += valore da accumulare
output di accumulatore
```

(Banale costruire la versione con indici, lavorando su ``c[i]`` invece che su ``e``)



_Esempio._ Scrivere una funzione che **restituisce la lunghezza di una sequenza**, senza utilizzare il metodo _built-in_ di Python `len()`.




```python
def lunghezza(seq):
  accumulatore = 0 # perchè inizializziamo a 0? perché non dovremmo? -ml
  for e in seq:
    accumulatore += 1
  return accumulatore

print(lunghezza('ciao'))
```

_Esempio._ Scrivere una funzione che _stampa a video_ **il numero di vocali** di una stringa passata come parametro.


```python
def stampa_n_vocali(s):
  vocali = 'aeiouAEIOU' # si potrebbe voler considerare anche le vocali accentate
  n_vocali = 0
  for l in s:
    if l in vocali:
      n_vocali += 1
  print('Ci sono ' + str(n_vocali) + ' vocali nella stringa ' + s)

stampa_n_vocali('ciao')
```

_Esempio._ Scrivere una funzione Python che *restituisce* **una stringa contenente le vocali** di una stringa passata come parametro.


```python
def vocali(s):
  vocali='aeiouAEIOU'
  vocali_in_s = ''
  for lettera in s:
    if lettera in vocali:
      vocali_in_s = vocali_in_s + lettera
  return vocali_in_s

print(vocali('ciao'))
```

## Ricerca Lineare

### Ricerca lineare certa

Cerchiamo un elemento ``e`` (per esempio in una successione di numeri, oppure in una sequenza o collezione ``c``) che soddisfa un certo requisito. Ci fermiamo quando lo troviamo.

Con iteratore
```
per (ogni) e in c:
   se e soddisfa il requisito:
      azione in caso di ritrovamento
      esci dal ciclo
```
Con indici
```
per i tra gli indici estremi di c:
  se c[i] soddisfa il requisito:
     azione in caso di ritrovamento
     esci dal ciclo
  incrementa i  
```
Con while
```
i = 0
finché i < lunghezza(c):
   se c[i] soddisfa il requisito:
     azione in caso di ritrovamento
     esci dal ciclo
   incrementa i
```
Con while, unendo le condizioni
```
i = 0
finché i < lunghezza(c) e c[i] non soddisfa il requisito:
   incrementa i
azione in caso di ritrovamento
```
Per quest'ultimo caso, si assume che il linguaggio di programmazione usi la valutazione lazy ("a corto circuito") delle espressioni booleane: es. se il primo degli operandi di un AND è falso, non si valuta il secondo (e si restituisce False); allo stesso modo se il primo degli operandi di un OR è vero, non si valuta il secondo (e si restituisce True).
Senza questa assuzione, nel caso in cui ``i == lunghezza(c)``, continuando a valutare l'espressione nel "finché", si prova ad accedere a ``c[i]``, che sarà fuori dal range della collezione (i cui indici vadano da ``0`` a ``lunghezza(c)-1``)


_Esempio._ Definire una funzione Python che **restituisce ``True`` se un elemento** (fornito come parametro) **si trova in una collezione** (fornita come parametro). Servirsi di un ciclo che processa gli elementi della collezione, fornendo una strategia per l'uscita dal ciclo nel caso l'elemento obiettivo della ricerca venga trovato prima del termine della scansione.


```python
def ricerca_lineare(elem , seq):
  for e in seq:
    if e == elem:
      return True
```

### Ricerca lineare incerta

Cerchiamo un elemento ``e`` (per esempio in una successione di numeri, oppure in una sequenza o collezione ``c``) che soddisfa un certo requisito. Dobbiamo gestire il caso particolare in cui l'elemento non sia presente.



Con iteratore
```
per (ogni) e in c:
   se e soddisfa il requisito: 
      azione in caso di ritrovamento
      esci dal ciclo
azione in caso di *mancato* ritrovamento
```
Con indici
```
per i tra gli indici estremi di c:
  se c[i] soddisfa il requisito:
     azione in caso di ritrovamento
     esci dal ciclo
  incrementa i
azione in caso di *mancato* ritrovamento
```
Con while
```
i = 0
finché i < lunghezza(c):
   se c[i] soddisfa il requisito:
     azione in caso di ritrovamento
     esci dal ciclo
   incrementa i
azione in caso di *mancato* ritrovamento
```
Con while, unendo le condizioni
```
i = 0
finché i < lunghezza(c) e c[i] non soddisfa il requisito:
   incrementa i
se i != lunghezza(c): 
   azione in caso di ritrovamento
altrimenti:
   azione in caso di *mancato* ritrovamento
```
NB: Si assume la valutazione "lazy"...



_Esempio._ Modificare la soluzione precedente in modo da gestire il caso in cui l'obiettivo della ricerca **non venga trovato** nella collezione, trattandolo come un caso particolare.


```python
def ricerca_lineare(elem, seq):
  for e in seq:
    if e == elem:
      return True
  return False
```

Analogamente, una possibile soluzione che utilizza il costrutto `while` sarà così definita:


```python
def ricerca_lineare_while(elem, seq):
  i = 0
  while i < len(seq):
    if seq[i] == elem:
      return True
    i += 1
  return False
```

O, più compattamente:


```python
def ricerca_lineare_while(elem, seq):
  i = 0
  while i < len(seq) and seq[i] != elem:
    i += 1
  return i != len(seq)
```

_Esempio._ Scrivere una funzione che restituisce ``True`` se il numero ``n`` passato come parametro è **primo**, e ``False`` altrimenti. 
Si tratta dell'algoritmo "ovvio", e corrisponde alla ricerca di un divisore per ``n`` tra i numeri minori di ``n``. 


```python
def primo(n): #supponiamo n>1
  for i in range(2,n): #in realtà basta arrivare a sqrt(n)
    if n % i == 0: # n è divisibile per i
      return False #trovato un divisore diverso da 1 e se stesso
  return True #non ho trovato divisori
```

## Scansioni e ricerche "interattive"

In questi casi la lunghezza della collezione non è conosciuta a priori, e l'utente fornisce gli elementi uno alla volta

### Scansione lineare (semplice o con accumulo) fino all'arrivo di una sentinella

Vogliamo leggere e processare tutti i valori inseriti uno alla volta dall'utente, finché non viene inserito uno specifico valore, che chiamiamo _sentinella_.



```
leggi valore
finché valore != sentinella:
  processa valore
  leggi valore
```



_Esempio._ Scrivere un programma che richiede in input i voti (da 1 a 10) di uno studente, li stampa (scansione semplice), li somma (scansione con accumulo) e termina quando l'utente inserisce il numero 0.


```python
somma = 0
voto = int(input("Inserisci un voto (intero, da 1 a 10): "))
while voto!= 0:
  print(voto)
  somma += voto
  voto = int(input("Inserisci un voto (intero, da 1 a 10): "))
```

### Lettura in input fino a che non si riceve il valore desiderato

Chiedo in input all'utente un valore con specifici vincoli e lo richiedo finché non ottengo un valore "valido".


```
leggi valore
finché valore non valido:
  stampa "Non valido"
  leggi valore
```



_Esempio._ Scrivere un programma che chiede all'utente di inserire un voto. Il programma verifica che sia compreso tra 1 e 10 (estremi inclusi): se non lo è, richiede nuovamente l'inserimento e continua così finché non viene inserito un voto "valido".


```python
  voto = float(input("Inserisci un voto (da 1 a 10): "))
  while (voto < 1 or voto > 10):
    print("Il voto deve essere compreso tra 1 e 10")
    voto = float(input("Inserisci un voto (da 1 a 10): "))
```

#### Alternative
Se non si vuole duplicare il codice dell'input, al posto della prima lettura (quella fuori dal while) si può assegnare a ``valore`` un valore sicuramente non valido (es. ``voto = 0`` nell'ultimo esempio; adattabile anche al penultimo), di modo che il ciclo ``while`` venga eseguito sicuramente almeno la prima volta. 
Nei linguaggi che lo permettono (non Python) è possibile in alternativa usare il costrutto ``do... while``.

Un'altra possibilità è quella di usare le eccezioni.

_Esempio._ Scrivere un programma che chiede all'utente di inserire un intero, e continua a chiederlo finché non lo ottiene.


```python
x = None
while x is None:
    try:
        x = int(input('Dammi un intero: '))
    except ValueError:
        print('Volevo un intero, e tu non me lo hai dato.')
print("Grazie di avermi dato l'intero", x)
```


# Esercizio
* Per ogni pattern, individuare un esempio (diverso da quelli già presentati e possibilmente non troppo ovvio) di applicazione del pattern, e scrivere il codice Python corrispondente.

# Riferimenti Bibliografici
1. [Owen Astrachan & Eugene Wallingford - Loop Patterns](http://www.cs.uni.edu/~wallingf/patterns/loops.html)
2. [Philip Guo - Python Tutor](http://pythontutor.com/visualize.html)
3. [Wikipdia - Design pattern](https://it.wikipedia.org/wiki/Design_pattern)
4. [Michael J. Clancy and Marcia C. Linn. 1999. Patterns and pedagogy. SIGCSE Bull. 31, 1](https://doi.org/10.1145/384266.299673)

*Grazie a Simone Martini e Stefano Pio Zingaro per i contributi al miglioramento di questa pagina*
