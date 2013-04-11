topic: Uvod u C++
title: Strukture

#Strukture u jeziku C++

Sintaksa:

	struct imeTipaStrukture {
		tip1 ime1;
		tip2 ime2;
		...
		tipk imek;
	} promenjiva1;

	imeTipaStrukture promenjiva2;

`Promenjiva1` i `Promenjiva2` su tipa `imeTipaStrukture`.

Definisali smo tip koji sadrzi k promenjivih tipova `tip1`, `tip2`, ..., `tipk`. Vrednosti ovih promenjivih mozemo pristupiti navodjenjem imena promenjive iza tacke(`.`).

**Primer:**

	promenjiva1.ime2 = vrednost;
	tipk x = promenjiva2.imek;
	
	
* Struktura ne moze sadrzati podatke tipa te strukture
* Struktura moze sadrzati podatke tipa pokazivaca na tu strukturu
* Strukture u sebi mogu sadrzati metode i operatore 
	* Metode mogu biti staticke	
	> Necemo ih koristiti u ovom kursu
	* Ne statickim metodam se pristupa slicno kao i podacima
		
			promenjiva1.metoda1(); // gde je promenjiva1 istanca strukture koja sadrzi metodu metoda1
		
**Primer:**

	struct Tacka {
		int x, y;
	};
	
	Tacka tacke[100];
	
	int main() {
		for(int i = 0; i < 100; i++)
			scanf("%d%d", &tacke[i].x, &tacke[i].y);
		....
		return 0;
	}
	

	

