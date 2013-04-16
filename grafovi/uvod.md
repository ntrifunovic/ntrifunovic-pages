topic: Grafovi
title: Uvod

#Osnovni pojmovi

Graf **G** je uredjeni skup **(V, E)**, gde je **V** skup cvorova, a **E** skup ivica. Svaka ivica predstavlja
par cvorova **(x, y)** iz **V**.

Put od cvora **X** do nekog drugog cvora **Y** je niz ivica koji spaja ova dva cvora, u kome se svaka ivica iz grafa pojavljuje najvise jedanput.

Za graf kazemo da je povezan ako i samo ako za svaka dva njegova cvora postoji put koji ih spaja. Ako graf nije povezan onda se on moze razbiti na povezane komponente, disjunktne po cvorovima.

#Nacini cuvanja grafa u memoriji racunara

1. **Matrica povezanosti:** U matrici velicine `nxn` (gde je `n` broj cvorova grafa) polje `i`, `j` ima vrednost `1` ako postoji ivica koja povezuje cvorove `i` i `j`, ili `0` u slucaju da takva ivica ne postoji.

		#define MAXN 100
		
		int veze[MAXN][MAXN];
    
	*Napomena:* umesto matrice tipa int moze se koristiti matrica tipa bool.

2. **Lista suseda:** U nizu velicne `n` (gde je `n` broj cvorova) `i`-ti element sadrzi povezanu listu u kojoj se nalaze svi cvorovi izmedju kojih i cvora `i` postoji ivica.

		#define MAXN 100
		
		struct PList {
		  int v;
		  PList* sled;
		};
		
		PList* veze[MAXN];
		
	*Napomena:* Moze se korisit i neka STD struktura za cuvanje liste suseda (`std::vector`, `std::list`, ... ).