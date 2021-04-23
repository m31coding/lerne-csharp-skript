### [Kursinhalt](../README.md)

IEnumerable
============

Listen und Arrays implementieren beide die **Schnittstelle** `IEnumerable<T>`. Das `I` steht hierbei für Interface, dem englischen Wort für Schnittstelle. Eine Schnittstelle definiert einen Vertrag, der von den Typen, die diese Schnittstelle implementieren, eingehalten werden muss. Die Schnittstelle `IEnumerable<T>` definiert Methoden um über Elemente vom Typ `T` zu iterieren. Enumerable heißt nichts weiter als **Auflistung**.

Sowohl Listen als auch Arrays können implizit in den Schnittstellentyp konvertiert werden: 

```cs
IEnumerable<int> zahlen = new int[]{2, 11, -4, 7};
```

und

```cs
IEnumerable<int> zahlen = new List<int>(){2, 11, -4, 7};
```

Für das `IEnumerable` gibt es eine spezielle Schleife, die `foreach` Schleife:

```cs
foreach(int zahl in zahlen)
{
    Console.WriteLine(zahl);
}
```

Man kann also ganz ohne einen Index sehr bequem auf alle Elemente der Auflistung nacheinander zugreifen.

LINQ
=====

LINQ (Language Integrated Query, sprich 'Link') stellt viele nützliche Methoden bereit, mit denen wir Objekte, welche die Schnittstelle `IEnumerable<T>` implementieren, abfragen und manipulieren können.

Hier sind einige Beispiele:

```cs
IEnumerable<int> zahlen = new List<int>() { 2, 11, -4, 7 };
zahlen.Count() // 4
zahlen.Min() // -4
zahlen.Max() // 11
zahlen.Sum() // 16
zahlen.First() // 2
zahlen.Last() // 7
zahlen.Take(2) // 2, 11
zahlen.Skip(1) // 11, -4, 7
zahlen.Skip(1).Take(2) // 11, -4
```

Wie das letzte Beispiel zeigt, sind die LINQ Methoden auch sehr gut für Verkettungen geeignet.

Einige Methoden nehmen eine Funktion als Argument entgegen, die sehr bequem durch einen sogenannten Lambdaausdruck definiert werden kann:

```cs
zahlen.Any(z => z < 5) // true
zahlen.All(z => z >= 0) // false
zahlen.Count(z => z % 2 == 0); // 2
```

Sehr häufig gebraucht wird die Methode `Where`, mit der man filtern kann, sowie die Methode `Select`, mit der man Elemente transformieren kann:

```cs
zahlen.Where(z => z > 0) // 2, 11, 7
zahlen.Select(z => z * 2) // 4, 22, -8, 14
zahlen.Where(z => z > 0).Select(z => z * 2) // 4, 22, 14
```

Es gibt außerdem nützliche Methoden zur Sortierung von `IEnumerable`-Objekten:

```cs
zahlen.OrderBy() // -4, 2, 7, 11
zahlen.OrderBy(z => z * z) // 2, -4, 7, 11
zahlen.OrderByDescending(z => z) // 11, 7, 2, -4
```

Zuletzt möchte ich noch die `Aggregate` Methode nicht unerwähnt lassen. Sie formt aus einem aggregierten Wert und dem nächsten Element der Auflistung einen neuen aggregierten Wert.

```cs
zahlen.Aggregate((z1, z2) => z1 * z2) // 2 * 11 * -4 * 7 = -616
```

Bei allen `IEnumerable`-Methoden ist zu beachten, dass sie funktional definiert sind. Das heißt sie verändern das Objekt auf dem sie aufgerufen werden nicht sondern geben ein neues Objekt zurück. Typischerweise gibt man das Ergebnis deshalb direkt in eine andere Methode oder speichert es in einer Variable. Hierzu sind die Methoden `ToList` und `ToArray` hilfreich, die eine Konvertierung in den entsprechenden Typ vornehmen. Zum Beispiel:

```cs
List<int> zahlenSortiert = zahlen.OrderBy(z => z).ToList();
```

Eine Übersicht über alle Enumerable Methoden in LINQ findest du hier in der Dokumentation: https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable?view=net-5.0

Verzögerte Ausführung
---------------------

Eine Besonderheit und Stärke von LINQ ist die iterative und zugleich verzögerte Ausführung.

Beispielsweise hat die zweite Zeile in 

```cs
IEnumerable<int> zahlen = new List<int>() { 2, 11, -4, 7 };
IEnumerable<int> positiveZahlen = zahlen.Where(z => z > 0);
```

zunächst keinerlei Auswirkung. Der `Where` Filter wird an dieser Stelle **noch nicht** ausgeführt.

Erst wenn wir über die variable `positiveZahlen` iterieren oder sie in eine Liste oder Array konvertieren wird der Filter angewandt.

```cs
foreach(zahl in positiveZahlen)
{
    Console.WriteLine(zahl);
}

List<int> positiveZahlenListe = positiveZahlen.ToList();
int[] positiveZahlenArray = positivieZahlen.ToArray();
```

Andererseits wird in diesem Beispiel der Filter dreimal von neuem angewandt, sodass man sich Gedanken darüber machen sollte, wann man über ein `IEnumerable` iteriert oder es konvertiert.


---

>In diesem Kapitel hast du LINQ kennengelernt, eines der mächtigsten Features in C#. Es kann nicht nur für Objekte vom Typ `IEnumerable` verwendet werden wie zum Beispiel Listen und Arrays. Man kann damit sogar auch Abfragen für Datenbanken und XML-Dokumente erstellen.

---
### [Kursinhalt](../README.md)