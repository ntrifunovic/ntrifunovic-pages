topic: Uvod u C++
title: Nizovi i Matrice

[TOC]

---

#Nizovi

	<tip> <ime>[<BROJ_ELEMENATA>]
	
* Slozeni tip podataka
* Osnovni struktuirani tip podataka
	* Elementi su istog tipa
	* Identifikuju se rednim brojem
		* Redni brojevi pocinju od `0` i idu do `<BROJ_ELEMENATA> - 1`
* `<BROJ_ELEMENATA>` je konkretan pozitivan ceo broj ili neka konstanta
* Nizovi se mogu inicijalizovati, tada se moze izostavitit duzina niza.

**Primer:**

	int a[10];

	int x[5] = {1, 2, 3, 4, 5};
	int y[] = {5, 4, 3, 2, 1};

	char s1[] = "End";
	const char s2[] = { 'E', 'n', 'd', '\0' };
	
#Matrice, Visedimenzionalni nizovi

Elementi niza mogu da budu nizovi, tako dobijamo visedimenzionalne nizove.

**Primer:**

	// Dvodimenzioni niz
	int x1[2][3] = {{5, 10, 15}, {3, 6, 9}};
	int x2[2][3] = {{5}, {3, 6}};

	// Trodimenzioni niz
	char tro[5][5][5];
	
Pristup elementima `k` dimenzionog niza:

	<tip> <ime>'['<N1>']''['<N1>']'...'['<Nk>']';

Ako zelimo da pristupimo elementu sa indekslima `x1`, `x2`, ... , `xk` to radimo na sledeci nacin:

	<ime>'['x1']''['x2']'...'['xk']'

**Primer:**

	int a[100][100];
	a[0][0] = a[1][1] = 10;
	a[2][2] = a[0][0] + a[1][1];
	
*Kako ucitati niz u memoriju?*

> 		int a[1000];  // niz u koji ucitavamo
> 		int n;  // n < 1000, inace ce doci do greske
> 		
> 		scanf("%d", &n);  // Ucitavamo velicinu niza
> 		
> 		// Ucitavamo elemente niza
> 		for(int i = 0; i < n; i++)
> 			scanf("%d", &a[i]);

	