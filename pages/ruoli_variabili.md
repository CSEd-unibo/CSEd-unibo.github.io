# Ruoli delle variabili

<!-- Gli studi sui ruoli delle variabili sono di [omissis...]. Questa pagina è ispirata al materiale presente [qui](). -->

I ruoli delle variabili sono usi tipici dei che le variabili hanno nei programmi.

Secondo i ricercatori che li propongono, i seguenti ruoli coprono il 99% dei programmi semplici. <!--[].-->

Non suggeriamo di insegnare i ruoli in astratto, quanto di farli osservare (e nominarli) esplicitamente quando si incontrano istanze concrete della loro applicazione.
<!--Maggiori informazioni sull'uso dei ruoli può essere trovato [qui]().-->

*NB: svolgere gli esercizi di completamento solo dopo aver letto tutti i ruoli.*

## Valore fissato
Una variabile assume il ruolo di "valore fissato" se il suo valore non viene modificato a runtime, **dopo l'inizializzazione**. 

```python3
pigreco = 3.14
r = float(input("Inserisci il raggio:"))
vol = (4/3)*pigreco*(r**3)
print("Il volume della sfera è", vol)
```

Sia la variabile ```pigreco``` che ```r``` sono dei **valori fissati**
La variabile ```vol``` è  _______________
Cosa fa il programma? ________________

## Contatore o Indice

Il contatore/indice serve per scorreere una succesisone di vaori in modo sistematico. Può anche essere usato per contare o come indice di un array/lista.

```python3
n = int(input("Di che numero vuoi la tabellina?:"))
fattore = 0
while fattore<11:
    print(n,"x",fattore,"=",n*fattore)
    fattore += 1
```
La variabile ```fattore``` è un contatore/indice.
La variabile ```n``` è  _______________
Cosa fa il programma? ________________

## Valore più recente

Una variabile è un **valore più recente** se contiene il più recente valore che posseggo di una certa sequenza o input.

```python3
voto = float(input("Inserisci un voto (da 1 a 10): "))
while (voto < 1 or voto > 10):
    print("Il voto deve essere compreso tra 1 e 10")
    voto = float(input("Inserisci un voto (da 1 a 10): "))
print(voto)
```

La variabile ```voto``` è un **valore più recente**.
Cosa fa il programma? ________________

## Valore più desiderato

Si tratta del "miglior" valore che ho trovato fino a questo momento.

```python3
L = [3, 1, 4, 10, 2, 7]
massimo = L[0]
for e in L[1:]:
    if e > massimo:
        massimo = e
print("Massimo: ", massimo)
```

La variabile ```massimo``` è un **valore più desiderato**.
La variabile ```L``` è  _______________
La variabile ```e``` è  _______________
Cosa fa il programma? ________________


## Accumulatore
Un accumulatore accumula tutti i valori che ho trovato fino a questo momento. Solitamente, va inizializzato con l'elemento neutro dell'operazione di accumulazione (es. 0 se somma, 1 se prodotto, collezione vuota se collezione, stringa vuota, True o False...).

```python3
s = 0
n = 0
i = int(input("Pioggia caduta: "))
while i != 99999:
    if i >= 0:
        s += i
        n += 1
    i = int(input("Pioggia caduta: "))

if n>0:
    print("Media di pioggia caduta:", s/n)
else:
    print("Nessun dato")
```

La variabile ```s``` è un **accumulatore**.
La variabile ```n``` è  _______________
La variabile ```i``` è  _______________



## Precedente
Una variabile è un *precedente* se contiene il valore di un'altra variabile nel momento in cui quest'ultima assume un nuovo valore (e dunque ricorda il valore precedente di quest'ultima)

```python3
prev_fibo = 0
fibo = 1
conta = 2
while fibo < 4000000:
   c = prev_fibo + fibo
   prev_fibo = fibo
   fibo = c
   conta += 1
print(conta)
```
La variabile ```prev_fibo``` è un **precedente** della variabile ```fibo```
La variabile ```conta``` è ______________
La variabile ```c``` è ______________
Cosa fa il programma? ________________

## Flag unidirezionale

Un flag unidirezionale è un booleano che può essere cambiata una sola volta, dopodiché non può più essere riportata al suo valore originale (è "write once").


```python3
s = "Michael Lodi"
spazio = False
vocali = 0
for c in s:
    if c in "aeiouAEIOU":
        vocali += 1
    elif c == " ":
        spazio = True
print("La stringa", s, "contiene", vocali, "vocali.")
if spazio:
    print("La stringa", s, "contiene almeno uno spazio")
```

La variabile ```spazio``` è un **flag unidirezionale**
La variabile ```vocali``` è  _______________
La variabile ```c``` è  _______________
La variabile ```s``` è  _______________
Cosa fa il programma? ________________

## Temporanea

Una variabile è temporanea se il suo valore è utilizzato soltanto per un breve periodo di tempo [e solo per calcoli intermedi], come ad esempio lo scambio di variabili. Si usa anche per ragioni di efficienza (memorizzare un valore che andrebbe ricalcolato più volte) o per rendere più leggibile un programma.

```python3
M = [[1,2,3],[4,5,6]]
MT = []
r = len(M)
if r != 0:
    c = len(M[0])
    for i in range(c): 
        col = [] 
        for j in range(r): 
            col.append(M[j][i])
        MT.append(col)
print(MT)
```
Le variabili ```r``` e  ```c``` sono variabli **temporanee**
Le variabili ```r``` e  ```c``` sono anche ________________
Le variabili ```MT``` e ```col``` sono _______________
La variabile ```col``` è anche _______________
Le variabili ```i``` e ```j``` sono _______________
Cosa fa il programma? ________________




## Attraversatore

Un attraversatore serve per scorrere gli elementi di una struttura dati (ad esempio in un "foreach")

```python3
class Nodo:
    def __init__(self, valore=None, succ=None):
        self.valore = valore
        self.succ = succ
    def __str__(self):
        return str(self.valore)

LL = Nodo(1, Nodo(2, Nodo(3)))

p = LL
while p is not None:
    print(p, end = " ")
    p = p.succ
print()
```

La variabile ```p``` è un **attraversatore**
La variabile ```LL``` è  _______________
Cosa fa il programma? ________________


Altri ruoli, che non studiamo oggi, sono:

## Organizer
Si tratta sostanzailmente di strutture dati ausiliarie (es. liste)  usate per riorganizzare elementi dopo l'inizializzazione
## Container
Struttura dati ausiliaria in cui gli elementi possono essere aggiunti e rimossi (es. pila)

