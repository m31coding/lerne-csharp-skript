### [Kursinhalt](../README.md)

Methoden
========

Eine Methode (oder auch Funktion) ist ein Stück Code welcher für eine bestimmte Sache zuständig ist und immer wieder aufgerufen werden kann. Eine Methode kann Werte entgegennehmen (**Argumente**) und auch einen Wert zurückgeben (**Rückgabewert**). 

Um eine eigene Methode zu definieren müssen wir angeben mit welchen Typen die Methode arbeitet. Eine Methode die das Quadrat eines `double` Wertes berechnet sieht beispielsweise wie folgt aus:

```cs
double BerechneQuadrat(double zahl)
{
    return zahl * zahl;
}

```

Als erstes muss man den Rückgabewert spezifizieren, hier ist dieser ein `double`. Dann wählt und schreibt man einen aussagekräftigen Namen. Danach folgen Klammern,  welche Parameter beinhalten können. In unserem Beispiel möchten wir die Methode mit einem einzelnen Argument aufrufen können und definieren den Parameter `double zahl`.
Das `return` Schlüsselwort sorgt dafür, dass das Ergebnis der Berechnung von der Methode zurückgegeben wird.

Die Methode kann nun im Code aufgerufen werden: 

```cs
double d = 1.5;
double quadrat = BerechneQuadrat(d);
Console.WriteLine($"Das Quadrat von {d} ist {quadrat}.");
```

Hier ist ein weiteres Beispiel für eine Methode die überprüft ob eine Zahl gerade ist.

```cs
int ZahlIstGerade(int zahl)
{
    return zahl % 2 == 0;
}

```

Methoden die keinen Rückgabewert haben müssen das Schlüsselwort `void` als Rückgabetyp aufweisen. Zum Beispiel: 

```cs
void GibDasQuadratAufDerKonsoleAus(double d)
{
    Console.WriteLine($"Das Quadrat von {d} ist {BerechneQuadrat(d)}.");
}

```

Wie du siehst kann man auch problemlos innerhalb einer Methode eine andere Methode aufrufen.

Eine `void` Methode kann durch das Schlüsselwort `return` abgebrochen werden:
```cs
void Begrüßung(d)
{
    Console.WriteLine("Herzlich willkommen");
    return;
    Console.WriteLine("zum Programmierkurs");
}

```

Diese Methode gibt nur die Zeile `Herzlich willkommen` aus.

Achte bei Methoden darauf, dass diese im Gegensatz zu Variablen mit einem Großbuchstaben beginnen. 

---

### [Kursinhalt](../README.md)