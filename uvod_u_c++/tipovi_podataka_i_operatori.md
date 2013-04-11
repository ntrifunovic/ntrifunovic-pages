topic: Uvod u C++
title: Tipovi podataka & Operatori

[TOC]

---

#Podaci i Tipovi

* Podatak je svaki objekat koji se obradjuje.
* U programskom jeziku C++ svaki podatak ima svoj tip (C++ je  strogo tipiziran jezik).
* Tip podatka odredjuje sta moze biti njegova vrednost i operacije koje mozemo izvrsavati nad njim.
* Podatak moze biti promenjiva ili konstanta.

#Prosti tipovi podataka

Tipovi ugradjeni u C++.

* `char` znak ili mali broj **[1B]**
* `short` celi broj **[2B]**
* `int` celi broj **[4B]**
* `long` celi broj **[4B]**
* `long long` celi broj **[8B]**
* `float` decimalni broj **[4B]**
* `double`  decimalni broj dvostruke preciznosti **[8B]**
* `bool` logicka vrednost **[1B]**
	* moze imati vrednosti `true` i `false`
	
*[1B]: 1 bajt
*[2B]: 2 bajta
*[4B]: 4 bajta
*[8B]: 8 bajta

Velicina tipa se moze utvrditi operatorom `sizeof`.

**Primer:**

	sizeof(int)

#Celobrojni tipovi podataka

* Svakom celobrojnom tipu moze biti dodat prefiks `unsigned`. To znaci da ce se podatak tog tipa tretirati kao neoznacen ceo broj.
* Oznaceni celi brojevi se pamte u drugom komplementu.
* Opseg u kome se moze nalaziti vrednost podatka nekog celobrojnog tipa zavisi od broja bajtova koje taj podatak zauzima u memoriji.

##Kako odrediti opseg vrednosti nekog celobrojnog tipa?

> **Neka je x broj bitova koje zauzima tip podatka koji analiziramo:**
>
> * Za oznacene brojeve:  
>    od $$0$$ do $$2^x-1$$
> * Za neoznacene brojeve:  
>    od $$-2^{x-1}$$ do $$2^{x-1}-1$$

**Primeri:**

*Koji je opseg tipa unsigned char ?*

> Resenje: od 0 do 255

*Koji je opseg tipa char ?*

> Resenje od -128 do 127

*Koji je opseg tipa int ?*

> Resenje od -231 do 231-1

#Identifikatori

* Imena konstanti, promenjivih, funkcija, ...
* Moraju da pocinju slovom ili znakom '_'
* Sastoje se od slova i cifara
* Ne smeju biti rezervisane reci
* Velika i mala slova se razlikuju

**Primeri:**

	a
	A
	_X
	main
	
#Deklaracija promenjive

	< tip > (< ime_promenjive >( = < vrednost >)?',' )*(< ime_promenjive >( = < vrednost >)?)';'

**Primeri:**

	char separator = ',';
	int suma = 0;
	bool test;
	long long a = 3, b, c = 44;
	
Pocetna vrednost nije obavezna. U tom slucaju promenjiva ima slucajnu pocetnu vrednost.

#Operatori

* U jeziku C++ postoje 3 vrste operatora:
	1. unarni **[U]**  
	
			<oper><promenjiva>
		ili
		
			<promenjiva><oper>
			
	2. binarni **[B]**  
			
			<promenjiva1> <oper> <promenjiva2>
			
	3. ternarni **[T]**  
	
			<promenjiva1> <oper_deo1> <promenjiva2> <oper_deo2> <promenjiva3>
		
* Rezultat primene operatora je ili neka vrednost ili promena objekta nad kojim operator radi.

##Operator dodele **[B]**

Operator dodele u jezik C++ je operator `=`.

**Primer:**

	int a;
	a = 3;
	int b = 2;
	a = b;
	b = 1;
		
*Koju vrednost imaju promenjive `a` i `b` ?*
>`a = 2`, `b = 1`

##Aritmeticki operatori

* `+` sabiranje **[B]**
* `-` oduzimanje **[B]**, negacija **[U]**
* `*` mnozenje **[B]**
* `/` deljenje **[B]**
* `%` ostatak pri deljenju (mod) **[B]**

**Primer:**

	int a = 3, b = 4;
	a = a + b;

*Koju vrednost imaju promenjive `a` i `b` ?*
>`a = 7`, `b = 4`

##Slozeni aritmeticki operatori dodele **[B]**

* `+=`
		
		a += b; // <=> a = a + b;

* `-=`

		a -= b; // <=>  a = a - b;

* `*=`

		a *= b; // <=> a = a * b;

* `/=`

		a /= b; // <=> a = a / b;


* `%=`

		a %= b; // <=> a = a % b;

##Operatori `++` i `--` **[U]**

za `++`

	++x; // <=> x = x + 1;
	x++; // <=> x = x + 1;

analogno i za `--`

	--x; // <=> x = x - 1;
	x--; // <=> x = x - 1;

##Relacioni operatori **[B]**

Relacioni operatori vracaju logicku vrednost.

* `==` jednakost
* `!=` nejednakost
* `>` vece
* `<` manje
* `>=` vece jednako
* `<=` manje jednako

##Logicki operatori

Logicki operatori rade sa logickim vrednostima.

* `!` negacija [U]
* `&&` logicko i [B]
* `||` logicko ili [B]

**Primer:**

	bool test = (a > 0) && !(b < 0);

*Koja je vrednost promenjive test za  `a = 3` i `b = 4` ?*
>Resenje: `true`

##Uslovni operator **[T]**

	< uslov > ? < vrednost1 > : < vrednost2 >

**Primeri:**

	int max = a > b ? a : b; 
	int min = a < b ? a : b;
	
*Kako odrediti max 3 broja koristeci ternarni operator ?*

>		int max_a_b = a > b ? a : b;
>		int max = max_a_b  > c ? max_a_b : c; 

##Napomena

**Postoje i drugi operatori (npr. bitovni operatori) koji ovde nisu obradjeni.**