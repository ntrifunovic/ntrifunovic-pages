topic: Strukture Podataka
title: Hash tabele

[TOC]

---

#Hash funkcije

* Hash funkcija je funkcija koja preslikava podatak promenjive velicine iz velikog skupa mogucih vrednosti u podatak fiksne velicine sa manjim skupom mogucih vrednosti.
* Podatak koji se preslikava se naziva kljuc

**Primer:** Kljuc moze biti ime osobe, koje se preslikava u ceo broj

**Primer:** Hash funkcija koja preslika rec od tri znaka

	h(r) = (r[0] + 3*r[1] + 7*r[2]) mod 11

#Hash tabele

* Hash funkcije se koriste za implementaciju hash tabela
* Hash tabela je struktura podataka sa asocijativnim pristupom, sto znaci da mapira kljuceve u njihove vrednosti
* Hash tabela koristi hash funkciju da preslika kljuc u br. ulaza tabele
* Svaki ulaz hash tabele je struktura podataka sa asocijativnim pristupom
* Najcesce se ulaz hash tabele realizuje kao povezana lista key-value parova
* Da bi se pretraga hash tabele brzo izvrsavala potrebno je da je br. elemenata u svim ulazima priblizno jednak. To se postize koriscenjem dobre hash funkcije

*Sta bi se desilo ako bi se svi kjucevi uvek preslikavali u jedan ulaz hash tabele?*

>Odgovor: Hash tabela bi se svela na pretrazivanje u povezanoj listi

#Dobre hash funkcije

* Hash funkcije koje imaju uniformnu distribuciju vrednosti su dobre hash funkcije
* Hash funkcija treba da bude sto prostija zbog lakseg i brzeg izracunavanja

Pokazuje se da je funkcija `h(K) = K mod p` gde je `p` prost broj dobra hash funkcija