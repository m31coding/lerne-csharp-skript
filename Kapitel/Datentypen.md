### [Kursinhalt](../README.md)

Datentypen
===========

In diesem Abschnitt diskutieren wir die Datentypen, die direkt in der Sprache integriert sind, diese werden auch integrierte Datentypen genannt.

 Primitive Datentypen
 --------------------

Die einfachsten und am häufigsten verwendeten Datentypen eines Programms sind **Zahlen**, **Zeichen**, und **Wahrheitswerte**. Die Typen für ganze Zahlen (integers) sind:

- `int`: von ca. -2 Milliarden bis +2 Milliarden (9 Nullen)
- `long`: von ca. -9 Trillionen bis ca. +9 Trillionen (18 Nullen)

Gleitkommazahlen (floating-point numbers) können durch die folgenden Typen repräsentiert werden:

- `float`: ca. 7 Nachkommastellen
- `double`: ca. 15 Nachkommastellen

Zusätzlich gibt es noch Zeichen (characters) und Wahrheitswerte (boolean values):

- `char`, zum Beispiel 'a', 'x', '2', '!'
- `bool`: true / false

TODO: 234.0f, 234234L

### Wie entscheide ich welchen Zahlentyp ich verwenden soll?

Für ganze Zahlen reicht es in den meisten Fällen aus ein `int` zu verwenden. Benötigst du allerdings ganze Zahlen über zwei Milliarden wählst du ein `long`. Für Gleitkommazahlen wählst du normalerweise den Type `double` aus. Dieser hat eine höhere Genauigkeit bei Berechnungen als `float` und du bist dadurch auf der sicheren Seite. 

Strings
--------

Ein `string` stellt eine Zeichenkette dar und muss in doppelte Anführungszeichen gesetzt werden: 

```cs
string begrüßung = "Herzlich Willkommen zum Programmierkurs";
```

Auf einem string lassen sich zahlreiche nützliche Eigenschaften und Methoden aufrufen, zum Beispiel `Length`, `Contains`, und `ToLower`. Eine Übersicht über alle Funktionalitäten finden sich in der [Dokumentation](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=net-5.0).

Weitere Typen
--------------

Weitere zusammengesetzten Datentypen sind beispielsweise Listen, Mengen, und vom Programmierer definierte Typen. Diese werden in einem späteren Kapitel behandelt.

---

### [Kursinhalt](../README.md)
