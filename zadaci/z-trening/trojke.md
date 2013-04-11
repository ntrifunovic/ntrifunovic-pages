title: Z-trening \ Trojke
topic: Zadaci

#[Z-trening \ Trojke](http://z-trening.com/tasks.php?show_task=5000000125)

Profesor matematike je postavio Dragancetu sledeci zadatak. Na osnovu datog niza brojeva `a[1]`, `a[2]`, ..., `a[n]`, Dragance treba da za svaku trojku indeksa (`i`, `j`, `k`), gde je `1 <= i < j < k <= n`, napiše na tabli najveci od brojeva `a[i]`, `a[j]` i `a[k]`. Zatim treba da izracuna ostatak koji daje zbir svih brojeva koji su napisani na tabli pri deljenju sa `10007`. Profesor je obecao Dragancetu peticu za kraj školske godine, ako dobije tacno rešenje pre kraja casa. Pomozite Dragancetu da što brže dobije tacan rezultat. 

**Ulaz:**

(Ulazni podaci se citaju sa standardnog ulaza) U prvom redu nalazi se broj `n` (`3 <= n <= 30000`). U sledecih n redova se nalaze celi brojevi `a[1]`, `a[2]`, ..., `a[n]`, pri cemu je `-100000 <= a[i] <= 100000`. 

**Izlaz:**

(Izlazne podatke ispisati na standardni izlaz) U prvom i jedinom redu ispisati sumu brojeva napisanih na tabli po modulu `10007`. 

*Primeri:*

> Ulaz:
> 4
> 3
> -1
> 2
> 2
> 
> Izlaz:
> 11
> 
> Objašnjenje.
> Sve trojke niza brojeva su: (3, -1, 2), (3, -1, 2), (3, 2, 2), (-1, 2, 2). Na tabli su napisani brojevi 3, 3, 3, 2, pa je rešenje u ovom slucaju 11.
> 
> Ulaz:
> 6
> 8
> -10
> 4
> 5
> 2
> 6
> 
> Izlaz:
> 135

---

##Resenje:

	:::C++
	#include<stdio.h>
	#include<algorithm>
	
	using namespace std;
	 
	#define MOD 10007
	#define MAXN 30000
	 
	int a[MAXN];
	 
	int n;
	long long ret;
		 
	int main() {
	 scanf("%d", &n);
	 
	 for(int i = 0; i < n; i++)
	  scanf("%d", &a[i]);
	 
	 sort(a, a+n);
	 reverse(a, a+n);
	 
	 for(int i = 0; i < n-2; i++) {
	   ret += (((n - i-1)*(n - i-2)/2) % MOD)*((a[i] + 100 * MOD) % MOD);
	   ret %= MOD;
	 }
	 
	 printf("%d", ret);
	 
	 getchar();
	 getchar();
	 
	 return 0;
	}
