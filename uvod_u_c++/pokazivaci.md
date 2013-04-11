topic: Uvod u C++
title: Pokazivaci

**(eng. Pointers)**

* Promenjiva tipa pokazivac na neki tip se deklarise na sledeci nacin

		tip *imePokazivaca;
		
* Vrednost pokazivaca predstavlja adresu u memoriji na kojoj se nalazi promenjiva onog tipa koji je koriscen pri deklaraciji pokazivaca
* Memoriskoj lokaciji na koju ukazuje pokazivac pristupamo unarnim prefiksnim operatorom `*`
* Unarni prefiksni operator `&` vraca adresu podatka u memoriji
* Za pristup elementima strukture preko pokazivaca koristi se operator `->`
* Pokazivaci se ponasaju kao i drugi podaci
	* Mogu se praviti nizovi pokazivaca
	* Strukture u sebi mogu sadrzati pokazivace


**Primer:**

	int x = 10;
	int *px = &x, y; // y nije pokazivac
	*px = 3;
	y = x;

*Koja je vrednost u promenjivoj y ?*
> Resenje: 3

	// Pristupanje elementima strukture preko pointera
	Tacka *pt = &t;
	(*pt).x = 0;
	pt->y = 0;