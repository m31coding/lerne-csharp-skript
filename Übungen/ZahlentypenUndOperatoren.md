### [Kursinhalt](../README.md)

Übungen zu Zahlentypen und Operatoren
===================================

Lege eine `double` Variable mit dem Namen `zahl1` an und eine `int` Variable mit dem Namen `zahl2`. Setze außerdem Werte, zum Beispiel `3.5` und `2`.

<details>
  <summary><b>Lösung</b></summary>

```cs
double zahl1 = 3.5;
int zahl2 = 2;
```
</details>

Definiere `double` Variablen `summe`, `differenz`, `produkt` und `quotient` und speichere darin das Ergebnis der entsprechenden Rechenoperationen.

<details>
  <summary><b>Lösung</b></summary>

```cs
double zahl1 = 3.5;
int zahl2 = 2;

double summe = zahl1 + zahl2;
double differenz = zahl1 - zahl2;
double produkt = zahl1 * zahl2;
double quotient = zahl1 / zahl2;
```
</details>

Gebe jedes Ergebnis in einer Zeile auf der Konsole aus, in etwa wie folgt:

```sh
Die Summe aus 3,5 und 2 ist 5,5.
Die Differenz aus 3,5 und 2 ist 1,5.
Das Produkt aus 3,5 und 2 ist 7.
Der Quotient aus 3,5 und 2 ist 1,75.
```

Aufgrund deiner Spracheinstellungen wird bei dir wahrscheinlich genauso wie bei mir der Wert `3.5` als `3,5` auf der Konsole ausgeben. Lass dich davon aber einfach nicht weiter beirren.


<details>
  <summary><b>Lösung</b></summary>

```cs
double zahl1 = 3.5;
int zahl2 = 2;

double summe = zahl1 + zahl2;
double differenz = zahl1 - zahl2;
double produkt = zahl1 * zahl2;
double quotient = zahl1 / zahl2;

Console.WriteLine($"Die Summe aus {zahl1} und {zahl2} ist {summe}.");
Console.WriteLine($"Die Differenz aus {zahl1} und {zahl2} ist {differenz}.");
Console.WriteLine($"Das Produkt aus {zahl1} und {zahl2} ist {produkt}.");
Console.WriteLine($"Der Quotient aus {zahl1} und {zahl2} ist {quotient}.");
```
</details>

Ändere nun deine beiden ersten Zeilen zu

```cs
int zahl1 = 3;
int zahl2 = 2;
```

und führe das Programm aus. Was ist auffällig?

<details>
  <summary><b>Lösung</b></summary>

```sh
Der Quotient aus 3 und 2 ist 1.
```
</details>

<details>
  <summary><b>Erklärung</b></summary>

Obwohl das Ergebnis von `zahl1 / zahl2` in einen `double` Wert gespeichert wird, wird zunächst eine `int` Division ausgeführt. Das Ergebnis hiervon ist wiederum ein `int`, sodass der Dezimalteil einfach abgeschnitten wird. Um das Problem zu umgehen kann man eine der beiden Zahlen in der Berechnung zu einem `double` konvertieren. Dies geschieht wie folgt: `double quotient = zahl1 / (double) zahl2;`
</details>


---

### [Kursinhalt](../README.md)