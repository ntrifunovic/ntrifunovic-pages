topic: Strukture Podataka
title: Povezane Liste

[TOC]

---

**(eng. Linked List)**

Povezana lista je linearna struktura podataka, tj. podaci su u nekom linearnom poretku.

#Vrste povezanih lista

* jednostruka ulancana lista
* dvostruko ulancana lista
* ciklicna lista
* ne ciklicna lista

#Primer implementacije

	struct Elem {
		Podaci p;
		Elem* next;
		Elem* prev;
	};
	
	Elem* head; // Pokazivac na pocetak liste
	
Jednostruko povezane liste sadrze samo pokazivac `next`, a dvostruko povezane liste sadrze i `next` i `prev` pokazivac. 

**Primer implementacije jednostuko povezanih listi:**

	struct Elem {
		Podaci p;
		Elem* next;
	};

#Ubacivanje elementa
	
	// Ubacujemo element n iza elementa e
	void ubaci(Elem *e, Elem *n) {
		n->sled = e->sled;
		n->prev = e;
		e->sled->prev = n;
		e->sled = n;
	} 
	
#Izbacivanje elementa
	
	// Izbacuje element e iz povezane liste
	void izbaci(Elem* e) {
		Elem* prev = e->prev;
		Elem* next = e->next;
		
		prev->next = next;
		next->prev = prev;
	}

**Napomena**: Pretpostavlja se da postoji poslednji dummy element. 
*Da li bi ova implementacija radila da on ne postoji ?*
