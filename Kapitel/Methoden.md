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

Als erstes muss man den Rückgabewert spezifizieren, hier ist dieser ein `double`. Dann wählt und schreibt man einen aussagekräftigen Namen. Danach folgen Klammern,  welche **Parameter** beinhalten können. In unserem Beispiel möchten wir die Methode mit einem einzelnen Argument aufrufen und definieren den Parameter `double zahl`. Das Verhalten der Methode wird innerhalb eines Codeblocks `{}` definiert, der in diesem Zusammenhang als **Methodenkörper** bezeichnet wird.

Um von einer Methode einen Wert zurückzugeben muss man das `return`-Schlüsselwort verwenden. An dieser Stelle springt das Programm wieder aus der Methode heraus. 

Wir können die Methode nun im Code wie folgt aufrufen: 

```cs
double d = 1.5;
double quadrat = BerechneQuadrat(d);
Console.WriteLine($"Das Quadrat von {d} ist {quadrat}.");
```

Vielleicht ist dir bereits aufgefallen, dass man bei Methoden zwischen **Parametern** und **Argumenten** unterscheidet. Als Parameter bezeichnet man die Platzhalter innerhalb einer Methode. Unsere Methode oben hat beispielsweise nur den Parameter `double zahl`. Argumente hingegen werden beim Methodenaufruf in die Parameterliste eingesetzt. Im obigen Beispiel ist das Argument folglich `1.5`.

Methoden die keinen Rückgabewert haben müssen das Schlüsselwort `void` als Rückgabetyp aufweisen. Zum Beispiel: 

```cs
void GibDasQuadratAufDerKonsoleAus(double d)
{
    Console.WriteLine($"Das Quadrat von {d} ist {BerechneQuadrat(d)}.");
    return;
}
```

Das `return` Statement in der letzten Zeile der `void` Methode ist optional. Es kann jedoch an anderen Stellen eingesetzt werden um die Methode vorzeitig zu beenden.

Anstelle von Variablen kann man natürlich auch direkt Werte in eine Methode einsetzen:

```cs
GibDasQuadratAufDerKonsoleAus(1.5);
GibDasQuadratAufDerKonsoleAus(4);
```

Hat eine Methode mehrere Parameter, so werden diese durch ein Komma getrennt:

```cs
void Begrüßung(string name1, string name2)
{
    Console.WriteLine($"Herzlich willkommen zum Kurs {name1} und {name2}!";
    return;
}

```

> Mit Methoden können wir unseren Code sehr sprechend gestalten, lege deshalb am besten großen Wert auf die Benennung deiner Methoden. Achte bitte außerdem darauf, dass Methoden im Gegensatz zu Variablen mit einem Großbuchstaben beginnen sollten. 

---

### [Kursinhalt](../README.md)