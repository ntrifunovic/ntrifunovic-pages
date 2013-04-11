topic: Uvod u C++
title: Primeri \ STD

[TOC]

---

#Liste

	:::C++
	// Primer sa listama 
	//
	// Liste koristiti kad ima dosta dodavanja na pocetak ili kraj liste
	// i kada se lista obilazi ili od pocetka ka kraju ili od kraja ka pocetku
	// ili kada se pristupa samo prvom i poslednjem elementu liste
	// Pristup i-tom elementu liste je ne efikasan posto se moraju obici elementi 
	// pre i-tog. 
	// Ako se cesto pristupa i-tom elementu bolje je koristiti std::vector.

	#include<stdio.h>
	#include<list>
	#include<set>
	
	using namespace std;
	
	int main() {
	  printf("Primer sa listama\n\n");
	
	  list<int> lista;
	
	  for(int i = 0; i < 10; i++) 
	    lista.push_back(i); // Ubacuje na kraj liste
	
	  for(int i = 0; i < 10; i++) 
	    lista.push_front(i);
	
	  if(!lista.empty()) {  // Provera da li je lista prazna 
	    // Pristup prvom i poslednjem elementu liste
	    printf("Prvi elem: %d\nPoslednji elem: %d\n", lista.front(), lista.back());
	  }
	
	  // Obilazak liste koristeci iteratore
	  //
	  // Lista ima dve specijalne metode begin() i end()
	  // begin() - vraca iterator koji pokazuje na prvi element liste
	  // end()   - vraca iterator koji pokazuje na element iza poslednjeg u listi
	  for (list<int>::iterator it = lista.begin(); it != lista.end(); it++) {
	    // *it vraca vrednost koja se nalazi u elementu liste na koji iterator
	    // pokazuje, iterator ima i operaciju ++ koja pomera iterator na sledeci
	    // element liste
	    printf("%d; ", *it);
	  }
	
	  putchar('\n');
	
	  while (!lista.empty()) {
	    printf("Prvi elem: %d\nPoslednji elem: %d\n", lista.front(), lista.back());
	    // Skidanje elementa sa pocetka i kraja liste
	    lista.pop_front();
	    lista.pop_back();
	  }
	
	  getchar();
	
	}

#Set

	:::C++
	// Primer sa setom
	//
	// Set ima sledece operacije:
	// insert - Ubacuje element u set O(logN))
	// erase  - Izbacuje element iz seta O(logN)
	// find   - Proverava da li se element nalazi u setu O(logN)
	
	#include<stdio.h>
	#include<list>
	#include<set>
	
	using namespace std;
	
	int main() {
	  printf("\n\nPrimer sa setom\n\n");
	
	  set<int> set_brojeva;
	
	  // set: 10 20 30 40 50
	  for (int i=1; i<=5; i++) {
	    set_brojeva.insert(i*10);    
	  }
	
	  set_brojeva.erase(20);
	
	  // Obilazak svih elemenata seta
	  for (set<int>::iterator it = set_brojeva.begin(); it != set_brojeva.end(); it++) {
	    printf("%d; ", *it);
	  }
	
	  for(int i = 0; i <= 10; i++)
	    if(set_brojeva.find(i) != set_brojeva.end()) {
	      printf("%d je u setu\n", i);
	    } else {
	     printf("%d nije u setu\n", i);
	    }
	
	  putchar('\n');
	
	  getchar();
	
	}
