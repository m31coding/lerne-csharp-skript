### [Kursinhalt](../README.md)

Klassen
=======

Einführung
----------

Mit Klassen können wir Dinge und Probleme der realen Welt modellieren. Wir haben bereits unter anderem die Klasse `Console` kennengelernt, die die Konsole unseres Programms modelliert, die Klasse `Random`, deren Objekte Zahlengeneratoren darstellen, und die Klasse `Stopwatch` um Zeitmessungen durchzuführen. Je nachdem welches Anwendungsgebiet dein Programm hat wirst du verschiedene Klassen schreiben. Um Bankabläufe zu digitalisieren könnte man zum Beispiel die Klassen `Bankkonto`, `Kunde` und `Transaktion` definieren. Für ein VierGewinnt-Spiel eignen sich hingegen Klassen wie `Spielstellung`, `KonsolenSpieler`, `MinMaxKI` und `Partie`. Jede Klasse hat hierbei Eigenschaften und Methoden um Zustand und Verhalten zu modellieren.

Bei Klassen unterscheidet man zwischen  **gewöhnlichen**, **nicht-statischen** Klassen, und **statischen** Klassen. Eine gewöhnliche Klasse ist ein Modell für ein Objekt und zugleich eine Schablone um konkrete Objekte zu erzeugen. Eine statische Klasse hingegen ist ein Modell und verkörpert gleichzeitig die modellierte Entität. Im Gegensatz zu einer gewöhnlichen Klasse können keine Objekte erzeugt werden.

Klassen verwenden
------------------

Die `Stopwatch`-Klasse ist eine nicht-statische Klasse und wir müssen zunächst durch eine **Konstruktor**-Methode ein Objekt erstellen bevor wir dieses verwenden können. 

```cs
Stopwatch stoppuhr = new Stopwatch();
stoppuhr.Start();
long vergangenenMillisekunden = stoppuhr.ElapsedMilliseconds;
```

Um einen Konstruktor aufzurufen muss das Schlüsselwort `new` verwendet werden. Die `Stopwatch`-Klasse ist nicht-statisch, da es Sinn macht mehrere `Stopwatch`-Objekte zu erzeugen um verschiedene Zeitmessungen durchzuführen:

```cs
Stopwatch stoppuhr1 = new Stopwatch();
Stopwatch stoppuhr2 = new Stopwatch();
// ...
```

Die `Console`-Klasse ist hingegen statisch, da es nur eine Konsole pro Programm geben kann. In diesem Fall müssen wir direkt über den Klassennamen auf Methoden und Eigenschaften zugreifen:

```cs
Console.WriteLine("Hello World!"); 
int fensterbreite = Console.WindowWidth; 
```


Klassen schreiben
------------------

Nehmen wir einmal an, wir wollen Software für ein Schachturnier programmieren. Um eine Person die am Turnier teilnimmt zu modellieren definieren wir eine Klasse `Schachspieler`. Ein Schachspieler soll die Eigenschaften `Vorname`, `Nachname`, `VollständigerName`, `Wertung` und `Platzierung` haben. Außerdem soll jeder Spieler die Methoden `void VerzeichneSieg()` und `void VerzeichneNiederlage()` haben, die die Wertung ändern. Bei einem Sieg soll die Wertung um eine feste Punktzahl `PunkteänderungProSpiel` steigen, bei einer Niederlage fallen. Allerdings sollte die Wertung nie unter null fallen können.

Eine erste Version der Klasse könnte wie folgt aussehen:

```cs
using System;

namespace Schachturnier
{
    public class Schachspieler
    {
        public string Vorname;
        public string Nachname;
        public string VollständigerName;
        public int Wertung;
        public int Platzierung;
        public int PunkteänderungProSpiel;

        public Schachspieler(string vorname, string nachname)
        {
            Vorname = vorname;
            Nachname = nachname;
            VollständigerName = $"{vorname} {nachname}";
            Wertung = 500;
            Platzierung = 0;
            PunkteänderungProSpiel = 10;
        }

        public void VerzeichneSieg()
        {
            Wertung = Math.Max(Wertung - PunkteänderungProSpiel, 0);
        }

        public void VerzeichneNiederlage()
        {
            Wertung += PunkteänderungProSpiel;
        }
    }
}

```

Um eine Klasse zu definieren verwenden wir das `class`-Schlüsselwort, gefolgt vom Namen der Klasse und einem Codeblock `{}`. Als nächstes legen wir die Variablen an, die jedes Objekt der Klasse besitzen soll. Diese initialisieren wir in der `Schachspieler`-Konstruktormethode. Konstruktoren weisen in der Definition keinen Rückgabewert auf und müssen den selben Namen besitzen wie die Klasse selbst. Zuletzt definieren wir noch die beiden Methoden um Sieg- und Niederlage zu verzeichnen, beide ohne Rückgabewert. Wir haben außerdem alle Elemente der Klasse und die Klasse selbst mit dem Schlüsselwort `public` annotiert, hierzu gleich mehr.

Wir können nun `Schachspieler`-Objekte (auch **Instanzen** genannt) mithilfe des `new`-Schlüsselworts und unseres Konstruktors bauen und im Anschluss verwenden:

```cs
Schachspieler spieler1 = new Schachspieler("Alice", "Queen");
Schachspieler spieler2 = new Schachspieler("Bob", "Bishop");
spieler1.VerzeichneSieg();
spieler2.VerzeichneNiederlage();
spieler1.Platzierung = 1;
spieler2.Platzierung = 2;
Console.WriteLine($"{spieler1.VollständigerName} hat die Platzierung {spieler1.Platzierung} " +
                $"erreicht mit einer Wertung von {spieler1.Wertung}");
```

Im Turnier würde man natürlich mit vielen Spielern mehrere Spiele spielen und die Platzierungen aus den Wertungen der Spieler berechnen. 

Die obige Implementierung der Klasse bringt leider einige Probleme mit sich. Das Schlüsselwort `public` ist ein Zugriffsmodifizierer und führt dazu dass die entsprechenden Elemente von überall aus aufgerufen und geändert werden können, insbesondere auch von außerhalb der Klasse. Alle Variablen der Klasse (auch **Felder** bezeichnet) wurden als öffentlich definiert. Es ist somit möglich einem Schachspieler durch die folgenden Zeilen Vorteile zu verschaffen:

```cs
spieler1.PunkteänderungProSpiel = 20;
spieler1.Wertung += 300;
```

Selbst die Namen könnten geändert werden:

```cs
spieler1.Vorname = "Carol";
spieler1.Nachname = "Cunning";
```

Falls das Feld `VollständigerName` nicht auch neu gesetzt wird, befindet sich das Schachspielerobjekt nun in einem äußerst inkonsistenten Zustand. Solches Verhalten wollen wir natürlich vermeiden, deshalb machen wir uns nun für jede Eigenschaft Gedanken ob diese öffentlich oder privat sein sollte. Zusätzlich sollten wir zwischen lesen und schreiben unterscheiden.

Die Eigenschaften Vorname, Nachname und der vollständige Name sollten öffentlich lesbar sein, aber nicht schreibbar, auch nicht innerhalb der Klasse (außer in der Initialisierung). Die Wertung sollte öffentlich lesbar sein, aber nur privat schreibbar. Die Punkteänderung pro Spiel dagegen überhaupt nicht schreibbar. Die Platzierung ist die einzige Eigenschaft die öffentlich les- und schreibbar sein soll. Damit ist sie auch privat schreibbar, denn alles was öffentlich möglich ist, ist auch privat möglich. Wir hätten also insgesamt gerne das folgende Verhalten:

|   |öffentlich lesbar|öffentlich schreibbar|privat schreibbar|
|---|---|---|---|
| Vorname  | ja  | nein  | nein  |
| Nachname  | ja  | nein  | nein  |
| VollständigerName  | ja  | nein | nein |
| Wertung | ja | nein | ja |
| Platzierung | ja | ja | ja |
| PunkteänderungProSpiel | ja | nein | nein |

Wie können wir dieses Verhalten nun am besten erreichen? Zunächst einmal sollten immer alle Felder (Variablen von Klassen) privat gemacht werden, und der Zugriff nur über sogenannte **Properties** ermöglicht werden.

Für die Variable `Platzierung` können wir anstelle von 

```cs
public string Platzierung;
```

ein privates Feld und eine **Property** verwenden:

```cs
private int platzierung;
public int Platzierung
{
    get
    {
        return platzierung;
    }
    
    set
    {
        platzierung = value;
    }
}
```

Die Property definiert einen Lesezugriff durch das Schlüsselwort `get`, und einen schreibenden Zugriff durch das Schlüsselwort `set`. Man spricht hierbei auch von einem `get`-Accessor und einem `set`-Accessor. Das `value`-Schlüsselwort wird verwendet um auf den Wert zuzugreifen, der von außen zugewiesen wird. Durch den Befehl

```cs
spieler1.Platzierung = 1;
```

wird also `set` aufgerufen mit `value=1`.

Durch die Property haben wir eine zusätzliche Schicht eingebaut, mit der wir genau steuern können wie mit dem privaten Feld interagiert wird. Außerdem können wir mit dem Debugger Haltepunkte im `get`- und `set`-Accessor setzen um genau zu beobachten wann das zugrundeliegende Feld verändert wird. Dies kann äußerst nützlich sein um Fehler schnell zu finden.

Soweit so gut. Allerdings ist der Code relativ lang in der Hinsicht, dass er nur dafür verantwortlich ist den Wert eines Feldes zu setzen und zurückzugeben. Deshalb gibt es sogenannte **Autoproperties**, die uns viel Schreibarbeit ersparen:

```cs
public int Platzierung {get; set;}
```

Durch diese Zeile wird beim kompilieren automatisch ein privates Feld im Hintergrund erzeugt, sowie `get`- und `set`-Accessors mit dem Standardverhalten. 

Mit Autoproperties können wir somit auch für die anderen Eigenschaften die gewünschten Zugriffsrechte auf einfache Weise spezifizieren: 

```cs
public string Vorname {get;}
public string Nachname {get;}
public string VollständigerName {get;}
public int Wertung {get; private set;}
public int PunkteänderungProSpiel {get;}
```

Wie du siehst können wir den `set`-Accessor einfach auf `private` setzten falls die Eigenschaft nicht öffentlich geschrieben werden soll. Falls sie überhaupt nicht veränderbar werden soll, lassen wir ihn einfach weg.

Unsere Klasse hat jetzt also die Form:

```cs
using System;

namespace Schachturnier
{
    public class Schachspieler
    {
        public Schachspieler(string vorname, string nachname)
        {
            Vorname = vorname;
            Nachname = nachname;
            VollständigerName = $"{vorname} {nachname}";
            Wertung = 500;
            Platzierung = 0;
            PunkteänderungProSpiel = 10;
        }

        public string Vorname { get; }
        public string Nachname { get; }
        public string VollständigerName { get; }
        public int Wertung { get; private set; }
        public int Platzierung { get; set; }
        public int PunkteänderungProSpiel { get; }

        public void VerzeichneSieg()
        {
            Wertung = Math.Max(Wertung - PunkteänderungProSpiel, 0);
        }

        public void VerzeichneNiederlage()
        {
            Wertung += PunkteänderungProSpiel;
        }
    }
}
```

Das ist schon viel besser als die erste Version! Nun kann nur noch die Eigenschaft `Platzierung` von außen gesetzt werden. 

>Lass dich nicht verwirren dass die Properties im Gegensatz zu den Feldern unter den Konstruktor geschrieben werden, das ist einfach eine Konvention. Properties werden außerdem groß geschrieben, genauso wie Methoden. Lediglich private Felder sollten mit einem Kleinbuchstaben beginnen.

Wir wollen im Folgenden noch ein paar kleine Verbesserungen in unserer Klasse vornehmen. Zunächst einmal wollen wir bei der Platzierung sicherstellen, dass keine negative Zahl oder die Null zugewiesen werden kann. Hierzu ändern wir die Autoproperty

```cs
public int Platzierung { get; set; }
```

in eine Gewöhnliche mit einem zugrundeliegenden privaten Feld und schreiben im `set`-Accessor die gewünschte Überprüfung:

```cs
private int platzierung;

public int Platzierung
{
    get
    {
        return platzierung;
    }
    set
    {
        if (value <= 0)
        {
            string fehler = $"InvalidPlatzierung für Spiele{VollständigerName}: {value}";
            throw new ArgumentException(fehler);
        }
        else
        {
            platzierung = value;
        }
    }
}
```

Der `get`-Accessor kann hierbei durch einen **Ausdruckskörper** zu einer einzelnen Zeile vereinfacht werden:

```cs
get => platzierung;
```

Als nächstes nehmen wir die Eigenschaft `PunkteänderungProSpiel` unter die Lupe. Diese sollte für alle Spieler gleich sein! Mit anderen Worten, dieser Wert sollte nur einmal auf der Klasse existieren, und nicht auf jedem Objekt. Dies können wir durch das `static`-Schlüsselwort erreichen:

```cs
public static int PunkteänderungProSpiel {get;}
```

Nun macht es allerdings keinen Sinn mehr diesen Wert im Konstruktor zuzuweisen, schließlich soll der Wert für alle Instanzen der Selbe sein und auch nur einmal zugewiesen werden.

Wir schreiben deshalb

```cs
public static int PunkteänderungProSpiel
{
    get
    {
        return 10;
    }
}
```

oder verkürzt mit einem Ausdruckskörper:

```cs
public static int PunkteänderungProSpiel => 10;
```

Zuletzt wollen wir noch die `VerzeichneSieg`-Methode etwas sprechender gestalten. Die `Max`-Methode sorgt dafür, dass die Wertung nie negativ werden kann.

Dies können wir in einer extra Klassenmethode zum Ausdruck bringen:

```cs
public void VerzeichneSieg()
{
    Wertung = PositiveWertungOderNull(Wertung - PunkteänderungProSpiel);
}

private static int PositiveWertungOderNull(int wertung)
{
    return Math.Max(wertung, 0);
}
```

Die Methode `PositiveWertungOderNull` bekommt von uns den `private`-Zugriffsmodifizierer, da wir nicht wollen dass sie von außen sichtbar und aufrufbar ist. Zusätzlich kennzeichnen wir sie als statisch (`static`), da diese unabhängig vom Zustand eines Schachspielerobjekts ist. Sie muss nicht auf Eigenschaften oder Methoden des Objekts zugreifen um ihr Ergebnis zu berechnen.

Alternative können wir diese Methode auch als **Lokale Funktion** innerhalb der `VerzeichneSieg`-Methode definieren:

```cs
public void VerzeichneSieg()
{
    Wertung = PositiveWertungOderNull(Wertung PunkteänderungProSpiel)
    
    static int PositiveWertungOderNull(int wertung)
    {
        return Math.Max(wertung, 0);
    }
}
```

Dies ist möglich, da sie nur innerhalb der `VerzeichneSieg`-Methode aufgerufen wird. Aus der Methode `VerzeichneNiederlage` könnte sie beispielsweise nun nicht mehr aufgerufen werden.

Unsere Klasse hat nun die folgende finale Gestalt und sieht ziemlich sauber aus (**Clean Code**):

```cs
using System;

namespace Schachturnier
{
    public class Schachspieler
    {
        private int platzierung;

        public Schachspieler(string vorname, string nachname)
        {
            Vorname = vorname;
            Nachname = nachname;
            VollständigerName = $"{vorname} {nachname}";
            Wertung = 500;
            platzierung = 0;
        }

        public string Vorname { get; }
        public string Nachname { get; }
        public string VollständigerName { get; }
        public int Wertung { get; private set; }
        public static int PunkteänderungProSpiel => 10;

        public int Platzierung
        {
            get => platzierung;

            set
            {
                if (value <= 0)
                {
                    string fehler = $"Invalide Platzierung für Spieler {VollständigerName}: {value}";
                    throw new ArgumentException(fehler);
                }
                else
                {
                    platzierung = value;
                }
            }
        }

        public void VerzeichneSieg()
        {
            Wertung = PositiveWertungOderNull(Wertung - PunkteänderungProSpiel);

            static int PositiveWertungOderNull(int wertung)
            {
                return Math.Max(wertung, 0);
            }
        }

        public void VerzeichneNiederlage()
        {
            Wertung += PunkteänderungProSpiel;
        }
    }
}

```

Kapselung und Zugriffsmodifizierer
-----------------------------------

Mit Klassen können wir Dinge und Probleme der realen Welt modellieren. Zustand und Verhalten von Objekten werden durch Eigenschaften und Methoden gebündelt. Dabei soll nach außen nur das Nötigste preisgegeben werden. In diesem Kontext spricht man auch von **Kapselung**. Für eine gute Kapselung brauchen wir die richtigen Zugriffsmodifizierer. Hier ist eine Übersicht über die wichtigsten Modifizierer:

- `public`: Zugriff von überall aus möglich.
- `private`: Zugriff nur von innerhalb der Klasse aus möglich.
- `protected`: Zugriff möglich von innerhalb der Klasse oder innerhalb einer abgeleiteten Klasse (siehe Vererbung).
- `internal`: Zugriff nur möglich von innerhalb der gleichen Assembly (dll oder exe). Das heißt bei einer Visual Studio Projektmappe nur innerhalb des selben Projekts.

Vererbung
----------

Eine Klasse kann von einer anderen Klasse abgeleitet werden um einen Teil des Modells dieser Klasse wiederzuverwenden (**Vererbung**). Vererbung ist ein fester Bestandteil der meisten objektorientierten Programmiersprachen, allerdings handelt es sich hierbei um ein kontroverses Thema. Oft kann nämlich ein besseres Modell durch eine Komposition erhalten werden anstelle von Vererbung, siehe auch "composition vs inheritance" bei der Suchmaschine deiner Wahl. Außerdem handelt es sich hierbei um fortgeschrittene Konzepte, die den Rahmen dieses Kurses sprengen würden.  

---
>In diesem Kapitel hast du gesehen, wie wir uns eine gute Klassendefinition Schritt für Schritt erarbeiten können. Das gut hinzubekommen ist alles andere als einfach! Es gibt ganze Bücher nur über diese Kunst (Domain-driven Design) und wie so oft macht Übung den Meister. Falls dir das alles noch sehr suspekt vorkommt, lass dich an dieser Stelle bitte nicht entmutigen, Klassen sind nämlich mit das Schwierigste was es in einer Sprache wie C# zu verstehen gibt! Im nächsten Kapitel werfen wir einen Blick auf Schnittstellen und betrachten weitere Beispielklassen.

---
### [Kursinhalt](../README.md) 