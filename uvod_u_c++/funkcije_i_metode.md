topic: Uvod u C++
title: Funkcije\Metode

	<tip> <ime>(<lista_argumenata>) <telo>
	
* Podela resenja na manje delove
* Koriscenje takvih delova na vise mesta
* Funkciju mozemo smatrati za n-arni operator najviseg prioriteta
* `<tip>` - svi tipovi koje smo spominjali + `void` (kada funkcija ne vraca vrednost)
* `<lista_argumenata>` - proizvoljni br. elemenata razdvojenih `,` (moze biti i nula).
* F-ja vraca vrednost koristeci komandu `return izraz;`, tada se ujedno izlazi iz f-je.

#Argumenti

* Argumenti se mogu u funkciju preneti po vrednosti ili po referenci.
* Podrazumevano je da se prenose po vrednosti
	* To znaci da f-ja ima svoju kopiju argumenata
* Ako zelimo da se argument prenosi po referenci tada treba da dodamo `&` ispred imena argumenta u listi argumenta.
	* To znaci da kada f-ja menja argument ona menja i vrednost za koju je f-ja pozvana
	
	
**Primer:**

	#include<stdio.h>
	
	int zbir(int a, int b) {
		return a + b;
	}
	
	int main() {
		int x = 1, y = 3;
	
		printf("%d %d %d", zbir(x, y), zbir(x, 5), zbir(3, 5));
	}
	
*Sta ispisuje program?*

> Resenje: 4 6 8