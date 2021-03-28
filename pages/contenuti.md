##CONOSCENZE DI BASE

(v. [Concetti fondamentali dell'Informatica](concetti_fondamentali.md) )
Definizione di Informatica
Hardware vs. Software
Algoritmo
Linguaggio
Programma/Processo
Eroi

##CLASSI DI APPLICAZIONI

GUI vs. CLI
Word Processor (WYSIWYG e non, font tipografici)
Foglio elettronico (cella, formule e dipendenza)
Presentazione
Grafica/elaborazione immagini (vettoriale e bitmap)
Elaborazione suono/musica (campionamento e MIDI)
Elaborazione video
Browser
Instant messaging
Posta Elettronica

Applicazioni installate e cloud based
Applicazioni e Distribuzioni

##PROGRAMMAZIONE

Linguaggi programmazione: procedurali, funzionali, logici

Linguaggi dei dati (Formati)
Linguaggi di Marcatura

Protocolli. 

Compilatori e Interpreti

Script e Programmi

Pseudocodice;

Concetti di programmazione:
Variabili;
Espressione;
Istruzione;
Sequenza;
Blocco;
Condizione;
Cicli;
Funzioni;
Ricorsione;
Moduli;
Oggetti;
Attributi:
Metodi:
Classi;
Librerie

##ALGORITMI
Tipi Elementari:
int;
float;
char;
unicode;
UTF

Strutture Dati:
scalari;
vettori;
liste;
code;
stack;
alberi;
grafi;

Complessita':
complessita' in tempo e in spazio;
come si misura;
ordine di crescita

Algoritmi elementari:
aritmetici (MCD, mcm...)

Tecniche Algoritmiche:
Divide et Impera;
Backtrack;
Algoritmi approssimati;
Greedy

Algoritmi di ordinamento:
counting sort;
inserimento;
selezione;
shellsort;
mergesort;
quicksort;
heapsort

Algoritmi di ricerca:
sequenziale;
ricerca binaria/dicotomica;
alberi di ricerca;
hashing (separate chaining, linear probing)

Algoritmi su alberi:
Visita depth first. breath first;
alberi binari: preordine, inordine, postordine;
alberi bilanciati;
alberi binari di ricerca

Algoritmi su grafi:
visita depth first;
visita breadth first;
calcolo delle componenti connesse;
riconoscimento dei cicli;
gradi di separazione;
sort topologico;
chiusura transitiva;
connessione forte in un grafo diretto;
Minimum spanning tree;
Minimo cammino su un grafo;
Calcolo di tutti i cammini minimi

Algoritmi su stringhe:
Radix sort;
Ricerca di sottostringhe;
Elaborazione di espressioni regolari (Automi a stati finiti);
Compressione: Codifiche run-length;
Compressione: Codifica di Huffman;
Compressione: Lempel-Ziv-Welch.

Altri Algoritmi:
Algoritmi geometrici;
B-tree;
Reti di flusso;
Matrimoni stabili;

Codifica:
Testo, Audio, Immagini;
Compressione lossless/lossy;
codice grey;
CRC;
Hamming;
Reed-Solomon;

##CALCOLO NUMERICO

Floating point, errori e propagazione

Calcolo di sistemi lineari: metodo di gauss, decomposizione matrici (LU e Cholesky), numero di condizione

Equazioni non lineari: quadratiche, cubiche, calcolo degli zeri (secanti e tangenti)

Derivazione numerica

Interpolazione 

Approssimazione

Integrazione: montecarlo, trapezi

Equazioni differenziali

Trasformata di Fourier (FFT)

Metodi montecarlo

##ARCHITETTURA

Storia dell'architettura: generazione 0 (Byron/Lovelace), 1 (valvole), 2 (transistor), 3 (IC), 4 (VLSI), quinta: computer invisibili

Lo zoo dei computer: microcontrollori/embedded, personal computer, server, mainframe, cloud

Elaborazione Digitale ed Analogica
Porte Logiche
tecniche costruttive: Relais/Transistor/IC
circuiti combinatorici elementari
-encoder
-decoder
-multiplex selector
-half-adder
-adder

circuiti sequenziali elementari
-flip-flop

Processori: control path e data path, CISC e RISC, microcodice, ISA, registri. Protezione hardware del sistema: Modo kernel/user. Interrupt/Trap.

Linguaggi assembler: codice operativo, indirizzamento, gestione stack, salti.

Memoria Centrale: RAM/ROM/EPROM memoria statica e bipolare, cache di processore. Codici di correzione errore.

MMU: indirizzi logici e fisici, protezione di memoria.

Memoria Secondaria: Gerarchia delle memorie. *Dischi magnetici, memorie flash, CD/DVD. RAID*

Memoria Virtuale.

Unita' di Input Output: Bus, DMA e arbitraggio del Bus, Unita' memory mapped.

Architetture Parallele: SIMD/MIMD. Multithreading. Tightly coupled multiprocessor: gestione interrupt e coerenza delle cache.
Loosely coupled multiprocessor: sistemi massicciamente paralleli. 

*(Attualita': approfondimento sulla struttura dei Data-Center)*

##MACCHINE ASTRATTE, LINGUAGGI FORMALI E CALCOLABILITA'
(ci sono argomenti adatti alle scuole superiori?)

Stringhe, alfabeti, linguaggi, operazioni.
Macchine a Stati finiti (deterministiche e non deterministiche: equivalenza)
Linguaggi regolari
Grammatiche: classificazione di Chomsky
Automi a pila e grammatiche context free
Macchine di Turing
Computabilità: MT universale, riducibilità, definizione di P, NP, NP-hard, NP-completo)

##COMPILATORI

Front-End e Back-End: porting di un compilatore

Compilatori e Interpreti

Passi di un compilatore: analisi lessicale, sintattica, generazione codice intermedio, ottimizzazione, generatore di codice macchina

Storia e tassonomia dei linguaggi di programmazione.

Il linkage editor, la gestione delle librerie, librerie statiche e dinamiche.

Il codice e l'ambiente di esecuzione.

##SISTEMI OPERATIVI

Definizione di Sistema Operativo (e di Distribuzione). Storia dei Sistemi Operativi. Sistemi Batch e interattivi. Sistemi mono-multi utente.

Struttura dei sistemi operativi: monolitico, monolitico/modulare, exokernel, microkernel, macchine virtuali.

Processi e Thread

Programmazione concorrente/Inter Process Communication: message passing, semafori, mutex, monitor.

Scheduling

I/O: device driver, interrupt handler. Deadlock.

Memory management: protezione di memoria, segmentazione/paginazione, paginazione a richiesta e memoria virtuale.

File System: File e directory. Attributi dei file. Implementazione dei File System. Allocazione indicizzate e concatenata.
controllo e ripristino di coerenza. Journaling.

##RETI

Struttura a Livelli dei Protocolli: i 7 livelli OSI (PDNTSPA) e i 5 reali: fisico, data link, network, transport, application.
LAN/WAN (MAN, PAN ...) 

Modelli di interazione: Client-Server, Peer-to-Peer

Fisico: Supporti per trasmissioni. Cavi, onde radio. Segnali e modulazioni, topologia fisica,

Data Link: indirizzo MAC,codici a correzione di errore, controllo di accesso del canale, reti a diffusione/bus e a token.
Funzionamento di Switch/Bridge

Network: internetworking, indirizzi a livello network. Indirizzamento, routing: link state e distance vector, controllo di congestione, QoS.

Transport: datagrammi e connessioni, controllo di connessione (protocollo a finestra scorrevole)

Protocolli applicativi.

Sicurezza in rete.

Architettura di Internet:
*Fisico/Data Link: Ethernet, Wi-Fi, ADSL*
*Network/Transport: IP, IPv6, TCP/UDP, ICMP (ICMPv6)*
*Protocolli Applicativi: DNS, SMTP, POP, IMAP, HTTP, FTP, SSH, protocolli Peer-to-Peer*

##DATA BASE
Concetto di sistema informativo. Informatizzazione dei sistemi informativi.

Il modello E/R. Gli attributi e le associazioni. Tipi di associazioni. Lo schema E/R.

Il modello relazionale. Le tabelle e le relazioni. Tipi di relazioni. Vincoli di integrità dei dati. La normalizzazione e le 3 forme normali. Operazioni dell'algebra relazionale: ridenominazione, proiezione, restrizione, incrocio, prodotto, join.

I sistemi integrati: DBMS. Tre linguaggi per i DBMS: DDL, DML, DCL. I linguaggi dichiarativi: l'SQL. Schema fisico VS schema logico. I DBMS come sistemi distribuiti. Cenni di sicurezza su un DBMS.

L'SQL come tutto fare della teoria relazionale. Modellazione di un sistema informativo: le istruzioni di DDL. I vincoli in SQL. Dalle operazioni relazionali e alle istruzioni di DML dell'SQL. Le interrogazioni: tecniche e funzionalità SQL. Gli indici. Cenni di politiche di sicurezza: SQL come DCL.

<!--Domanda aperta: presentare prima la teoria relazionale, con tanto di algebra relazionale, e solo in seguito mostrare come l'SQL si dimostri linguaggio tutto fare nel realizzarne concetti e operazioni o invece introdurre l'SQL assieme al concetto di algebra relazionale, integrando passo passo la spiegazione delle operazioni relazionali con il parallelo delle corrispettive nel linguaggio SQL (che darebbe, tra l'altro, la possibilità di un effetto pratico, verificale dagli studenti)? -->

##SICUREZZA

Vulnerabilità, rischi, attaccanti, exploit
Crittografia (simmetrica, asimmetrica, firma eletronica)
Autenticazione
Autorizzazione e controllo di accesso
Vulnerabilità del software (bug di progetto, errori di memoria, buffer overflow, tempo autorizzazione-tempo uso, iniezione di codice) 
Architetture di rete sicure (firewall, VPN)
Sicurezza dei sistemi wireless
Codice malevolo (virus, vermi, cavalli di troia, botnet e reti sotterranee, honeypot)
Ingegneria sociale (phishing)

##INGEGNERIA DEL SOFTWARE

Design pattern: Model View Controller (MVC)
Modelli a cascata e agile.
Software testing

##USABILITA' E ACCESSIBILITA'

Concetti di base sull'usabilità. Concetti di base sull'accessibilità.

##BIG DATA

##INTELLIGENZA ARTIFICIALE
Test di Turing
Intelligenza debole e forte
Reti Neuronali *multilivello, feed forward, ricorrenti*
Apprendimento *supervisionato, isemi-supervisionato, non supervisionato*

##ASPETTI LEGALI ED ETICI

Programma come testo, diritto di autore. Concetto di Plagio. Licenze.
Software proprietario e software libero.
Protocolli e Formati aperti e chiusi.
Open Data.
