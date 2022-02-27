# Esercizi di "lettura" di programmi Python

Gli esercizi proposti sono programmi funzionanti.

Come svolgimento dell'esercizio si deve:

* determinare lo scopo del programma
* modificare, migliorare discutere le soluzioni proposta. Proporre soluzioni alternative dello stesso problema.

### 1
```python
def dd(s):
  d,m,y = s.split('.')
  d,m,y = int(d),int(m),int(y)
  md = [0,31,28,31,30,31,30,31,31,30,31,30,31]
  if y % 4 == 0:
    md[2]=29
  dy = d
  for i in range(1,m):
    dy += md[i]
  return dy

if __name__ == "__main__":
  data=input("Dammi una data (es. 14.03.2014): ")
  print("il risultato della funzione misteriosa è ", dd(data))
```

### 2
```python
def imin(l):
  im,mn = 0,l[0]
  for i in range(1,len(l)):
    if l[i]<mn:
      im,mn = i,l[i]
  return im

if __name__ = "__main__":
  l = input('dammi in input una lista di elementi (es: [1,2,3]): ')
  print("l'output della funzione misteriosa è: ", imin(l))
```

### 3
```python
def r13(s):
        e = ''
        for c in s:
                if 'A' <= c <= 'Z':
                        e += chr(((ord(c)-ord('A')) + 13)%26 + ord('A'))
                elif 'a' <= c <= 'z':
                        e += chr(((ord(c)-ord('a')) + 13)%26 + ord('a'))
                else:
                        e += c
        return e

if __name__ == "__main__":
        s = input("scrivi una semplice frase (es: 'Ciao Mondo') ")
        r = r13(s)
        print("il risultato della funzione misteriosa è: ", r)
        print("consiglio: prova a eseguire nuovamente il programma scrivendo")
        print("la frase: ", r)
```

### 4
```python
def pf(n):
        f = []
        for i in range(2,n+1):
                while n % i == 0:
                        f.append(i)
                        n //= i
                if n == 1:
                        break
        return f

if __name__ == "__main__":
        n = int(input("dammi un numero (consigliato da 2 a 1000): "))
        print("il risultato della funzione misteriosa è ", pf(n))
```

### 5
(richiede il modulo turtle)

```python
import turtle
import random

def cy(r):
    turtle.setup(400,400)
    turtle.penup()
    turtle.hideturtle()
    turtle.speed(0)
    for i in range(1000):
        x,y = random.randint(-200,200),random.randint(-200,200)
        if (x*x + y*y)**0.5 < r:
            color = "red"
        else:
            color = "blue"
        turtle.goto(x,y)
        turtle.dot(5,color)

if __name__ == "__main__":
    r = float(input("scrivi un numero (consigliato da 100 a 200): "))
    print("guarda il risultato della funzione misteriosa")
    cy(r)
    turtle.exitonclick()
```

### 6
(richiede il modulo turtle)

```python
import turtle

def poly(n):
        for i in range(n):
                turtle.forward(50)
                turtle.left(360/n)

if __name__=="__main__":
        n=int(input("dammi un intero (consigliato da 3 a 12): "))
        poly(n)
        turtle.exitonclick()
```

### 7
Questo è contorto. Se vi piace... iniziate a preoccuparvi: state diventando informatici ;-)
```python
f="f={0}{1}{0};print(f.format(chr(34),f))";print(f.format(chr(34),f))
```
NB: non è necessario capire questo programma, è solo per chi si vuole cimentare in una sfida...

### 8
```python
def pf(n):
        f=[]
        for i in range(2,n+1):
                while n % i == 0:
                        f.append(i)
                        n //= i
                if n == 1:
                        break
        return f

def fgcd(a,b):
        def rgcd(fa,fb):
                if fa and fb:
                        if fa[0]==fb[0]:
                                return fa[:1]+rgcd(fa[1:],fb[1:])
                        elif fa[0]<fb[0]:
                                return rgcd(fa[1:],fb)
                        else:
                                return rgcd(fa,fb[1:])
                else:
                        return []
        return rgcd(pf(a),pf(b))

def flcm(a,b):
        def rlcm(fa,fb):
                if fa and fb:
                        if fa[0]==fb[0]:
                                return fa[:1]+rlcm(fa[1:],fb[1:])
                        elif fa[0]<fb[0]:
                                return fa[:1]+rlcm(fa[1:],fb)
                        else:
                                return fa[:1]+rlcm(fa,fb[1:])
                else:
                        return fa if fa else fb
        return rlcm(pf(a),pf(b))

def mul(l):
        rv=1
        for el in l:
                rv *= el
        return rv

def gcd(x,y):
        return mul(fgcd(x,y))

def lcm(x,y):
        return mul(flcm(x,y))

if __name__=="__main__":
        a,b=input("Inserisci due numeri (es: 48 36): ").split()
        a,b=int(a),int(b)
        print("pf({})={}".format(a,pf(a)))
        print("pf({})={}".format(b,pf(b)))
        print("fgcd({},{})={}".format(a,b,fgcd(a,b)))
        print("flcm({},{})={}".format(a,b,flcm(a,b)))
        print("gcd({},{})={}".format(a,b,gcd(a,b)))
        print("lcm({},{})={}".format(a,b,lcm(a,b)))
```

### 9
```python
def div(n):
        return {x for x in range(1,n+1) if n % x == 0}

#alternativa:
#def div(n):
#       d=set()
#       for x in range(1,n+1):
#               if n % x == 0: d.add(x)
#       return d

def gcd(a,b):
        return max(div(a) & div(b))

def mul(n,limit):
        return {x*n for x in range(1,limit//n + 1)}

#alternativa
#def mul(n,limit):
#       d=set()
#       for x in range(1,limit//n + 1):
#               d.add(x*n)
#       return d

def lcm(a,b):
        return min(mul(a,a*b) & mul(b,a*b))

if __name__=="__main__":
        a,b=input("Inserisci due numeri (es: 48 36): ").split()
        a,b=int(a),int(b)
        print("div({})={}".format(a,div(a)))
        print("div({})={}".format(b,div(b)))
        print("mul({},{})={}".format(a,a*b,mul(a,a*b)))
        print("mul({},{})={}".format(b,a*b,mul(b,a*b)))
        print("gcd({},{})={}".format(a,b,gcd(a,b)))
        print("lcm({},{})={}".format(a,b,lcm(a,b)))
```

### 10
```python
def sdiv(n):
        return {x for x in range(2,n) if n % x == 0}

#alternativa:
#def sdiv(n):
#       d=set()
#       for x in range(2,n):
#               if n % x == 0: d.add(x)
#       return d

def pr(n):
        return not sdiv(n)

def pdiv(n):
        return {x for x in sdiv(n) if pr(x)}

#alternativa:
#def pdiv(n):
#       d=set()
#       for x in sdiv(n):
#               if pr(x): d.add(x)
#       return d

def gcd(a,b):
        csdiv=pdiv(a) & pdiv(b)
        r=1
        for x in csdiv:
                while a % (r*x) == 0 and b % (r*x) == 0:
                        r *= x
        return r

def lcm(a,b):
        return a * b // gcd(a,b)

if __name__=="__main__":
        a,b=input("Inserisci due numeri (es: 48 36): ").split()
        a,b=int(a),int(b)
        print("pdiv({})={}".format(a,pdiv(a)))
        print("pdiv({})={}".format(b,pdiv(b)))
        print("gcd({},{})={}".format(a,b,gcd(a,b)))
        print("lcm({},{})={}".format(a,b,lcm(a,b)))
```
### 11
```python
def tartline(l):
        l[:0]=[1]
        for i in range(1,len(l)-1):
                l[i] += l[i+1]

l=[]
for i in range(12):
        tartline(l)
        print("{:^60}".format(str(l)))
```

### 12
```python
def sdiv(n):
        return {x for x in range(2,n) if n % x == 0}

#alternativa:
#def sdiv(n):
#       d=set()
#       for x in range(2,n):
#               if n % x == 0: d.add(x)
#       return d

def pr(n):
        return not sdiv(n)

N=int(input("dammi il numero massimo (es 100): "))
print("ecco i numeri ***** fino a",N,":",[n for n in range(1,N+1) if pr(n)])
```


### 13
```python
vf=[("Nella vecchia fattoria","Quante bestie ha zio Tobia","C'è la capra","capra","ca"),
        ("Attaccato a un carrettino","C'è un quadrupede piccino","L'asinel","nel","nè"),
        ("Tra le casse e i ferri rotti", "Dove i topi son grassotti","C'è un bel gatto","gatto","ga"),
        ("Tanto grasso e tanto grosso", "Sempre sporco a più non posso", "C'è il maiale","iale","ia"),
        ("Poi sull'argine del fosso", "Alle prese con un osso", "C'è un bel cane","cane","ca"),
        ("Nella stalla silenziosa", "Dopo aver mangiato a iosa", "Dorme il bue","bue","bu")]
refrain="ia ia o"

def recverse(m,n):
        v1,v2,an1,an2,an3=vf[m]
        if n==m:
                print(v1,refrain)
                print(v2,refrain)
        else:
                recverse(m+1,n)
        print(an1,an2,an3,an3,an2)

for i in range(len(vf)):
        recverse(0,i)
        print(vf[0][0],refrain)
        print()
```

### 14
```python
import turtle

def hser(size, level):
        if level==0:
                turtle.forward(size)
        else:
                hser(size,level-1)
                turtle.left(45)
                turtle.forward(size * 2**0.5)
                turtle.left(45)
                hser(size,level-1)
                turtle.right(90)
                turtle.forward(size)
                turtle.right(90)
                hser(size,level-1)
                turtle.left(45)
                turtle.forward(size * 2**0.5)
                turtle.left(45)
                hser(size,level-1)

def ser(size, level):
        turtle.penup()
        pos=(2**(level+2)-3) * size // 2 #posizione iniziale
        turtle.setpos(-pos,pos)
        turtle.pendown()
        hser(size,level)
        turtle.right(90)
        hser(size,level)
        turtle.right(90)
        hser(size,level)
        turtle.right(90)
        hser(size,level)
        turtle.right(90)

turtle.speed(0)
turtle.hideturtle()
ser(2,1)
ser(2,2)
ser(2,3)
ser(2,4)
turtle.exitonclick()
```
### 15
```python
import turtle
import colorsys
import sys

def arrowstep(level, length, angle):
        if level:
                arrowstep(level-1, length/2, -angle)
                turtle.left(angle)
                arrowstep(level-1, length/2, angle)
                turtle.left(angle)
                arrowstep(level-1, length/2, -angle)
        else:
                turtle.forward(length)

def arrow(level, length):
        if level & 1:
                turtle.left(60)
                arrowstep(level, length, -60)
        else:
                arrowstep(level, length, -60)

turtle.speed(0)
turtle.hideturtle()
turtle.colormode(1)
nmax=6
width=256
xmin= -width//2
ymin= -width*(3**0.5)//4
for n in range(nmax):
        turtle.penup()
        turtle.setposition(xmin,ymin)
        turtle.setheading(0)
        turtle.pencolor(colorsys.hls_to_rgb(1.0*n/6,0.5,1))
        turtle.pendown()
        arrow(n,256)

turtle.exitonclick()
```
### 16
```python
def av(l):
        return sum(l)/len(l)

def rg(l):
        return max(l)-min(l)

def md(l):
        lx=len(l)
        ls=sorted(l)
        if lx%2:
                return ls[lx//2]
        else:
                return (ls[lx//2-1]+ls[lx//2])/2

if __name__=="__main__":
        l=input("dammi una lista di numeri separati da virgole (es: 1,2,3,4.4): ")
        l=[float(x) for x in l.split(',')]
        print("i valori trovati dalle tre funzioni sono: {:.4f} {:.4f} {:.4f}".format(av(l),rg(l),md(l)))
```

### 17
```python
import turtle
import sys

rows,cols=4,4
buttonsize=50
topdisplay=2*buttonsize

stack=[0]
fresh=True

def num(x):
        global fresh,stack
        if fresh:
                stack[:0]=[x]
                fresh=False
        else:
                stack[0]=stack[0]*10+x

enter,add,sub,mul,div=0,int.__add__,int.__sub__,int.__mul__,int.__floordiv__

def op(x):
        global fresh,stack
        if x!=enter and len(stack)>1:
                stack=[x(stack[1],stack[0])]+stack[2:]
        fresh=True

def off(x):
        sys.exit(0)

buttons={ 
        (0,0):('0',num,0), (1,0):('1',num,1), (1,1):('2',num,2), (1,2):('3',num,3), (2,0):('4',num,4), 
        (2,1):('5',num,5), (2,2):('6',num,6), (3,0):('7',num,7), (3,1):('8',num,8), (3,2):('9',num,9), 
        (3,3):('+',op,add), (2,3):('-',op,sub), (1,3):('*',op,mul), (0,3):('/',op,div),
        (0,2):('ent',op,enter), (0,1):('off',off,0)}

def click(x,y):
        col=x//buttonsize
        row=y//buttonsize
        if (row,col) in buttons:
                label,op,val=buttons[row,col]
                op(val)
                drawcalc()

def drawcalc():
        def drawbutton(col,row,label):
                turtle.setpos(row*buttonsize,col*buttonsize)
                turtle.pendown()
                for _ in range(4):
                        turtle.forward(buttonsize)
                        turtle.left(90)
                turtle.penup()
                turtle.setpos(row*buttonsize+buttonsize//2,col*buttonsize+buttonsize//2)
                turtle.write(label,align="center")
        turtle.clear()
        turtle.penup()
        for row,col in buttons:
                drawbutton(row,col,buttons[row,col][0])
        turtle.setpos(row*buttonsize*(rows-1),col*buttonsize*(cols+1))
        turtle.write(str(stack[0]),align="right")
        turtle.update()

turtle.screensize(cols*buttonsize+1, rows*buttonsize+topdisplay+1)
turtle.setup(cols*buttonsize+1, rows*buttonsize+topdisplay+1)
turtle.setworldcoordinates(0,0,cols*buttonsize, rows*buttonsize+topdisplay)
turtle.hideturtle()
turtle.speed(10)
turtle.tracer(0)
drawcalc()
turtle.onscreenclick(click)
turtle.listen()
turtle.mainloop()
```

### 18
```python
import turtle
import colorsys
import time

N=6
frompin=list(range(N,0,-1))
auxpin=[]
topin=[]

def rectangle(size, level, pin):
        turtle.penup()
        turtle.setpos(2*N*10*pin,level*10)
        turtle.setheading(0)
        turtle.pendown()
        turtle.fillcolor(colorsys.hls_to_rgb(1.0*(size-1)/N,0.5,1))
        turtle.begin_fill()
        turtle.forward(size*10)
        turtle.left(90)
        turtle.forward(10)
        turtle.left(90)
        turtle.forward(size*20)
        turtle.left(90)
        turtle.forward(10)
        turtle.left(90)
        turtle.forward(size*10)
        turtle.end_fill()

def showhanoi():
        turtle.clear()
        lf,la,lt=map(len,(frompin,auxpin,topin))
        for i in range(lf):
                rectangle(frompin[i], i, -1)
        for i in range(la):
                rectangle(auxpin[i], i, 0)
        for i in range(lt):
                rectangle(topin[i], i, 1)
        turtle.update()
        time.sleep(0.2)

def hanoi(n,f,a,t):
        if n==1:
                t.append(f.pop())
                showhanoi()
        else:
                hanoi(n-1,f,t,a)
                hanoi(1,f,a,t)
                hanoi(n-1,a,f,t)

turtle.hideturtle()
turtle.speed(10)
turtle.tracer(0)
showhanoi()
hanoi(N,frompin,auxpin,topin)
turtle.exitonclick()
```
### 19
```python
#!/usr/bin/env python3
#   Copyright 2014 Renzo Davoli University of Bologna - Italy
#   This program is free software; you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation; either version 2 of the License, or
#   (at your option) any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License along
#   with this program; if not, write to the Free Software Foundation, Inc.,
#   51 Franklin St, Fifth Floor, Boston, MA  02110-1301 USA.
#
import sys

class num:
	def __init__(self,n):
		self.val=n

class mul(num):
	pass

class onemul(mul):
	pass

class plus():
	pass

class times():
	pass

class numlanguage():
	def __init__(self):
		self.dict={}
	def __setitem__(self,s,op):
		self.dict[s]=op
		for l in range(len(s)-1,0,-1):
			if s[:l] in self.dict:
				break
			else:
				self.dict[s[:l]]=None
		return op
	def match(self,s):
		matchlen,obj=0,None
		for l in range(1,len(s)+1):
			if s[:l] in self.dict:
				matchlen,obj=l,self.dict[s[:l]]
			else:
				break
		return matchlen,obj

def str2num(langnum,s):
	hi=mid=lo=last=0
	lastop=None
	while s:
		if s[0] in " -\t\n":
			s=s[1:]
		else:
			ml,obj=langnum.match(s)
			if obj:
				if isinstance(obj,num):
					if isinstance(obj,mul):
						if isinstance(obj,onemul) and lo == 0:
							lo = 1
						if (last <= obj.val or isinstance(lastop,times)) and not isinstance(lastop,plus):
							hi,mid,lo = (hi+mid+lo)*obj.val,0,0
						else:
							hi,mid,lo = hi+(lo+mid)*obj.val,0,0
						last=obj.val
					else: 
						if obj.val == 100:
						 	mid,lo = lo*obj.val if lo else obj.val,0
						elif obj.val <= lo or isinstance(lastop,plus):
							lo += obj.val
						else:
							lo = lo*obj.val if lo else obj.val
					lastop=None
				else:
					lastop=obj
#print(s[:ml],hi,mid,lo,last,lastop)
				s=s[ml:]
			else:
				return -1
	return hi+mid+lo

def num_it():
	nl=numlanguage()
	nl["zero"]=num(0) 
	nl["uno"]=nl["un"]=nl["una"]=num(1) 
	nl["due"]=num(2) 
	nl["tre"]=num(3) 
	nl["quattro"]=num(4) 
	nl["cinque"]=num(5) 
	nl["sei"]=num(6) 
	nl["sette"]=num(7) 
	nl["otto"]=num(8) 
	nl["nove"]=num(9) 
	nl["dieci"]=num(10) 
	nl["undici"]=num(11) 
	nl["dodici"]=num(12) 
	nl["tredici"]=num(13) 
	nl["quattordici"]=num(14) 
	nl["quindici"]=num(15) 
	nl["sedici"]=num(16) 
	nl["diciassette"]=num(17) 
	nl["diciotto"]=num(18) 
	nl["diciannove"]=num(19) 
	nl["venti"]=nl["vent"]=num(20) 
	nl["trenta"]=nl["trent"]=num(30) 
	nl["quaranta"]=nl["quarant"]=num(40) 
	nl["cinquanta"]=nl["cinquant"]=num(50) 
	nl["sessanta"]=nl["sessant"]=num(60) 
	nl["settanta"]=nl["settant"]=num(70) 
	nl["ottanta"]=nl["ottant"]=num(80) 
	nl["novanta"]=nl["novant"]=num(90) 
	nl["cento"]=num(100) 
	nl["mille"]=onemul(10**3) 
	nl["mila"]=nl["migliaia"]=mul(10**3) 
	nl["milioni"]=nl["milione"]=mul(10**6) 
	nl["miliardi"]=nl["miliardo"]=mul(10**9) 
	nl["dozzine"]=nl["dozzina"]=mul(12) 
	nl["decine"]=mul(10) 
	nl["centinaia"]=mul(100) 
	nl["di"]=times() 
	nl["e"]=plus() 
	return nl

def num_en():
	nl=numlanguage()
	nl["zero"]=nl["null"]=num(0)
	nl["one"]=nl["a"]=num(1)
	nl["two"]=num(2)
	nl["three"]=num(3)
	nl["four"]=num(4)
	nl["five"]=num(5)
	nl["six"]=num(6)
	nl["seven"]=num(7)
	nl["eight"]=num(8)
	nl["nine"]=num(9)
	nl["ten"]=num(10)
	nl["eleven"]=num(11)
	nl["twelve"]=num(12)
	nl["thirteen"]=num(13)
	nl["fourteen"]=num(14)
	nl["fifteen"]=num(15)
	nl["sixteen"]=num(16)
	nl["seventeen"]=num(17)
	nl["eighteen"]=num(18)
	nl["nineteen"]=num(19)
	nl["twenty"]=num(20)
	nl["thirty"]=num(30)
	nl["forty"]=num(40)
	nl["fifty"]=num(50)
	nl["sixty"]=num(60)
	nl["seventy"]=num(70)
	nl["eighty"]=num(80)
	nl["ninety"]=num(90)
	nl["hundred"]=num(100)
	nl["thousand"]=mul(10**3)
	nl["million"]=mul(10**6)
	nl["billion"]=mul(10**9)
	nl["trillion"]=mul(10**12)
	nl["dozen"]=mul(12)
	nl["and"]=plus()
	nl["of"]=times()
	return nl
	
def num_fr():
	nl=numlanguage()
	nl["zero"]=num(0)
	nl["un"]=num(1)
	nl["deux"]=num(2)
	nl["trois"]=num(3)
	nl["quatre"]=num(4)
	nl["cinq"]=num(5)
	nl["six"]=num(6)
	nl["sept"]=num(7)
	nl["huit"]=num(8)
	nl["neuf"]=num(9)
	nl["dix"]=num(10)
	nl["onze"]=num(11)
	nl["douze"]=num(12)
	nl["treize"]=num(13)
	nl["quatorze"]=num(14)
	nl["quinze"]=num(15)
	nl["seize"]=num(16)
	nl["vingt"]=num(20)
	nl["trente"]=num(30)
	nl["quarante"]=num(40)
	nl["cinquante"]=num(50)
	nl["soixante"]=num(60)
	nl["cent"]=num(100)
	nl["mille"]=onemul(10**3)
	nl["million"]=mul(10**6)
	nl["milliard"]=mul(10**9)
	nl["douzaine"]=mul(12)
	nl["et"]=plus()
	nl["de"]=times()
	return nl

def num_de():
	nl=numlanguage()
	nl["null"]=num(0)
	nl["eins"]=nl["ein"]=num(1)
	nl["zwei"]=nl["zwo"]=num(2)
	nl["drei"]=num(3)
	nl["vier"]=num(4)
	nl["fÃ¼nf"]=num(5)
	nl["sechs"]=num(6)
	nl["sieben"]=num(7)
	nl["acht"]=num(8)
	nl["neun"]=num(9)
	nl["zehn"]=num(10)
	nl["elf"]=num(11)
	nl["zwÃ¶lf"]=num(12)
	nl["dreizehn"]=num(13)
	nl["vierzehn"]=num(14)
	nl["fÃ¼nfzehn"]=num(15)
	nl["sechzehn"]=num(16)
	nl["siebzehn"]=num(17)
	nl["achtzehn"]=num(18)
	nl["neunzehn"]=num(19)
	nl["zwanzig"]=num(20)
	nl["dreiÎ²ig"]=num(30)
	nl["dreiÃig"]=num(30)
	nl["vierzig"]=num(40)
	nl["fÃ¼nfzig"]=num(50)
	nl["sechzig"]=num(60)
	nl["siebzig"]=num(70)
	nl["achtzig"]=num(80)
	nl["neunzig"]=num(90)
	nl["hundert"]=num(100)
	nl["tausend"]=mul(10**3)
	nl["million"]=mul(10**6)
	nl["milliard"]=mul(10**9)
	nl["und"]=plus()
	return nl

def num_es():
	nl=numlanguage()
	nl["cero"]=num(0)
	nl["uno"]=num(1)
	nl["dos"]=num(2)
	nl["tres"]=num(3)
	nl["cuatro"]=num(4)
	nl["cinco"]=num(5)
	nl["seis"]=num(6)
	nl["siete"]=num(7)
	nl["ocho"]=num(8)
	nl["nueve"]=num(9)
	nl["diez"]=num(10)
	nl["once"]=num(11)
	nl["doce"]=num(12)
	nl["trece"]=num(13)
	nl["catorce"]=num(14)
	nl["quince"]=num(15)
	nl["diecisÃ©is"]=num(16)
	nl["diecisiete"]=num(17)
	nl["dieciocho"]=num(18)
	nl["diecinueve"]=num(19)
	nl["veinte"]=nl["veinti"]=num(20)
	nl["treinta"]=num(30)
	nl["cuarenta"]=num(40)
	nl["cincuenta"]=num(50)
	nl["sesenta"]=num(60)
	nl["setenta"]=num(70)
	nl["ochenta"]=num(80)
	nl["noventa"]=num(90)
	nl["cien"]=nl["cientos"]=num(100)
	nl["quinientos"]=num(500)
	nl["setecientos "]=num(700)
	nl["novecientos"]=num(900)
	nl["mil"]=onemul(10**3)
	nl["millÃ³n"]=nl["millones"]=mul(10**6)
	nl["billÃ³n"]=nl["billones"]=mul(10**12)
	nl["y"]=plus()
	return nl

if __name__ == "__main__":
	itnum=num_it()
	print("it",str2num(itnum,sys.argv[1]))
	ennum=num_en()
	print("en",str2num(ennum,sys.argv[1]))
	frnum=num_fr()
	print("fr",str2num(frnum,sys.argv[1]))
	denum=num_de()
	print("de",str2num(denum,sys.argv[1]))
	esnum=num_es()
	print("es",str2num(esnum,sys.argv[1]))
```
### 20
trace.py:
```python
def trace(f):
  f.indent = 0
  def strtuple(x):
    return "("+str(x[0])+")" if len(x)==1 else str(x)
  def g(*x):
    print('| ' * f.indent + '/-- ', f.__name__, strtuple(x), sep='')
    f.indent += 1
    value = f(*x)
    f.indent -= 1
    print('| ' * f.indent + '\-- ', 'return', repr(value))
    return value
  return g

def memoize(f):
  cache = {}
  def g(*x):
    if x not in cache:
      cache[x] = f(*x)
    return cache[x]
  return g
```
main.py:
```python
#!/usr/bin/env python3
import sys
import trace

# try to uncomment the following statements:
#@trace.trace
#@trace.memoize
def fib(i):
  if i<=0:
    return 0
  elif i==1:
    return 1
  else:
    return fib(i-1)+fib(i-2)

if __name__=="__main__":
  for i in range(int(sys.argv[1])):
    print(i,fib(i))
```
