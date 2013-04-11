topic: Uvod u C++
title: I\O


#Input\Output

---

[TOC]

---

##C vs C++ I\O

*[vs]: Protiv (eng. versus)

U ovom kursu koristicemo C I\O (biblioteku `stdio.h`) za input i output

* zato sto je znatno brza u odnosu na C++ I\O (biblioteka `iostream` - `cin` i `cout`)
* metode koje cemo najvise koristiti su
	* `scanf`, `fscanf`, `sscanf`
	* `printf`, `fprintf`
	* `getchar`, `fgetc`
	* `gets`, `fgets`
	* `puts`, `fputs`
	* `putchar`, `fputc`
	* `fopen`
	
**Primer:** Ucitavanje niza od `1 000 000` elemenata u nekom zadatku na takmicenju (sa standardnim vremenskim ogranicenjem od `1s`) moze biti suvise sporo ako se koristi `cin` (samo ucitavanje moze trajati duze od `1s`), a da radi dovoljno brzo ako se umesto `cin` koristi  `scanf`.
	
##Struktura C++ programa

Program koji ispisuje `Zdravo svete !!!`

	:::C++
	// Ovo je komentar
	/* I ovo je komentar */

	#include <stdio.h> // Koristimo standardnu biblioteku stdio

	int main() { // Ulazna tacka u program
		printf("Zdravo svete !!!"); // poziv metode za ispis na ekran iz biblioteke stdio
	
		return 0; // Vracamo vrednost 0, sto znaci da se nas program uspesno zavrsio
	} // Kraj metode main
		
Program koji sabira dva broja uneta sa tastature

	:::C++	
	// Program koji sabira dva broja uneta sa tastature
	
	#include <stdio.h> // Koristimo standardnu biblioteku stdio
	
	int main() { // Ulazna tacka u program
		int a, b; // Deklaracija promenjivih a i b tipa int
	
		// poziv metode scanf za citanje sa tastature iz biblioteke stdio
		scanf("%d%d", &a, &b); 
	
		printf("%d", a + b); // poziv metode za ispis na ekran iz biblioteke stdio
	
		return 0; // Vracamo vrednost 0, sto znaci da se nas program uspesno zavrsio
	} // Kraj metode main
	
## stdio.h

	FILE* fopen(const char* fileName, const char* mode);
	
`mode` moze biti

* `"r"` ako zelimo da citamo iz fajla
* `"w"` ako zelimo da pisemo u fajl
*  postoje i drugi modovi, ali mi ih necemo koristiti


Povratna vrednost je pokazivac na objekat tipa `FILE` koji koristimo za pristup otvorenom fajlu.

*[pokazivac]: Pokazivace cemo raditi kasnije u kursu, za sada ne moramo da znamo nista o njima da bismo koristili ove funkcije

Ako je doslo do greske prilikom otvaranja fajla povratna vrednost je `null` (pokazivac na nista).

*Takodje postoji i metoda `fclose` , koja sluzi za zatvaranje fajla, ali mi je necemo koristiit zato sto se po zavrsetku programa fajl sam zatvara.*

---

	int getchar(); // cita sa standardnog ulaza
	int fgetc(FILE* f); // cita iz fajla
	
* Cita jedan karakter sa standardnog ulaza\fajla
* Povratna vrednost je procitani znak (njegov ASCII kod ili `EOF` ako se stiglo do kraja fajla)
	* `EOF` je konstanta koja se nalazi u `stdio.h`

`getc` radi isto sto i `fgetc`.

---

	int putchar(int ch); // pise na standardni izlaz
	int fputc(int ch, FILE* f); // pise u fajl
	
* Pise jedan karakter na standardni izlaz\fajl
* Vraca `ch` ako je upis uspeo, `EOF` ako je doslo do greske

`putc` radi isto sto i `fputc`.

---

`gets`, `fgets` - Cita do kraja linije  
`puts`, `fputs` - Ispisuje jednu liniju

*Za koriscenje ovih metoda potrebno je znanje nizova koje cemo uciti kasnije tokom kursa, pa ne ulazimo u detalje.*

**Primer:** Program radi isto kao program sa pocetka ove lekcije.

	#include <stdio.h>
	 
	int main() {
	    puts("Zdravo svete !!!");
	
	    return 0;
	}

---

	int scanf(const char* format, ...);
	int fscanf(FILE* f, const char* format, ...);
	
* Povratna vrednost je broj procitanih elemenata, `EOF` ako je doslo do greske
* `format` - Format ulaza koji se cita
* Posle formata sledi lista adresa promenjivih u koje se pamte ucitane vrednosti
	* Za dobijanje adrese promenjive koristi se operator `&` 

---

	int printf(const char* format, ...);
	int fprintf(FILE* f, const char* format, ...);

* Povratna vrednost je broj ispisanih karaktera, negativna vrednost ako je doslo do greske
* `format` - Format izlaza koji se ispisuje
* Posle formata sledi lista promenjivih koje se ispisuju

---

###`scanf`, `printf`, `sscanf`, ...  parametar `format`

* `%c` 		`char`
* `%d` 		`long`, `int`
* `%u` 		`unsigned int`
* `%lld` 	`long long`
* `%f` 		`float`
* `%lf` 	`double`
* `%s` 		`char*`

* Opciono posle `%` moze ici `*` sto ce za posledicu imati da se procitani podatak ne pamti u neku promenjivu
* Postoje i drugi opcioni parametri vezani za formatiranje ulaza