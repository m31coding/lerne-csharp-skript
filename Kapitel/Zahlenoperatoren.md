### [Kursinhalt](../README.md)

Zahlenoperatoren
=================

Rechenoperatoren
------------------


Zahlentypen wie `int`, `long`, `float` und `double` können durch die üblichen Rechenoperatoren `+`, `-`, `*`, und `/` miteinander verknüpft werden. Hierbei ist die Präzedenz der Operatoren zu beachten (Punkt vor Strich):

```cs
int zahl1 = 2 + 2 * 2; // 6
int zahl2 = (2 + 2) * 2; // 8
```

Mit dem Inkrementierungsoperator `++` kann man eine Zahl um eins erhöhen, und mit dem Dekrementierungsoperator `--` um eins verringern:

```cs
int i = 1;
i++; // i ist nun 2
int j = 10;
j--; // j ist nun 9
```

Mit dem Modulooperator `%` kann der Rest einer Division bestimmt werden:

```cs
int divisionsRest = 11 % 3; // 2
```

Vergleichsoperatoren
--------------------

Desweiteren gibt es eine Reihe von nützlichen Vergleichsoperatoren: `==`, `!=`, `<`, `>`, `<=`, `>=`.
Vergleiche der beiden obigen Zahlen liefern die folgenden Ergebnisse: 

```cs
bool zahlenSindGleich = zahl1 == zahl2; // false
zahl1 != zahl2 // true
zahl1 < zahl2 // true
zahl1 > zahl2 // false
zahl1 <= zahl2 // true
zahl1 >= zahl2 // false
```

---

### [Kursinhalt](../README.md)