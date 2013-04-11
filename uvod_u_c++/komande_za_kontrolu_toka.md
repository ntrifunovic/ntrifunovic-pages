topic: Uvod u C++
title: Komande za kontrolu toka

[TOC]

---

#if - else


	if (izraz)
		naredba1;
	else
		naredba2;

* Naredba grananja
* Ako je `izraz == true` onda se izvrsava naredba1 a ako nije onda se izvrsava naredba2
* `else` grana je opciona

**Primer:**

	if (mesec == 12) {
		godina++;
		mesec = 1;
	} else
		mesec ++;
		
#switch

	switch (izraz) {
		case v1: niz_naredbi_1;
		case v2: niz_naredbi_2;
		...
		case vN: niz_naredbi_N;
		default: niz_naredbi;
	}
	
* `default` - izvrsava se kada vrednost izraza nije nijedna od zadatih, nije obavezan
* Najcesce se svaki niz naredbi zavrsava sa naredbom `break;`

**Primer:**

	switch(getchar()) {
		case 'X':
		case 'x':
			scanf("%d", &x);
			break;
		case 'Y':
		case 'y':
			scanf("%d", &y);
			break;
		default:
			printf("Greska");
	}
	
#Ciklusi

* Kontrolisano ponavljanje naredbe u zavisnosti od nekog uslova.
* Eksplicitno zavrsavanje ciklusa (naredba `break`)
* Ciklusi u jeziku C++ `while`, `do while` i `for`

Ako je uslov ispunjen ulazimo u petlju kada se naredba izvrsi opet proveramo uslov da odlucimo da li cemo opet uci u petlju ili cemo produziti dalje sa izvrsavanjem.


Svaka `while` petlja ima 0 ili vise iteracija.

##while

	while (uslov) 
		naredba;

**Primeri:**

		while(n > 0)
			printf("%d", n--);

Beskonacna petlja 

	while (true)
		...

##do while

	do
		naredba;
	while (uslov);

Prvo se izvrsi telo petlje pa se zatim proverava uslov.

Ciklus se ponavalja bar jedan put.

**Primer:**

	do {
		x++;
		y += 2;
	} while(y < x);
	
##for

	for(izraz_inicijalizacija; uslov; izraz_korak)
		naredba;
	
1. `izraz_inicijalizacija` se izvrsava jednom pri ulasku u petlju.
2. Zatim se proverava `uslov` i ako je ispunjen ulazi se u petlju ako nije petlja se  zavrsava.
3. Izrsava se telo petlje posle cega se izvrsava `izraz_korak` i ponavlja sve od korak 2.

*Kako odrediti maksimum n brojeva ?*

> 		int n, max;
> 		scanf("%d", &n);
> 		
> 		for (int i = 0; i < n; i++) {
> 			int tren;
> 			scanf("%d", &tren);
> 		
> 		if (i == 0)
> 			max = tren;
> 		else if (max < tren)
> 			max = tren;
> 		}
> 		
> 		printf("%d", max);

##break & continue

`break` - naredba za izlazak iz ciklusa

* skace se na prvu naredbu posle ciklusa
* preskace ostale naredbe u `switch`-u

`continue` - naredba za skok na kraj ciklusa

* preskace ostale naredbe u telu petlje

**Primer:**
	
	// Prva petlja
	while (true) {
		i = 4;
		break;
		i = 3;
		continue;
	}
	
	// Druga petlja
	while (true) {
		i = 3;
		continue;
		i = 4;
		break;
	}
	
*Koja petlja ce se izvrsavati beskonacno dugo i zasto ?*

> Resenje: druga

*Zadatak za uvezbavanje:* Odrediti i ispisati sumu brojeva koji se unose sa tastature sve dok se ne unese `0`.