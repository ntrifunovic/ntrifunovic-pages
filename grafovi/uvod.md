topic: Grafovi
title: Uvod

[TOC]

---

#Osnovni pojmovi

**Definicija:** Graf `G` je uređeni skup `(V, E)`, gde je `V` konačan neprazan skup čvorova, a `E` skup ivica (grana). Svaka ivica predstavlja par čvorova `(x, y)` iz `V`.

**Definicija:** Put od čvora `X` do nekog drugog čvora `Y` je niz ivica koji spaja ova dva čvora, u kome se svaka ivica iz grafa pojavljuje najviše jedanput.

**Definicija:** Za graf kažemo da je *povezan* ako i samo ako za svaka dva njegova čvora postoji put koji ih spaja. 

**Teorema:** Ako graf nije povezan onda se on može razbiti na povezane komponente, disjunktne po čvorovima.

#Načini čuvanja grafa u memoriji računara

U programskim jezicima koji se koriste na takmičenjima iz informatike graf ne postoji kao standardni tip podataka, pa ga zato na neki način treba predstaviti i čuvati u memoriji računara. 

Ovde su data dva načina čuvanja grafa u memoriji računara:

1. **Matrica povezanosti:** U matrici veličine `nxn` (gde je `n` broj čvorova grafa) polje `i`, `j` ima vrednost `1` ako postoji ivica koja povezuje čvorove `i` i `j`, ili `0` u slučaju da takva ivica ne postoji.

		#define MAXN 100
		
		int veze[MAXN][MAXN];
    
	*Napomena:* umesto matrice tipa int može se koristiti matrica tipa bool.

2. **Lista suseda:** U nizu velične `n` (gde je `n` broj cvorova) `i`-ti element sadrži povezanu listu u kojoj se nalaze svi čvorovi izmedju kojih i čvora `i` postoji ivica.

		#define MAXN 100
		
		// Lista indeksa čvorova
		struct PList { 
		  int v; // indeks čvora sa kojim je neki čvor povezan
		  PList* sled;
		};
		
		PList* veze[MAXN]; // Niz veza čiji su elementi liste indeksa čvorova
		
	*Napomena:* Može se korisit i neka STD struktura za čuvanje liste suseda (npr. `std::vector`, `std::list`, ... ).
	
#Vrste grafova

##Usmereni grafovi

Matrica povezanosti ne mora da bude simetrična, tj. ako postoji  grana `(a, b)` onda ne mora da postoji grana `(b, a)`.

![usmereni graf](/static/grafovi/Directed.svg)

##Ne usmereni grafovi

Matrica povezanosti je simetrična, tj. ako postoji  grana `(a, b)` onda postoji i grana `(b, a)`.

![ne usmereni graf](/static/grafovi/Undirected.svg)

###Drvo

**Definicija:** Drvo je neusmereni povezani graf bez ciklusa.

**Teorema:** Ako važe dve od sledeće tri osobine za neki graf onda za taj graf važi i treća osobina:

1. Graf od `N` čvorova ima `N-1` granu
2. Graf je povezan
3. Graf je drvo

![drvo graf](/static/grafovi/Tree_graph.svg)
