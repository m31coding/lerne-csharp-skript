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

Gleitkommazahlen werden in C# mit einem Punkt getrennt! Zum Beispiel stellt `3.1415` ein `double` dar, bei `3,1415` handelt es sich jedoch um einen Syntaxfehler.

Um `float` Werte von `double` Werten zu unterscheiden, erhalten diese ein `f` als Suffix: `3.1415f`. Analog erhalten `long` Werte ein `L` als Suffix um sie von `int` Werten unterscheiden zu können. Die folgenden Beispiele zeigen wie wir Variablen der unterschiedlichen Typen anlegen können:

```cs
char ausrufezeichen = '!';
bool spieler1HatGewonnen = true;
int punkteSpieler1 = 100;
long anzahlMenschenAufErde = 7800000000L;
float schulnote = 1.25f;
double pi = 3.14159265359;
```


### Wie entscheide ich welchen Zahlentyp ich verwenden soll?

Für ganze Zahlen reicht es in den meisten Fällen aus ein `int` zu verwenden. Benötigst du allerdings ganze Zahlen über zwei Milliarden wählst du ein `long`. Für Gleitkommazahlen wählst du normalerweise den Type `double` aus. Dieser hat eine höhere Genauigkeit bei Berechnungen als `float` und du bist dadurch auf der sicheren Seite. 

Strings
--------

Ein `string` stellt eine Zeichenkette dar und muss in doppelte Anführungszeichen gesetzt werden: 

```cs
string begrüßung = "Herzlich Willkommen zum Programmierkurs!";
```

Auf einem string lassen sich zahlreiche nützliche Eigenschaften und Methoden aufrufen, zum Beispiel `Length`, `Contains`, und `ToLower`:

```cs
Console.WriteLine(begrüßung.Length); // 40
Console.WriteLine(begrüßung.Contains("Willkommen")); // true
Console.WriteLine(begrüßung.ToLower()); // herzlich willkommen zum programmierkurs!
```

`Length` ist hierbei eine Eigenschaft (Property), `Contains`, und `ToLower` hingegen sind Methoden und müssen mit Runden Klammern `()` aufgerufen werden. Viele Methoden nehmen Argumente entgegen, die `Contains`-Methode beispielsweise erwartet einen `string` auf den geprüft werden soll. 


Äußerst nützlich ist außerdem die Stringinterpolation `$`, welche es uns erlaubt Variablen wie folgt in einen string einzusetzen:

```cs
string name = "Kevin";
Console.WriteLine($"Herzlich willkommen zum Programmierkurs {name}!");
```

Strings können außerdem mit dem Gleichheitsoperator `==` und dem Ungleichheitsoperator `!=` verglichen werden: 

```cs
string name1 = "Alice";
string name2 = "Bob";
bool namenSindGleich = name1 == name2; // false
bool namenSindUngleich = name1 != name2; // true
```

Eine Übersicht über alle Funktionalitäten findest du in der Dokumentation: https://docs.microsoft.com/en-us/dotnet/api/system.string.

>Um die Dokumentation für einen bestimmten Typ zu erhalten suche ich meistens bei der Suchmaschine meiner Wahl nach dem Schlüsselwort in Verbindung mit 'msdn' (Microsoft Developer Network). Also zum Beispiel suche ich nach "string msdn". Die gewünschte Dokumentation ist dann meistens der erste Treffer.

>Tipp: Um von der englischsprachigen zur deutschsprachigen Dokumentation zu wechseln, könnt ihr in der URL `en-us` durch `de-de` ersetzten. 

Weitere Typen
--------------

Weitere zusammengesetzten Datentypen sind beispielsweise Listen, Mengen, und vom Programmierer definierte Typen. Diese werden in einem späteren Kapitel behandelt.

---

### [Kursinhalt](../README.md)
