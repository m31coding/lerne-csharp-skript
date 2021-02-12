### [Kursinhalt](../README.md)

Listen und Arrays
==================

Bisher haben wir für jeden Wert den wir speichern wollten eine extra Variable angelegt.
In diesem Kapitel lernen wir **Datenstrukturen** kennen die es uns ermöglichen **mehrere Werte** in einer einzelnen Variablen zu speichern und somit zusammengehörige Werte zusammenzufassen.

Listen
======

Eine Liste ist vom Typ `List<T>`, wobei `T` ein Platzhalter für den Typ der Elemente ist die die Liste aufnehmen soll. Man spricht deshalb auch von `List<T>` als einem *generischen* Typ. Man kann sich diesen Syntax merken, indem man bei `<T>` an eine Tasse Tee denkt, das `T` ist in der Tasse `<>` :).

Wir können eine leere Liste mit Strings wie folgt deklarieren und initialisieren:

```cs
List<string> namen = new List<string>();
```

Der Typ `List<T>` ist eine Klasse und um ein Listenobjekt zu erzeugen brauchen wir das `new` Schlüsselwort, gefolgt vom Typ und runden Klammern. Dies stellt eine spezielle Methode dar, um Objekte zu erstellen. Sie wird *Konstruktor* genannt und dazu erfahren wir mehr im Kapitel über Klassen.

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

Es ist zu beachten dass das erste Element nicht den Index `1`, sondern den Index `0` hat.

Mit dem gleichen Syntax auch ein Wert gesetzt werden:

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

Arrays bieten ähnliche Funktionalitäten wie Listen, sind etwas performanter aber dafür weniger flexibel. Der Grund hierfür ist dass ein Array eine **feste** Anzahl Elemente beinhaltet.

Wenn wir ein Array definieren, müssen wir also direkt die Anzahl an Elementen spezifizieren:

```cs
string[] namen = new string[3];
```

Analog zu Listen können wir Elemente mit einem Index setzen:

```cs
namen[0] = "Kevin";
namen[1] = "Alice";
namen[2] = "Bob";
```

Die Deklaration und Initialisierung kann wiederum auch in einer Zeile erfolgen:

```cs
string[] namen = new string[] { "Kevin", "Alice", "Bob" };
```

Anstelle der `Count` Eigenschaft gibt es bei Arrays die `Length` Eigenschaft:

```cs
int anzahlNamen = namen.Length;
```

Aufgrund der festen Länge haben Arrays weniger Methoden als Listen, es gibt zum Beispiel keine `Add` oder `Remove` Methode.


Array mit Standardwerten
------------------------

Ein Array das nicht explizit mit Werten initialisiert wird, enthält automatisch für jedes Element den Standardwert. Beispielsweise enthält das Array

```cs
int[] zahlen = new int[5];
```

fünfmal den Wert `0`. Der Standardwert für Klassenobjekte ist ein spezieller Wert, nämlich `null` (dazu später mehr):

```cs
string[] namen = new string[3]; // {null, null, null}
```

Mehrdimensionale Arrays
-----------------------

Arrays bieten die Möglichkeit Werte in mehreren Dimensionen abzuspeichern. Ein zweidimensionales Array kann man sich beispielsweise als Tabelle oder Gitter vorstellen.

Um beispielsweise ein TicTacToe Spielbrett zu modellieren ist ein zweidimensionales Array sehr gut geeignet:

```cs
string[,] spielbrett = new string[3, 3];
spielbrett[0, 2] = "Kreuz"; // Setze ein Kreuz in Zeile 0, Spalte 2.
spielbrett[1, 1] = "Kreis"; // Setze einen Kreis in die Mitte des Bretts.
```

Wie du siehst werden bei solch einem Array die Dimensionen einfach durch ein Komma abgetrennt.

> Anmerkung: Wir verwenden für das TicTacToe Spielbrett ein Array mit einem selbst definierten Typ anstelle eines String-Arrays, dazu später mehr!

---

> Du hast die Grundlagen von Listen und Arrays verinnerlicht, spitzenmäßig! Diese Datenstrukturen wirst du beim Programmieren sehr häufig benötigen. Verwende ein Array wenn die Elementanzahl von vornherein bekannt ist und sich nicht verändert. Andernfalls verwende eine Liste. 


---
### [Kursinhalt](../README.md)