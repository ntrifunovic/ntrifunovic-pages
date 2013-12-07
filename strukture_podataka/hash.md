topic: Strukture Podataka
title: Hash tabele

[TOC]

---

**Grafička ilustracija Hash tabele:**  
(Primer hash tabele koja preslikava imena u brojeve telefona)

![ilustracija hash tabela hashtabela funkcija](/static/strukture_podataka/Hash_table_3_1_1_0_1_0_0_SP.svg)

#Hash funkcije

* Hash funkcija je funkcija koja preslikava podatak promenjive veličine iz velikog skupa mogućih vrednosti u podatak fiksne veličine sa manjim skupom mogućih vrednosti.
* Podatak koji se preslikava se naziva ključ

**Primer:** Ključ moze biti ime osobe, koje se preslikava u ceo broj

**Primer:** Hash funkcija koja preslika reč od tri znaka

	h(r) = (r[0] + 3*r[1] + 7*r[2]) mod 11

#Hash tabele

* Hash funkcije se koriste za implementaciju hash tabela
* Hash tabela je struktura podataka sa asocijativnim pristupom, što znači da mapira ključeve u njihove vrednosti
* Hash tabela koristi hash funkciju da preslika ključ u br. ulaza tabele
* Svaki ulaz hash tabele je struktura podataka sa asocijativnim pristupom
* Najčešće se ulaz hash tabele realizuje kao povezana lista key-value parova
* Da bi se pretraga hash tabele brzo izvršavala potrebno je da je br. elemenata u svim ulazima približno jednak. To se postiže korišćenjem dobre hash funkcije

*Šta bi se desilo ako bi se svi kjučevi uvek preslikavali u jedan ulaz hash tabele?*

>Odgovor: Hash tabela bi se svela na pretraživanje u povezanoj listi

#Dobre hash funkcije

* Hash funkcije koje imaju uniformnu distribuciju vrednosti su dobre hash funkcije
* Hash funkcija treba da bude što prostija zbog lakšeg i bržeg izračunavanja

Pokazuje se da je funkcija `h(K) = K mod p`, gde je `p` prost broj, dobra hash funkcija.