### [Kursinhalt](../README.md)

Struct
======

Ein Struct ist einer Klasse ähnlich, es hat einen oder mehrere Konstruktoren und kann ebenfalls Felder, Properties und Methoden besitzen. Structs sind dazu gedacht **kompakte Datentypen** abzubilden. Genauso wie für Enums und Klassen, sollte man für ein Struct eine eigene C#-Datei (.cs) anlegen. Die Hauptunterschiede zu einer Klasse sind überwiegend von technischer Natur wie du in Kürze sehen wirst.

Zunächst einmal zeige ich dir aber zwei Beispiele für Typen die man am besten als Struct definiert. Betrachten wir zunächst einmal ein Struct `Punkt` welches so in einer Geometriebibliothek vorzufinden sein könnte:

```cs
namespace Geometrie
{
    public struct Punkt
    {
        public Punkt(double x, double y)
        {
            X = x;
            Y = y;
        }

        public double X { get; }
        public double Y { get; }

        public override string ToString()
        {
            return $"({X}, {Y})";
        }
    }
}
```

Ein Punkt speichert nichts weiter als eine x- und y-Koordinate und hat als einzige Methodendefinition eine `ToString`-Methode.

Bei unserer Vier gewinnt Implementierung ist der Typ `Spielzug` ein geeigneter Kandidat für ein Struct:

```cs
namespace VierGewinnt.Spiel
{
    public struct Spielzug
    {
        public Spielzug(Farbe farbe, int spalte)
        {
            Farbe = farbe;
            Spalte = spalte;
        }

        public Farbe Farbe { get; }
        public int Spalte { get; }

        public override string ToString()
        {
            return $"(Farbe={Farbe}, Spalte={Spalte})";
        }
    }
}
```

Bei beiden Beispielen handelt es sich um kompakte Typen die ausschließlich Konstanten und Zahlen speichern. Damit definiert man diese Typen am besten als Structs. Warum das so ist erfährst du in den nächsten beiden Abschnitten.


Werttypen vs. Referenztypen
------------------------------

Alle Typen in C# lassen sich in eine von den folgenden Kategorien einteilen: Klasse, Struct, Enum, Schnittstelle, und Delegate. Wir haben hiervon bereits alle bis auf die letzte Kategorie kennengelernt. Auf diese wollen wir in diesem Kurs auch nicht weiter eingehen. Die primitiven Datentypen `int`, `float`, `double`, u.s.w. die wir zu Beginn des Kurses behandelt haben sind allesamt Structs. `string`, `Console`, und `Stopwatch` sind hingegen Klassen. 

>Vielleicht fragst du dich an dieser Stelle warum manche Typen Kleingeschrieben werden, und andere groß. Bei den kleingeschriebenen Typen handelt es sich um in die C#-Sprache **integrierte** Typen. `int`, `float`, `double` und `string` sind Schlüsselwörter für die .Net-Typen `Int32`, `Single`, `Double` und `String`. Eine Übersicht über alle integrierten Typen findest du hier: https://docs.microsoft.com/de-de/dotnet/csharp/language-reference/builtin-types/built-in-types.

Außerdem ist jeder Typ entweder ein Werttyp, oder ein Referenztyp. Structs und Enums sind Werttypen, bei Klassen, Schnittstellen und Delegaten hingegen handelt es sich um Referenztypen. 

Die entscheidenden Unterschiede zwischen einem Werttyp und einem Referenztyp sind die Folgenden: Eine Variable eines Werttyps enthält den Wert direkt. In einer Variable eines Referenztyps hingegen wird eine Referenz (**Zeiger**) auf das eigentliche Objekt gespeichert.

Betrachten wir eimal das folgende Beispiel:

```cs
int zahl = 2;
List<int>() zahlen = new List<int>(){1, 2, 3}; 
```

In der ersten Zeile speichern wir den Wert `2` in die Variable `zahl` des Typs `int`. Da es sich bei `int` um ein Struct und somit einen Werttyp handelt wird die Zahl direkt in die Variable gespeichert. Dies ist möglich, da ein `int`-Wert immer die selbe Größe hat (32 bit).

In der unteren Zeile speichern wir eine Liste in der Variable `zahlen`. Da es sich bei `List<int>` um eine Klasse und somit um ein Referenztyp handelt enthält die Variable die Liste allerdings nicht direkt, sondern eine Referenz auf das Listenobjekt, welches sich an einer anderen Stelle irgendwo im Speicher unseres Computers befindet.

Wenn man nun die Variable `zahlen` einer Methode übergibt, beispielsweise durch den Befehl 

```cs
double mittelwert = BerechneMittelwert(zahlen);
```

wird also die Referenz auf das Objekt übergeben und nicht das Objekt selbst. Das hat den Vorteil dass das Objekt nicht kopiert werden muss um in der Methode anzukommen.

Und das ist auch schon der größte Unterschied zwischen Wert- und Referenztypen:

Bei einer Zuweisung, einem Methodenaufruf und bei der Rückgabe aus einer Methode werden Variablenwerten von Werttypen kopiert! Bei Referenztypen wird hingegen nur die Referenz kopiert, das Objekt selbst muss nicht angefasst werden.

Nehmen wir einmal an unser `Punkt`-Typ von oben hat für die Property X und Y nicht nur eine `get`-Methode, sondern auch eine `set`-Methode, sodass wir neue Werte setzen können. Im Folgenden Code legen wir einen Punkt `p1` an, weisen `p1` dann einem Punkt `p2` zu, und verändern schließlich den X-Wert von `p2`. 

```cs
Punkt p1 = new Punkt(0, 1);
Console.WriteLine(p1);
Punkt p2 = p1;
p2.X = 2;
Console.WriteLine(p2);
Console.WriteLine(p1);
```

Was geschieht hierbei mit dem Punkt `p1`? Wie in der Konsolenausgabe zu sehen ist bleibt der Punkt `p1` unverändert:

```sh
(0, 1)
(2, 1)
(0, 1)
```

Der Knackpunkt ist dass bei der Zuweisung in der Zeile

```cs
Punkt p2 = p1;
```

eine Kopie von `p1` erstellt wird. `p1` und `p2` speichern nach dieser Zuweisung zwar den gleichen Punkt, es ist allerdings nicht der selbe Punkt. Im Speicher existieren nun zwei Punkte.

Wenn wir unsere Definition des Punkttyps von `struct` zu `class` ändern machen wir aus `Punkt` einen Referenztyp. Wiederholen wir nun das Experiment erhalten wir eine andere Ausgabe:

```sh
(0, 1)
(2, 1)
(2, 1)
```

Durch die Änderung von `p2` durch den Befehl 

```cs
p2.X = 2;
```

 hat sich also auch `p1` geändert! Wie kann dies erklärt werden? Ist `Punkt` eine Klasse und somit ein Referenztyp erhält die Variable `p2` durch die Zuweisung 

 ```cs
Punkt p2 = p1;
 ```

 eine Referenz auf das selbe Punktobjekt, das auch in `p1` mittels einer Referenz gespeichert wird. Das Punktobjekt kann also verändert werden indem man über `p1` darauf zugreift, oder aber über `p2`.


Wann verwende ich eine Klasse, wann ein Struct?
-----------------------------------------------

Ein Struct eignet sich hervorragend wenn du einen **kompakten, datenorientierten Typen** definieren möchtest. Das heißt wenn der zu definierende Typ nur 1-3 Variablen hat die selbst auch Werttypen sind, also beispielsweise Zahlen oder Enums. Es empfiehlt sich außerdem die Eigenschaften des Structs **unveränderlich** zu machen, also keinen `set`-Accessor zur Verfügung zu stellen. Dies soll verhindern dass sich aufgrund der Wertsemantik Fehler im Programm einschleichen. Man kann sich dann nämlich sicher sein, dass die Kopien des Wertobjektes zu jeder Zeit die gleichen Eigenschaftswerte haben wie das Originalobjekt.

Wenn du mit deinem Typ ein **Interface** implementieren möchtest, ist es in den allermeisten Fällen besser eine **Klasse** zu definieren. An den Stellen wo du das Struct als den Interfacetyp verwendest muss dieses dann in ein Referenzobjekt eingepackt werden was mit zusätzlichem Rechenaufwand verbunden ist. Siehe hierzu auch "C# boxing unboxing" bei der Suchmaschine deines Vertrauens. Wenn du hingegen **Vererbung** verwenden möchtest musst du dich zwangsläufig für eine Klasse entscheiden, da diese von Structs nicht unterstützt wird.

>Wenn du dir in manchen Fällen überhaupt nicht sicher bist ob ein Struct oder ein Klasse die bessere Wahl für einen Typ ist dann empfehle ich dir zunächst eine Klasse zu verwenden. Diese Wahl ermöglicht dir etwas mehr Flexibilität. Wenn dein Programm dann einmal läuft und zufriedenstellend funktioniert kannst du deine Entscheidung noch einmal überprüfen. Ändere hierzu deinen Typ von Klasse zu Struct und messen ob sich die Laufzeit und oder der Speicherverbrauch deines Programms reduzieren. Ist dies nicht der Fall, oder es zeigt sich nur eine sehr geringe Verbesserung, kannst du guten Gewissens eine Klasse verwenden.

---
### [Kursinhalt](../README.md)