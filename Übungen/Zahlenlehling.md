### [Kursinhalt](../README.md)

Abschlussübung: Zahlenlehrling
==============================

Rechtsklick auf Projektmappe.

Hinzufügen, 
Neues Projekt erstellen
Gib dem Projekt einen Name: Zahlenlehrling

Rechtsklick auf Zahlenlehrling Projekt
Als Startprojekt festlegen.

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

Refactoring
-----------

<details>
  <summary><b>Bitte erst auklappen, nachdem wir die Übung gemeinsam besprochen haben.</b></summary>

TODO

</details>

Hausaufgabe
-----------



// ```cs
// Stopwatch stoppUhr = new Stopwatch();
// stoppUhr.Start();
// // code 
// int vergangenenZeitInMS = stoppUhr.Ellapsed;
// ```

---

### [Kursinhalt](../README.md)