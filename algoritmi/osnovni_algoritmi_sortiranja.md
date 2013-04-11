topic: Algoritmi
title: Osnovni algoritmi sortiranja

[TOC]

---

* Sortiranje je proces preuredjivanja skupa podataka da zadovoljava neki zadati poredak
* Sortiranje omogucava kasnije efikasno pretrazivanje
* Postoje razni algoritmi sortiranja

Osnovni algoritmi sortiranja koje cemo obraditi u ovoj prezentaciji su:

* Insertion sort
* Selection sort
* Bubble sort
* Counting sort
* Radix sort

#Insertion sort

1. Uredjeni deo niza se sastoji samo od prvog elementa niza
2. Sledeci element se umece u uredjeni deo niza na odgovarajuce mesto. Ovim se uredjeni deo niza povecava za jedan element, a ne uredjeni deo smanjuje za jedan element
3. Ako ne uredjeni deo nije prazan ponavlja se korak 2.


**Primer:** sortiramo niz 3 1 4 2 koristeci insertion sort

> 3 | 1 4 2
>
> 1 3 | 4 2
> 
> 1 3 4 | 2
> 
> 1 2 3 4 | 

#Selection sort

1. Uredjeni deo niza je prazan
2. Najmanji element ne uredjenog dela niza se prebacuje na kraj uredjenog dela niza
3. Ako ne uredjeni deo nije prazan ponavlja se korak 2.

**Primer:** sortiramo niz 3 1 4 2 koristeci slection sort

> 1 | 3 4 2
> 
> 1 2 | 3 4
> 
> 1 2 3 | 4
> 
> 1 2 3 4 | 

#Bubble sort

1. Prolazimo kroz niz i poredimo dva susedna elementa ako nisu u dobrom poredku menjamo im redosled
2. Ako je pri prolasku bilo promena ponavljamo korak 1.

**Primer:** sortiramo niz 3 1 4 2 koristeci bubble sort

> 3 1 4 2; 1-3 4 2; 1 3 2-4
> 
> 1 3 2 4; 1 2-3 4

#Counting sort

Podrazumeva se da su kljucevi po kojima se podaci sortiraju celi brojevi iz intervala od `1` do `K`.

**Ideja counting sort-a:** Odrediti broj elemenata manjih od nekog elementa. Koristeci ovu informaciju mozemo odrediti poziciju elementa u nizu.

*Sta da radimo kada niz sadrzi elemente sa istim kjucem ?*

1. Odredimo `C[x] =` broj elementa u nizu sa kljucem `x`, `x = 1..K `
2. `C[2] += C[1]; C[3] += C[2]; ... C[K] += C[K-1];`
3. Pozicija u sortiranom nizu elementa sa kljucem `x` je `C[x]`, problem vise istih  kjuceva resavamo tako sto radimo `C[x]--` posto smestimo element na njegovo mesto.

**Primer:** sortiramo niz 3 2 1 3 2 koristeci countig sort

>
1. `C[1] = 1`, `C[2] = 2`, `C[3] = 2`
2.  `C[1] = 1`, `C[2] = 3`, `C[3] = 5`
3.  
3. 	
 		_ _ _ _ 3 C[3] = 4
		_ _ 2 _ 3 C[2] = 2
     	1 _ 2 _ 3 C[1] = 0
     	1 _ 2 3 3 C[3] = 3
     	1 2 2 3 3 C[2] = 1	  

     	  
#Radix sort

Koristi si se kada su kjucevi k-tocifreni celi brojevi

1. Prvo se posmatra najmladja cifra kljuca
2. Elemente niza redom dodajemo na kraj jednog od 10 redova u zavisnosti od posmatrane cifre
3. Spajamo redove
4. Ponavljamo postupak od koraka 2. za sledecu cifru

**Primer:** sortiramo niz 213 191 222 214 koristeci radix sort

> 191 222 213 214
> 
> 213 214 222 191
> 
> 191 213 214 222