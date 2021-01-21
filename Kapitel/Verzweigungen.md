### [Kursinhalt](../README.md)

Verzweigungen
==============

In vielen Situationen wollen wir einen Teil eines Programms nur dann ausführen wenn eine bestimmte Bedingung gegeben ist. Dies kann durch den **if Ausdruck** programmiert werden.

```cs
if(bedingung)
{
  // führe diesen Code aus
}
```

Der obige Code wird nur genau dann ausgeführt wenn die Bedingung den Wert `true` hat, ansonsten wird der Block übersprungen.

Ein **if-else Ausdruck** kann verwendet werden um verschiedene Abzweigungen abzubilden:

```cs
if(bedingung)
{
  // führe diesen Code aus
}
else
{
  // führe jenen Code aus
}
```

Mehrere Bedingungen, welche der Reihe nach geprüft werden, können durch das Schlüsselwort **else if** ausgedrückt werden:

```cs
if(bedingung1)
{
  // ...
}
else if(bedingung2)
{
  // ...
}
else if(bedingung3)
{
  // ...
}
else
{
  // ...
}
```

Da es sich bei den Blöcken `{}` um gewöhnliche Codeblöcke handelt können darin erneut if-else Ausdrücke enthalten sein, sodass verschachtelte Ausdrücke keine Seltenheit sind. 
Es folgt ein Beispiel für verschachtelte Ausdrücke wie sie in einem Spiel vorkommen könnten:


```cs
if(spielBeendet)
{
  if(spieler1HatGewonnen)
  {
    Console.WriteLine("Spieler 1 hat gewonnen!");
  }
  else
  {
    Console.WriteLine("Spieler 2 hat gewonnen!");
  }
}
else
{
  Console.WriteLine("Der nächste Zug beginnt!");
}
```

Als Argument für eine Verzweigung kann natürlich auch ein Methodenaufruf eingesetzt werden, solange es sich um eine Methode handelt die `true` oder `false` zurückgibt. Zum Beispiel:

```cs
if (SpielBeendet(punkteSpieler1, punkteSpieler2))
{
  Console.WriteLine($"Das Spiel ist aus! Punkte Spieler 1 = {punkteSpieler1}. Punkte Spieler 2 = {punkteSpieler2}.");
}
```

Bedingter Operator
--------------------

Ein if-else Ausdruck in dem ein Wert berechnet oder gesetzt wird kann durch den bedingten Operator `?:` abgekürzt werden:

```
bedingung ? konsequenz : alternative
```

Beispielsweise kann 

```cs
string ausgabe = string.Empty;

if(spieler1HatGewonnen)
{
  ausgabe = "Spieler 1 hat gewonnen!";
}
else
{
  ausgabe = "Spieler 2 hat gewonnen!";
}

Console.WriteLine(ausgabe);
```

geschrieben werden als

```cs
string ausgabe = spieler1HatGewonnen ? "Spieler 1 hat gewonnen!" : "Spieler 2 hat gewonnen!";
Console.WriteLine(ausgabe);
```

---

### [Kursinhalt](../README.md)