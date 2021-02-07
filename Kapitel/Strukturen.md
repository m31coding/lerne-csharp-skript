### [Kursinhalt](../README.md)

Struct
======

Ein Struct ist einer Klasse ähnlich, es hat einen oder mehrere Konstruktoren und kann ebenfalls Felder, Properties und Methoden besitzen. Structs sind dazu gedacht **kompakte Datentypen** abzubilden. Genauso wie für Enums und Klassen, sollte man für ein Struct eine eigene C#-Datei (.cs) anlegen. Die Hauptunterschiede zu einer Klasse sind überwiegend von technischer Natur wie du in Kürze sehen wirst.

Zunächst einmal zeige ich dir aber zwei Beispiele für Typen die man am besten als Struct definiert.

Punkte und Vektoren Geometriebibliothek

```cs
public struct Coords
{
    public Coords(double x, double y)
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
```

Konstruktor: Unterschied zu Klassen

Bei unserer Vier gewinnt Implementierung ist der Typ `Spielzug` ein geeigneter Kandidat für ein Struct:

```cs
namespace VierGewinnt.Spiel
{
    public readonly struct Spielzug
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

In der Tat handelt es sich bei diesen Beispielen um kompakte Typen die nur Konstanten und Zahlen speichern.


Strukturen vs. Klassen
======================


Werttypen vs. Referenztypen
------------------------------


Wann verwende ich eine Klasse, wann ein Struct?
-----------------------------------------------

Ein Struct eignet sich hervorragend wenn du einen **kompakten, datenorientierten Typen** definieren möchtest. Das heißt wenn der zu definierende Typ nur 1-3 Variablen hat die selbst auch Werttypen sind, also beispielsweise Zahlen oder Enums. Es empfiehlt sich außerdem die Eigenschaften des Structs **unveränderlich** zu machen, also keinen `set`-Accessor zur Verfügung zu stellen. Dies soll verhindern dass sich aufgrund der Wertsemantik Fehler im Programm einschleichen. Man kann sich dann nämlich sicher sein, dass die Kopien des Wertobjektes zu jeder Zeit die gleichen Eigenschaftswerte haben wie das Originalobjekt.

Wenn du mit deinem Typ ein **Interface** implementieren möchtest, ist es in den allermeisten Fällen besser eine **Klasse** zu definieren. An den Stellen wo du das Struct als den Interfacetyp verwendest muss dieses dann in ein Referenzobjekt eingepackt werden was mit zusätzlichem Rechenaufwand verbunden ist. Siehe hierzu auch "C# boxing unboxing" bei der Suchmaschine deines Vertrauens. Wenn du hingegen **Vererbung** verwenden möchtest musst du dich zwangsläufig für eine Klasse entscheiden, da diese von Structs nicht unterstützt wird.

> Wenn du dir in manchen Fällen überhaupt nicht sicher bist ob ein Struct oder ein Klasse die bessere Wahl für einen Typ ist dann empfehle ich dir zunächst eine Klasse zu verwenden. Diese Wahl ermöglicht dir etwas mehr Flexibilität. Wenn dein Programm dann einmal läuft und zufriedenstellend funktioniert kannst du deine Entscheidung noch einmal überprüfen. Ändere hierzu deinen Typ von Klasse zu Struct und messen ob sich die Laufzeit und oder der Speicherverbrauch deines Programms reduzieren. Ist dies nicht der Fall, oder es zeigt sich nur eine sehr geringe Verbesserung, kannst du guten Gewissens eine Klasse verwenden.

---
### [Kursinhalt](../README.md)