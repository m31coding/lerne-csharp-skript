### [Kursinhalt](../README.md)

Schnittstellen
================

Eine Schnittstelle ist ein Vertrag der von einer Klasse oder Struktur eingehalten werden muss. Schnittstellen dienen dazu Klassen und Strukturen die die gleichen Methoden- und Propertydeklarationen besitzen zusammenzufassen. 

Betrachten wir beispielsweise ein TicTacToe-Programm bei dem es möglich sein soll dass verschiedene Spieler gegeneinander antreten können. Dies können sowohl KIs sein, als auch ein menschlicher Spieler der Eingaben über die Konsole macht. Letzteren modellieren wir durch eine Klasse mit dem Namen `Konsolenspieler`.

Eine sehr einfache (aber auch sehr schwache) KI macht immer einen zufälligen Zug wenn sie an der Reihe ist. Wir wollen diese KI mittels einer Klasse `MissRandom` modellieren. 

Beide Klassen repräsentieren einen TicTacToe-Spieler und Instanzen der Klassen sollen tun was TicTacToe-Spieler nun so einmal so machen :). Sie schauen sich die Spielstellung scharf an und überlegen sich den nächsten Zug. Wir wollen folglich auf beiden Klassen eine Methode implementieren die wie folgt aussieht:

```cs
Spielzug BerechneNächstenSpielzug(Spielstellung stellung)
```

Unsere beiden Klassen haben also in etwa die folgende Form:

```cs
namespace TicTacToe.Spieler
{
    public class Konsolenspieler 
    {
        public Konsolenspieler()
        {

        }

        public Spielzug BerechneNächstenSpielzug(Spielstellung stellung)
        {
            /*
             * Gib auf der Konsole alle möglichen Züge aus und
             * lies die Spielereingabe von der Konsole ein.
             */
        }
    }
}
```

und

```cs
namespace TicTacToe.Spieler
{
    public class MissRandom
    {
        private readonly Random zahlengenerator;

        public MissRandom(Random random)
        {
            zahlengenerator = random;
        }

        public Spielzug BerechneNächstenSpielzug(Spielstellung stellung)
        {
            /*
             * Wähle mithilfe des Zahlengenerators einen 
             * zufälligen Zug und gib diesen zurück.
             */ 
        }
    }
}
```

Außerdem soll eine Klasse `Partie` implementiert werden die zwei Spieler entgegennimmt und eine Methode `SpielePartie` zur Verfügung stellt. Der Code um zwei Spieler zu definieren und eine Partie durchzuführen sieht in etwa wie folgt aus:

```cs
Konsolenspieler spieler1 = new Konsolenspieler();
MissRandom spieler2 = new MissRandom(new Random());
Partie partie = new Partie(spieler1, spieler2);
Spielstand spielstand = partie.SpielePartie();
VerkündeErgebnis(spielstand);
```

Wie aber müsste nun die Klasse `Partie` und insbesondere deren Konstruktor aussehen? Für den Konsolenspieler und Miss Random bräuchten wir die folgende Klassendefinition:

```cs
namespace TicTacToe
{
    public class Partie
    {
        private readonly Konsolenspieler spieler1;
        private readonly MissRandom spieler2;

        public Partie(Konsolenspieler spieler1, MissRandom spieler2)
        {
            this.spieler1 = spieler1;
            this.spieler2 = spieler2;
        }

        public Spielstand SpielePartie()
        {
            /*
             * ...
             * Ruft die Methode BerechneNächstenSpielzug(Spielstellung stellung) 
             * abwechselnd auf Spieler 1 und Spieler 2 auf.
             */
        }
    }
}
```

Nun haben wir aber das Problem, dass immer nur ein Konsolenspieler gegen Miss Random spielen kann. Wir wollen aber natürlich auch abbilden, dass zwei Konsolenspieler gegeneinander spielen können, oder aber zwei KIs. Zudem möchten wir noch weitere KIs implementieren.

Dieses Dilemma können wir durch eine Schnittstelle auflösen. Die Klasse `Partie` benötigt von den Spielern lediglich die Methode `Spielzug BerechneNächstenSpielzug(Spielstellung stellung)` und diese Gemeinsamkeit können wir in einer Schnittstelle die wir `ISpieler` nennen wollen wie folgt abbilden:

```cs
using TicTacToe.Spiel;

namespace TicTacToe.Spieler
{
    public interface ISpieler
    {
        Spielzug BerechneNächstenSpielzug(Spielstellung stellung);
    }
}
```

Um eine Schnittstelle zu definieren verwenden wir das Schlüsselwort `interface`. Der Name der Schnittstelle ist frei wählbar, es ist jedoch eine feste Konvention diesen mit einem großen `I` zu beginnen. Danach folgt ein Codeblock `{}` der Methoden- und Propertydeklarationen enthalten kann. In unserem Beispiel benötigen wir nur eine Methode.

>Obwohl man beliebig viele Methoden und Properties auf einer Schnittstelle definieren kann ist es ratsam kleine Schnittstellen mit wenigen Methoden und Properties zu definieren. In der Softwaretechnik heißt dieses Prinzip **Interface segregation principle**. Hierdurch wird erreicht, dass an den Stellen an denen die Schnittstelle verwendet wird auch wirklich nur die Methoden und Properties zur Verfügung stehen die benötigt werden. 

Wir können nun unsere beiden Spielerklassen leicht abändern um auszudrücken dass sie sich an die `ISpieler`-Schnittstelle halten:

```cs
namespace TicTacToe.Spieler
{
    public class Konsolenspieler : ISpieler
    {
        public Konsolenspieler()
        {

        }

        public Spielzug BerechneNächstenSpielzug(Spielstellung stellung)
        {
            /*
             * Gib auf der Konsole alle möglichen Züge aus und
             * lies die Spielereingabe von der Konsole ein.
             */
        }
    }
}
```

und

```cs
namespace TicTacToe.Spieler
{
    public class MissRandom : ISpieler
    {
        private readonly Random zahlengenerator;

        public MissRandom(Random random)
        {
            zahlengenerator = random;
        }

        public Spielzug BerechneNächstenSpielzug(Spielstellung stellung)
        {
            /*
             * Wähle mithilfe des zahlengenerators einen 
             * zufälligen Zug und gib diesen zurück.
             */ 
        }
    }
}
```

Wie du siehst hat sich nicht viel geändert, wir haben lediglich einen Doppelpunkt und den Namen der Schnittstelle hinter die Klassennamen geschrieben. Die größte Auswirkung dieser Änderung ist, dass beide Klassen nun eine Metdhode `Spielzug BerechneNächstenSpielzug(Spielstellung stellung)` haben *müssen*. Entfernte man diese Methode nun aus der Klasse, so würde sich der Compiler mit einer Fehlermeldung beschweren.

Zu guter Letzt können wir die Problematik unserer `Partie`-Klasse auflösen. Anstelle einer konkreten Klasse übergeben wir ein Objekt des Schnittstellentyps `ISpieler`:

```cs
namespace TicTacToe
{
    public class Partie
    {
        private readonly ISpieler spieler1;
        private readonly ISpieler spieler2;

        public Partie(ISpieler spieler1, ISpieler spieler2)
        {
            this.spieler1 = spieler1;
            this.spieler2 = spieler2;
        }

        public Spielstand SpielePartie()
        {
            /*
             * ...
             * Ruft die Methode BerechneNächstenSpielzug(Spielstellung stellung) 
             * abwechselnd auf Spieler 1 und Spieler 2 auf.
             */
        }
    }
}
```

Die Durchführung einer Partie sieht genauso aus wie zuvor:

```cs
Konsolenspieler spieler1 = new Konsolenspieler();
MissRandom spieler2 = new MissRandom(new Random());
Partie partie = new Partie(spieler1, spieler2);
Spielstand spielstand = partie.SpielePartie();
VerkündeErgebnis(spielstand);
```

In der Zeile

```cs
Partie partie = new Partie(spieler1, spieler2);
```

werden die Objekte implizit in den Schnittstellentyp `ISpieler` konvertiert.
Alternativ können wir die Spielerobjekte auch direkt in `ISpieler`-Variable speichern. In diesem Fall geschieht die Konvertierung bei der Variablenzuweisung:

```cs
ISpieler spieler1 = new Konsolenspieler();
ISpieler spieler2 = new MissRandom(new Random());
Partie partie = new Partie(spieler1, spieler2);
Spielstand spielstand = partie.SpielePartie();
VerkündeErgebnis(spielstand);
```

>In diesem Kapitel haben wir das Konzept der Schnittstellen besprochen. Klassen und Schnittstellen bilden zusammen die wichtigsten Komponenten der modernen objektorientierten Programmierung. Hast du diese Konzepte verinnerlicht so bleibt mir nichts weiter als dir zu gratulieren! Du hast dann nämlich einen großen und entscheidenden Schritt gemacht. Welche Klassen und Schnittstellen man für das jeweilige Problem am besten definieren sollte ist eine Wissenschaft für sich. Zahlreiche Bücher widmen sich dem Thema der Modellierung (**Domain-driven Design**) und des Schreibens von sauberem Code (**Clean Code**). Ich halte es für eine sehr gute Idee dass du dich bald mit diesen Konzepten vertraut machst, allerdings würde dies den Rahmen dieses Kurses sprengen. 

---
### [Kursinhalt](../README.md)