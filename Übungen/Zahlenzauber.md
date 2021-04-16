### [Kursinhalt](../README.md)

Zahlenlehrling
===============

Projekt anlegen
---------------

Für diese Übung wollen wir ein neues Projekt anlegen. Mache im Projektmappen-Explorer auf der rechten Seite einen rechtsklick auf die Projektmappe *Programmierkurs*. Dann wählst du  *Hinzufügen* -> *Neues Projekt* aus. Wähle als Typ Konsolen-App (.NET Core) und klicke auf weiter. Gib dem Projekt den Namen *Zahlenlehrling* und klicke auf *Erstellen*. Nun sollte das Projekt im Projektmappen-Explorer erscheinen.

Klicke mit rechts auf das neue Projekt *Zahlenlehrling* und wähle *Als Startprojekt festlegen* (das ist die Option mit dem Rädchen). Nun kannst du das neue Projekt starten.

Aufgabe
--------

Wir wollen ein Programm schreiben, in welchem der Computer uns dazu auffordert eine geheime Zahl zu erraten. Die geheime Zahl soll hierbei zufällig sein. Nachdem wir eine Zahl geraten und eingegeben haben hat sagt uns der Computer ob die geheime Zahl größer, kleiner, oder genau richtig ist. Behandle außerdem Eingaben die keine Zahl sind, und zähle die Versuche die der Benutzer braucht um die richtige Zahl zu erraten. Die Konsolenausgabe könnte wie folgt aussehen:

```sh
Willkommen, errate meine geheime zwischen 0 und 100 Zahl!
42
Die geheime Zahl ist größer als 42! Los, versuch es erneut!
65
Die geheime Zahl ist größer als 65! Los, versuch es erneut!
was weiß ich denn?
Das ist keine ganze Zahl! Versuch es erneut!
80
Die geheime Zahl ist größer als 80! Los, versuch es erneut!
92
Die geheime Zahl ist größer als 92! Los, versuch es erneut!
95
Hervorragend, du hast meine Zahl in 6 versuchen erraten!
```

Für diese Programm müssen wir eine Zufallszahl erzeugen. Dies geschieht mittels der `Random` Klasse. Durch die folgenden Zeilen erhaltet ihr beispielsweise einen Zufallszahlengenerator sowie eine Zufallszahl zwischen 0 und 100:

```cs
Random zahlengenerator = new Random();
int zufallszahl = zahlengenerator.Next(0, 100);
```

Falls ihr, wie in unserem Fall, nur eine einzelne Zufallszahl braucht, könnt ihr dies auch in einer einzelnen Zeile schreiben:

```cs
int zufallszahl = new Random().Next(0, 100);
```


Du kannst nun entweder versuchen die Übung ohne Hilfe zu lösen oder aber, falls du dich noch etwas unsicher fühlst, die folgende Schritt für Schritt Anleitung verwenden.

<details>
  <summary><b>Schritt 1</b></summary>

Definiere zunächst in der `main` Methode zwei `int` Variablen `min` und `max`, welche den Ratebereich begrenzen und gib eine Begrüßung aus. Definiere außerdem eine Variable `geheimeZahl`, in der du eine zufällig generierte Zahl speicherst. 

</details>

<details>
  <summary><b>Lösung</b></summary>

```cs
using System;

namespace Zahlenlehrling
{
    class Program
    {
        static void Main(string[] args)
        {
            int min = 0;
            int max = 100;
            Console.WriteLine($"Willkommen, errate meine geheime Zahl zwischen {min} und {max}!");
            int geheimeZahl = new Random().Next(min, max);
        }
    }
}
```

</details>


<details>
  <summary><b>Schritt 2</b></summary>

Verwende eine `while(true)` Schleife in der du die Benutzereingabe einliest. Hierzu kannst du die Methode `Console.ReadLine` verwenden. Überprüfe anschließend mit der Methode `int.TryParse` ob sich die Benutzereingabe in eine ganze Zahl umwandeln lässt. Ist dies nicht der Fall, gib eine entsprechende Meldung aus und springe zurück zum Beginn der Schleife.
</details>

<details>
  <summary><b>Lösung</b></summary>

```cs
using System;

namespace Zahlenlehrling
{
    class Program
    {
        static void Main(string[] args)
        {
            int min = 0;
            int max = 100;
            Console.WriteLine($"Willkommen, errate meine geheime Zahl zwischen {min} und {max}!");
            int geheimeZahl = new Random().Next(min, max);

            while (true)
            {
                string eingabe = Console.ReadLine();
                if (!int.TryParse(eingabe, out int gerateneZahl))
                {
                    Console.WriteLine("Das ist keine ganze Zahl! Versuch es erneut!");
                    continue;
                }
            }
        }
    }
}
```
</details>

<details>
  <summary><b>Schritt 3</b></summary>
Falls die Eingabe in eine Zahl umgewandelt werden konnte überprüfe ob die eingegebene Zahl der geheimen Zahl entspricht, kleiner als diese ist, oder größer. Gib wiederum entsprechende Meldungen auf der Konsole aus. Stoppe außerdem die Schleife für den Fall dass es sich bei der Eingabe um die richtige Zahl handelt.
</details>

<details>
  <summary><b>Lösung</b></summary>

```cs
using System;

namespace Zahlenlehrling
{
    class Program
    {
        static void Main(string[] args)
        {
            int min = 0;
            int max = 100;
            Console.WriteLine($"Willkommen, errate meine geheime Zahl zwischen {min} und {max}!");
            int geheimeZahl = new Random().Next(min, max);

            while (true)
            {
                string eingabe = Console.ReadLine();
                if (!int.TryParse(eingabe, out int gerateneZahl))
                {
                    Console.WriteLine("Das ist keine ganze Zahl! Versuch es erneut!");
                    continue;
                }

                if (gerateneZahl == geheimeZahl)
                {
                    Console.WriteLine($"Hervorragend, du hast meine Zahl erraten!");
                    break;
                }
                else if (gerateneZahl < geheimeZahl)
                {
                    Console.WriteLine($"Die geheime Zahl ist größer als {gerateneZahl}! Los, versuch es erneut!");
                }
                else
                {
                    Console.WriteLine($"Die geheime Zahl ist kleiner als {gerateneZahl}! Das schaffst du!");
                }
            }
        }
    }
}
```
</details>

<details>
  <summary><b>Schritt 4</b></summary>

Als letzten Schritt wollen wir das Programm noch erweitern, sodass die Anzahl Versuche mit ausgegeben wird. Definiere hierzu eine Variable `anzahlVersuche` außerhalb der Schleife und setze ihren Wert auf 0. Erhöhe diese Anzahl bei jedem Schleifendurchgang um 1, und gib die Variable im Erfolgsfall mit aus.

</details>

<details>
  <summary><b>Lösung</b></summary>

```cs
using System;

namespace Zahlenlehrling
{
    class Program
    {
        static void Main(string[] args)
        {
            int min = 0;
            int max = 100;
            Console.WriteLine($"Willkommen, errate meine geheime Zahl zwischen {min} und {max}!");
            int geheimeZahl = new Random().Next(min, max);
            int anzahlVersuche = 0;

            while (true)
            {
                anzahlVersuche++;
                string eingabe = Console.ReadLine();

                if (!int.TryParse(eingabe, out int gerateneZahl))
                {
                    Console.WriteLine("Das ist keine ganze Zahl! Versuch es erneut!");
                    continue;
                }

                if (gerateneZahl == geheimeZahl)
                {
                    Console.WriteLine($"Hervorragend, du hast meine Zahl in {anzahlVersuche} versuchen erraten!");
                    break;
                }
                else if (gerateneZahl < geheimeZahl)
                {
                    Console.WriteLine($"Die geheime Zahl ist größer als {gerateneZahl}! Los, versuch es erneut!");
                }
                else
                {
                    Console.WriteLine($"Die geheime Zahl ist kleiner als {gerateneZahl}! Das schaffst du!");
                }
            }
        }
    }
}
```

</details>


<details>
  <summary><b>Ich bin fertig mit der Übung :)</b></summary>

> Du hast diese Übungsaufgabe gemeistert? Ausgezeichnet! Damit hast du bewiesen dass du schon etwas komplexere Programme in C# schreiben kannst, Gratulation!

</details>

Zeitmessung und Wertung
------------------------

Wir wollen nun nicht nur die Anzahl Versuche ausgeben die der Benutzer gebraucht hat um die Zahl zu erraten, sondern eine Sternewertung zwischen 0 und 5. In diese Wertung soll neben der Anzahl Versuche auch die benötigte Zeit einfließen.

Um Zeitmessungen durchzuführen müssen wir einen zusätzlichen Namensraum unserem Code verwenden:

```cs
using System.Diagnostics;
```

Eine Zeitmessung kann dann mit einer Stopwatch gestartet werden: 

```cs
Stopwatch watch = new Stopwatch();
watch.Start();
```

Anschließend könnt ihr jeder Zeit die vergangene Zeit abrufen:
```cs
long vergangeneMillisekunden = watch.ElapsedMilliseconds;
```

Überlege dir wie du aus den Größen Anzahl Versuche und vergangene Zeit eine Wertung berechnen kannst. Hier gibt es kein richtig oder falsch, versuche dich einfach daran :).

Zahlenzauberer
===============

Wir wollen nun das umgekehrte Programm schreiben: Der Computer soll uns auffordern an eine geheime Zahl zu denken. Anschließend versucht der Computer diese Zahl zu erraten und wir teilen ihm über die Pfeiltasten mit ob er richtig geraten hat. Lege auch hierzu ein neues Projekt an und nenne es *Zahlenzauberer*.

Die Ausgabe könnte für die geheime Zahl 42 wie folgt aussehen:

```sh
Willkommen, denke an eine geheime zwischen 0 und 100!

Ist die Zahl größer, drücke die Pfeiltaste nach oben!
Ist deine geheime Zahl kleiner, dann drücke dagegen die Pfeiltaste nach unten!
Und falls ich die Zahl erraten habe ... drücke Enter!

Ist deine geheime Zahl die 50?

Ist deine geheime Zahl die 25?

Ist deine geheime Zahl die 37?

Ist deine geheime Zahl die 43?

Ist deine geheime Zahl die 40?

Ist deine geheime Zahl die 41?

Ist deine geheime Zahl die 42?

Ich wusste es!
```

Das drücken einer Pfeil- oder der Entertaste kann auf der Konsole leider nicht dargestellt werden, hierfür wird lediglich automatisch eine leere Zeile ausgegeben.

Überlege dir zunächst eine Strategie wie das Programm die nächste Zahl ermitteln soll, sodass die richtige Zahl mit möglichst wenigen Versuchen erraten wird. Versuche diese Strategie in deinem Programm abzubilden. Es ist hilfreich wenn du dabei an die vorherige Übung *Zahlenlehrling* denkst, mit welcher Strategie hast du die nächste Zahl gewählt und eingegeben?

<details>
<summary><b>Hinweis 1</b></summary>

- Die gedachte Zahl befindet sich zu Beginn zwischen `int min = 0` und `int max = 100`. Als erster Rateversuch eignet sich hiervon die Mitte des Intervals.
</details>

<details>
<summary><b>Hinweis 2</b></summary>

- Nach jedem Rateversuch kannst du im Programm berücksichtigen, dass sich entweder die untere oder die obere Grenze des Intervals geändert hat. 
- Als nächsten Rateversuch wählt man am besten wieder die Mitte des neuen Intervals.
</details>

<details><summary><b>Gesamtlösung</b></summary>

```cs
using System;

namespace Zahlenzauberer
{
    class Program
    {
        static void Main(string[] args)
        {

            int min = 0;
            int max = 100;
            Console.WriteLine($"Willkommen, denke an eine geheime zwischen {min} und {max}!");
            Console.WriteLine();
            Console.WriteLine("Ist die Zahl größer, drücke die Pfeiltaste nach oben!");
            Console.WriteLine("Ist deine geheime Zahl kleiner, dann drücke dagegen die Pfeiltaste nach unten!");
            Console.WriteLine("Und falls ich die Zahl erraten habe ... drücke Enter!");
            Console.WriteLine();

            int gerateneZahl = RateZahl(min, max);

            while (true)
            {
                Console.WriteLine($"Ist deine geheime Zahl die {gerateneZahl}?");
                ConsoleKey taste = Console.ReadKey().Key;
                Console.WriteLine();

                if (taste == ConsoleKey.UpArrow)
                {
                    min = gerateneZahl;
                    gerateneZahl = RateZahl(min, max);
                }
                else if (taste == ConsoleKey.DownArrow)
                {
                    max = gerateneZahl;
                    gerateneZahl = RateZahl(min, max);
                }
                else if (taste == ConsoleKey.Enter)
                {
                    Console.WriteLine("Ich wusste es!");
                    break;
                }
                else
                {
                    Console.WriteLine("Das hilft mir nicht weiter...!");
                }
            }

            static int RateZahl(int min, int max)
            {
                return (min + max) / 2;
            }
        }
    }
}
```
</details>

<details>
<summary><b>Ich habe die Aufgabe gelöst :)</b></summary>

>Hervorragend!, du hast dir einen Algorithmus ausgedacht der möglichst schnell zur gedachten Zahl führt und diesen auch noch blitzsauber implementiert. So schnell kann dir keiner mehr etwas vormachen!
</details>

---

### [Kursinhalt](../README.md)