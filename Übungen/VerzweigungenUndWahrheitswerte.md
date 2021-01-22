### [Kursinhalt](../README.md)

Übungen zu Verzweigungen und Wahrheitswerten
============================================

Maximum von Zahlen
------------------

Schreibe eine Methode `static double Maximum(double d1, double d2)` die das Maximum zweier Zahlen zurückgibt.

<details><summary><b>Hinweis</b></summary>

- Verwende `if` und `else` oder den bedingten Operator `?:`.
</details>

<details><summary><b>Lösung</b></summary>

```cs
static double Maximum(double d1, double d2)
{
    if(d1 > d2)
    {
        return d1;
    }
    else
    {
        return d2;
    }
}
```
</details>

Zufällige Begrüßung
--------------------

Schreibe eine Methode `static void ZufälligeBegrüßung(string name)` die einen Namen entgegennimmt und eine von drei zufälligen Begrüßungen auf die Konsole schreibt. 

Die Aufrufe 

```cs
ZufälligeBegrüßung("Kevin");
ZufälligeBegrüßung("Alice");
ZufälligeBegrüßung("Bob");
```

könnten zum Beispiel die folgende Ausgabe erzeugen:

```sh
Willkommen zum Programmierkurs Kevin!
Schön dass du mit dabei bist Alice!
Sei gegrüßt Bob!
```

In dieser Methode müssen wir uns eine Zufallszahl generieren. Hierfür können wir die `Random` Klasse verwenden. Mit den folgenden Zeilen kannst du eine zufällige Zahl erzeugen, die entweder 0, 1, oder 2 ist.

```cs
Random zahlengenerator = new Random();
int zufälligeZahl = zahlengenerator.Next(0, 3);
```

<details><summary><b>Hinweis</b></summary>

- Verwende `if`, `else if` und `else`.
</details>

<details><summary><b>Lösung</b></summary>

```cs
static void ZufälligeBegrüßung(string name)
{
    Random zahlengenerator = new Random();
    int zufälligeZahl = zahlengenerator.Next(0, 3);

    if(zufälligeZahl == 0)
    {
        Console.WriteLine($"Willkommen zum Programmierkurs {name}!");
    }
    else if(zufälligeZahl == 1)
    {
        Console.WriteLine($"Schön dass du mit dabei bist {name}!");
    }
    else
    {
        Console.WriteLine($"Sei gegrüßt {name}!");
    }
}
```
</details>


Bonusaufgaben
==============

Test ob eine Zahl ungerade ist
-----------------------------

Schreibe eine Methode `static bool ZahlIstUngerade(int zahl)` die testet ob eine Zahl ungerade ist, ohne dabei den Modulooperator direkt zu verwenden.

<details><summary><b>Hinweis</b></summary>

- Verwende deine Methode `static ZahlIstGerade`
</details>

<details><summary><b>Lösung</b></summary>

```cs
static bool ZahlIstUngerade(int zahl)
{
    return !ZahlIstGerade(zahl);
}
```

</details>

Maximum von drei Zahlen
-----------------------

Schreibe eine Methode `static double Maximum(double d1, double d2, double d3)` die das Maximum von drei Zahlen zurückgibt.

<details><summary><b>Lösung</b></summary>

```cs
static double Maximum(double d1, double d2, double d3)
{
    if (d1 > d2 && d1 > d3)
    {
        return d1;
    }
    else if(d2 > d1 && d2 > d3)
    {
        return d2;
    }
    else
    {
        return d3;
    }
}
```

</details>

<details><summary><b>Elegantere Lösung</b></summary>

Verwende deine Maximum Methode für zwei Zahlen:

```cs
static double Maximum(double d1, double d2, double d3)
{
    return Maximum(d1, Maximum(d2, d3));
}
```

</details>

### [Kursinhalt](../README.md)