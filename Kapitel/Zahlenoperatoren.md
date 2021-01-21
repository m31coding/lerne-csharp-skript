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

Die `+=` und `-=` Operatoren sind nützlich um eine Erhöhung oder Verminderung einer Zahl kompakt zu schreiben.
So kann beispielsweise 

```cs
zahl1 = zahl1 + 3;
```

geschrieben werden als

```
zahl1 += 3;
```

Analog zu den Operatoren `+=` und `-=` gibt es auch die Operatoren `*=` und `/=`:

```cs
zahl1 *= 4; // Die Zahl wird vervierfacht.
zahl2 /= 2; // Die Zahl wird halbiert.
```

Da man eine Erhöhung oder Verminderung einer Zahl um `1` besonders häufig benötigt gibt es hierfür nochmal zusätzliche Operatoren, den sogenannten Inkrementierungsoperator `++` und den Dekrementierungsoperator `--`:

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

Des weiteren gibt es eine Reihe von nützlichen Vergleichsoperatoren: `==`, `!=`, `<`, `>`, `<=`, `>=`. Diese haben als Rückgabewert einen `bool`, wie die folgenden Beispiele zeigen:

```cs
int zahl1 = 6;
int zahl2 = 8;
bool zahlenSindGleich = zahl1 == zahl2; // false
zahl1 != zahl2 // true
zahl1 < zahl2 // true
zahl1 > zahl2 // false
zahl1 <= zahl2 // true
zahl1 >= zahl2 // false
```

---

### [Kursinhalt](../README.md)