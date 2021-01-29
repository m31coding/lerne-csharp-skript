### [Kursinhalt](../README.md)

Listen und Arrays
==================

Bisher haben wir für jeden Wert den wir speichern wollten eine extra Variablen angelegt.
In diesem Kapitel lernen wir Datenstrukturen kennen, die es uns ermöglichen mehrere Werte in einer einzelnen Variablen zu speichern und somit zusammengehörige Werte zusammenzufassen.

Listen
======

Eine Liste ist vom Typ `List<T>`, wobei `T` ein Platzhalter für den Typ der Elemente ist die die Liste aufnehmen soll. Man spricht deshalb auch von `List<T>` als einem *generischen* Typ. 

Wir können eine leere Liste mit Strings wie folgt definieren und initialisieren:

```cs
List<string> namen = new List<string>();
```

Der Typ `List<T>` ist eine Klasse und um ein Listenobjekt zu erzeugen brauchen wir das `new` Schlüsselwort gefolgt vom Typ und runden Klammern. Dies stellt eine spezielle Methode dar um Objekte zu erstellen, sie wird *Konstruktor* genannt, dazu erfahren wir mehr im Kapitel über Klassen.

Wir können nun Elemente mittels der `Add` Methode hinzufügen;

```cs
namen.Add("Kevin");
namen.Add("Alice");
namen.Add("Bob");
```

Alternativ können wir auch direkt bei der Konstruktion der Liste Elemente setzen:

```cs
List<string> namen = new List<string>() { "Kevin", "Alice", "Bob" };
```

Die `Count` Eigenschaft gibt uns Auskunft über die Anzahl Elemente in der Liste:

```cs
int anzahlNamen = namen.Count; // 3
```

Wir können durch einen `int` Index auf die einzelnen Elemente in der Liste zugreifen:

```cs
Console.WriteLine(namen[0]); // Kevin 
Console.WriteLine(namen[1]); // Alice
Console.WriteLine(namen[2]); // Bob
```

Analog hierzu kann ein Element gesetzt werden:

```cs
namen[1] = "Carol";
Console.WriteLine(namen[1]); // Carol
```

Um ein Element an einer bestimmten Position zu entfernen verwenden wir die `RemoveAt` Methode: 

```cs
namen.RemoveAt(2); // Entfernt Bob.
```

Alternativ kann auch die `Remove` Methode verwendet werden und das Element angegeben werden:

```cs
namen.Remove("Kevin"); 
```

Und um schließlich die gesamte Liste zu leeren schreiben wir:

```cs
namen.Clear();
```

Listen haben noch einige weitere nützliche Methoden, wie zum Beispiel `AddRange`, `Contains`, und `Sort`.

Eine vollständige Übersicht über alle Konstruktoren, Eigenschaften, und Methoden findet ihr in der MSDN Dokumentation: https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.


> Um Listen verwenden zu können benötigen wir einen Verweis auf den richtigen Namensraum. Diesen erhalten wir mit der Zeile `using System.Collections.Generic;`. Das müssen wir allerdings keinesfalls auswendig wissen, denn Visual Studio kann diese Zeile automatisch einfügen. Wenn du beispielsweise `List<string>` eintippst kannst du dir von Visual Studio mittels STRG+. vorschlagen lassen den richtigen Namensraum oben in die Codedatei einfügen zu lassen. Einmal mit der Eingabetaste bestätigen und schon ist die rote Schlangenlinie verschwunden.

Arrays
======

---



Iterieren mit foreach


LINQ
=====

### [Kursinhalt](../README.md)