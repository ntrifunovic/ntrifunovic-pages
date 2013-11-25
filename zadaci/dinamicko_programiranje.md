topic: Zadaci
title: Dinamičko programiranje
 
1. Odrediti n-ti fibonačijev broj. (`f[0] = 1`, `f[1] = 1`, `f[i] = f[i-1] + f[i-2]`)

		n < 1.000.000

2. Dat je niz celih brojeva. Naći podniz uzastopnih brojeva tako da je njihova suma maksimalna.

3. Perica je na poklon dobio bele i crne kuglice. On želi da ih složi u niz tako da u nizu (gledajući sa leva na desno) ako se nalazi bela kuglica onda iza nje mora obavezno ići crna, a iza crne može ići i bela i crna kuglica. Koliko postoji različitih nizova dužine `n`?

4. Data je matrica a dimenzije `n * m` popunjena celim brojevima. Sa svakog polja u matrici dozvoljeno je preći samo na polje ispod ili na polje desno od tog polja (ukoliko postoje). Potrebno je izabrati put od gornjeg levog polja (polje sa koordinatama  `[1; 1]`), do donjeg desnog polja (polja sa koordinatama `[n;m]`), tako da zbir brojeva u poljima preko kojih se ide, bude maksimalan.

		n, m < 5000

5. Data je binarna matrica (elementi matrice su 0 ili 1) dimenzije `n * m`. Naći najveću kvadratnu podmatricu koja u sebi sadrži samo nule.

		n, m < 5000

6. Koliko ima 2N-tocifrenih brojeva čiji je zbir prvih `N` cifara jednak zbiru poslednjih `N` cifara? Rešenje štampati po modulu `7919`.

		N < 10000

7. Najduži zajednički podniz (eng. *longest common subsequence*): Data su dva niza `a` i `b`. Naći niz najveće moguće dužine koji je podniz i za `a` i za `b`.

		|a|, |b| < 5000
      
8. Dat je niz prirodnih brojeva dužine `n`. Nači najduži rastuči podniz. (ne nužno uzastopnih elemenata)

		n < 5000

9. **Problem ranca:**  
Provalnik sa rancem zapremine `N` upao je u prostoriju u kojoj se čuvaju vredni
predmeti. U prostoriji ima ukupno M predmeta. Za svaki predmet poznata je njegova vrednost `v[k]` i njegova zapremina `z[k], k ϵ [1,M]`. Sve navedene vrednosti su celobrojne. Provalnik želi da napuni ranac najvrednijim sadržajem.  

	Potrebno je odredti koje predmete treba staviti u ranac.

		N, M < 5000

10. **Problem ranca sa ponavljanjem elemenata:**  
Provalnik sa rancem zapremine `N` upao je u prostoriju u kojoj se čuvaju vredni
predmeti. U prostoriji ima ukupno `M` klasa predmeta. Za svaku klasu predmeta poznata je njegova vrednost `v[k]` i njegova zapremina `z[k], k ϵ [1,M]`. Sve navedene vrednosti su celobrojne, predmeta svake klase ima beskonačno mnogo. Provalnik želi da napuni ranac najvrednijim sadržajem.  

	Potrebno je odredti koje predmete treba staviti u ranac.

		N, M < 5000