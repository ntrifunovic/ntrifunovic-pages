topic: Grafovi
title: Obilasci grafova

[TOC]

---

#Pretraga u širinu (BFS eng. Breadth first search)

Ovaj algoritam prvo posećuje početni čvor,  
zatim posećuje sve njegove susede,  
zatim posećuje sve njihove neposećene susede,  
...

Algoritam završava rad kada nema više ne posećenih suseda.

**Predlog implementacije:**

1. Početni čvor se stavi na početak praznog reda
2. Uzima se čvor sa početka reda i njegovi ne posećeni susedi se dodaju na kraj reda
3. Ako red nije prazan prelazi se na korak 2,  
   u suprotnom je kraj izvršavanja algoritma

Prikaz obilaska grafa dobijenog BFS algoritmom:  
  
![Prikaz rada BFS algoritma](/static/grafovi/Breadth-first-tree.svg)

#Pretraga u dubinu (DFS eng. Depth first search)

Rekurzivni DFS algoritam:

	DFS(x):
		for y in susedi od x
			if y nije posecen
				DFS(y)

Prikaz obilaska grafa dobijenog DFS algoritmom:  

![Prikaz rada DFS algoritma](/static/grafovi/Depth-first-tree.svg)