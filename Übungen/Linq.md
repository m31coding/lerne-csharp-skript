### [Kursinhalt](../README.md)

Übungen zu LINQ
================

Vorbereitung
-------------

Für diese Übung habe ich eine separate Projektmappe vorbereitet, die du auf [dieser Seite](https://github.com/m31coding/lerne-csharp-uebungen) herunterladen kannst. Klicke hierzu einfach auf den grünen Button **Code** und wähle **Download ZIP**. Im Anschluss kann der Ordner entpackt werden indem du in Windows einen rechtsklick darauf machst und **Alle extrahieren** auswählst. Zu guter Letzt kannst du die Projektmappe **LerneCSharpÜbungen.sln** mit einem Doppelklick öffnen.

Beschreibung
-------------

Ich habe für euch Daten der besten 1000 Schachspieler vorbereitet. In der Datei **schachspieler.json** befindet sich für jeden Spieler ein Eintrag für seinen Namen, sein Geburtsjahr, seine Elo-Zahl (Spielstärke) und den aktuellen Weltranglistenplatz. Aus diesen Daten generieren wir im Code eine Liste aus Objekten des Typs **Schachspieler**. Ein Schachspielerobjekt hat die folgenden Eigenschaften:

- Name
- Alter
- Elo

Verwende die Liste `List<Schachspieler> spieler` um die unten stehenden Abfragen mit Hilfe von LINQ zu kreieren. 

Ist das Ergebnis einer Abfrage eine Auflistung (`IEnumerable`), verwende die Methode `Konsolenausgabe<T>(IEnumerable<T> auflistung)` um das Ergebnis auf der Konsole darzustellen. Der Grund hierfür ist, dass es keine sinnvolle Überladung der Methode `Console.WriteLine` gibt, die ein `IEnumerable` entgegennimmt. Außerdem beschränkt die Funktion **Konsolenausgabe** die Ausgabe für eine bessere Übersicht auf vier Elemente der Auflistung. 

Für Abfragen die eine Zahl oder einen anderen primitiven Wert zurückgeben kannst du einfach wie gewohnt `Console.WriteLine` verwenden. Viel Spaß und Erfolg bei der Übung!

Übungen
--------

---

```cs
Console.WriteLine("Alphabetisch nach Namen sortiert:");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende OrderBy.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Konsolenausgabe(spieler.OrderBy(s => s.Name));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Nach Spielerstärke (Elo) sortiert (stärkste zuerst):");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende OrderByDescending.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Konsolenausgabe(spieler.OrderByDescending(s => s.Elo));

```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Die höchste Elo-Zahl:");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die Max-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Console.WriteLine(spieler.Max(s => s.Elo));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Anzahl Spieler mit einer Elo-Zahl > 2600:");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die Count-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Console.WriteLine(spieler.Count(s => s.Elo > 2600));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Haben alle Spieler eine Elo-Zahl > 2500?");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die All-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Console.WriteLine(spieler.All(s => s.Elo > 2500));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Gibt es Spieler mit einer Elo-Zahl > 2600, die 60 Jahre oder älter sind?");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die Any-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Console.WriteLine(spieler.Any(s => s.Elo > 2600 && s.Alter >= 60));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Der jüngste Spieler ist:"); // verwende Aggregate
```

<details>
<summary><b>Hinweis</b></summary>
Der neue aggregierte Spieler ist der Jüngere von dem aktuellen aggregierten Spieler und dem Nächsten. 
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Console.WriteLine(spieler.Aggregate((s1, s2) => s1.Alter < s2.Alter ? s1 : s2));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Der älteste Spieler ist:"); // verwende Aggregate
```

<details>
<summary><b>Hinweis</b></summary>
Der neue aggregierte Spieler ist der Ältere von dem aktuellen aggregierten Spieler und dem Nächsten. 
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Console.WriteLine(spieler.Aggregate((s1, s2) => s1.Alter > s2.Alter ? s1 : s2));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Spieler unter 18 mit einer Elo-Zahl > 2500:");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die Where-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Konsolenausgabe(spieler.Where(s => s.Alter < 18 && s.Elo > 2500));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Die Namen der Spieler:");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die Select-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Konsolenausgabe(spieler.Select(s => s.Name));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Namen der Spieler mit einer Elo-Zahl über 2600:");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die Where- und die Select-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Konsolenausgabe(spieler.Where(s => s.Elo > 2600).Select(s => s.Name));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Die Namen der 3 jüngsten Spieler:");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die OrderBy-, die Take-, und die Select-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Konsolenausgabe(spieler.OrderBy(s => s.Alter).Take(3).Select(s => s.Name));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Der älteste Spieler mit einer Elo-Zahl > 2600:");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die OrderByDescending- und die First-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Console.WriteLine(spieler.OrderByDescending(s => s.Alter).First(s => s.Elo > 2600));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Der beste Spieler unter 18:");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die Where-, die OrderByDescending-, und die First-Methode.
<br>
Alternativ: Verwende die Where- und die Aggregate-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Console.WriteLine(spieler.Where(s => s.Alter < 18).OrderByDescending(s => s.Elo).First());
```
</details>

<details>
<summary><b>Alternative Lösung</b></summary>
<br>

```cs
Console.WriteLine(spieler.Where(s => s.Alter < 18).Aggregate((s1, s2) => s1.Elo > s2.Elo ? s1 : s2));
```
</details>

---

```cs
Console.WriteLine($"{Environment.NewLine}Der zweit, dritt, und viert beste Spieler unter 18:");
```

<details>
<summary><b>Hinweis</b></summary>
Verwende die Where-, die OrderByDescending-, die Skip-, und die Take-Methode.
</details>

<details>
<summary><b>Lösung</b></summary>
<br>

```cs
Konsolenausgabe(spieler.Where(s => s.Alter < 18).OrderByDescending(s => s.Elo).Skip(1).Take(3));
```
</details>

---

### [Kursinhalt](../README.md)
