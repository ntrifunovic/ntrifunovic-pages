topic: Algoritmi
title: Složenost algoritma

[TOC]

---

# Medjusobno poredjenje vise algoritama

Da bi se od vise mogucih algoritama odredio najbolji obicno je potrebno oceniti dve velcine:

* **Vremenska slozenost** - broj elementarnih operacija koje program izvrsi
* **Prostorna slozenost** - Zauzece memorije

Uobicajan nacin za izrazavanje slozenosti algoritma je *O*-notacija.

## Najcesce funkcije kojima se izrazava slozenost su:

* $O(1)$
	* Izracunavanje u konstantom vremenu.	
	* *Primer:* 
	>		(a + b) % c
* $O(\log n)$
	* Logaritamska slozenost. Slozenost veoma sporo raste sa povecanjem dimenzije ulaza.
	* *Primer:* 
	> Binarna pretraga
* $O(n)$
	* Linerana slozenost. Za svaki element ulaza potrebno je neko konstatno vreme obrade.
* $O(n \log n)$
	* *Primer:* 
	> Merge Sort, Heap Sort 
* $O(n^2)$
	* Kvadratna slozenost. 	
	* *Primer:* 
	> 		for(int i = 0; i < n; i++)
				for(int j = 0; j < n; j++)
					... // Neka obrada u slozenosti O(1)
* $O(n^3)$
* $O(2^n)$  
	* Eksponencijalna slozenost.
	* *Primer:* 
	> *Brute force* resenja problema

# Osobine funkcije *O*

$O(c \cdot n) = O(n),\ c - const$  
$O(f(n)) + O(g(n)) = O(f(n) + g(n))$  
$O(f(n)) O(g(n)) = O(f(n) g(n))$  