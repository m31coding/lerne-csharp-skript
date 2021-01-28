### [Kursinhalt](../README.md)

Übungen zu Methoden
===================

Begrüßungsmethode
------------------

Schreibe in die Klasse `program` und unter die `main` Methode eine Methode `static void Begrüßung(string name)`. Rufe diese in der `main` Methode mit verschiedenen Namen auf. 

Achte darauf dass du das `static` Schlüsselwort zu Beginn der Definition nicht vergisst. Was es damit auf sich hat werden wir zu einem späteren Zeitpunkt lernen. Der Knackpunkt ist dass man aus der statischen `main` Methode heraus nur andere statische Methoden direkt aufrufen kann.

Ihr könnt den anderen Code den ihr bereits geschrieben habt einfach auskommentieren, beziehungsweise die Teile die ihr für die Methode braucht ausschneiden und in die Methode einfügen.


<details>
  <summary><b>Lösung</b></summary>

```cs
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            /*
             * Euer anderer Code 
             * ...
             */

            Begrüßung("Kevin");
            Begrüßung("Alice");
            Begrüßung("Bob");
        }

        static void Begrüßung(string name)
        {
            Console.WriteLine($"Herzlich willkommen zum Programmierkurs {name}!");
        }
    }
}

```
</details>

Ausgabe der Grundrechenarten
----------------------------

Schreibt außerdem eine Methode `static void GebeAlleGrundrechenartenAus(double zahl1, double zahl2)` die für die vier Grundrechenarten jeweils eine Zeile in der Konsole ausgibt, wie ihr es bereits programmiert habt. Rufe auch diese neue Methode in der `main` Methode auf.

<details>
  <summary><b>Lösung</b></summary>

```cs
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Begrüßung("Kevin");
            Begrüßung("Alice");
            Begrüßung("Bob");
            GebeAlleGrundrechenartenAus(1.5, 2.5);
        }

        static void Begrüßung(string name)
        {
            Console.WriteLine($"Herzlich willkommen zum Programmierkurs {name}!");
        }

        static void GebeAlleGrundrechenartenAus(double zahl1, double zahl2)
        {
            double summe = zahl1 + zahl2;
            double differenz = zahl1 - zahl2;
            double produkt = zahl1 * zahl2;
            double quotient = zahl1 / zahl2;

            Console.WriteLine($"Die Summe aus {zahl1} und {zahl2} ist {summe}.");
            Console.WriteLine($"Die Differenz aus {zahl1} und {zahl2} ist {differenz}.");
            Console.WriteLine($"Das Produkt aus {zahl1} und {zahl2} ist {produkt}.");
            Console.WriteLine($"Der Quotient aus {zahl1} und {zahl2} ist {quotient}.");
        }
    }
}

```
</details>

Konvertierung zwischen Stunden und Sekunden
--------------------------------------------

Schreibe die Methoden `static double ErhalteSekunden(double stunden)` und `static double ErhalteStunden(double sekunden)`.

<details><summary><b>Lösung für ErhalteSekunden</b></summary>

```cs
static double ErhalteSekunden(double stunden)
{
    return stunden * 3600;
}
```
</details>

<details><summary><b>Lösung für ErhalteStunden</b></summary>

```cs
static double ErhalteStunden(double sekunden)
{
    return sekunden / 3600;
}
```
</details>

Test ob eine Zahl gerade ist
-----------------------------

Schreibe eine Methode `static bool ZahlIstGerade(int zahl)` die testet ob eine Zahl gerade ist.

<details><summary><b>Hinweis</b></summary>

- Verwende den Modulooperator `%`.
</details>

<details><summary><b>Lösung</b></summary>

```cs
static bool ZahlIstGerade(int zahl)
{
    return zahl % 2 == 0;
}
```

</details>

Skalierung
-----------

Angenommen bei einem Spiel können die Spieler zwischen 10 und 250 Punkte erzielen. Wir wollen das Endergebnis in eine Sternebewertung umrechnen wobei es 0 Sterne für die niedrigste und 5 Sterne für die höchste Punktzahl gibt. Dazwischen hätten wir gerne ein lineares (proportionales) Verhalten.

- Schreibe eine Methode `static double AnzahlSterne(int punktzahl)`.

<details><summary><b>Lösung</b></summary>

```cs
// [10, 250] => [0, 5]
static double AnzahlSterne(int punktzahl)
{
    double relativePunktzahl = (punktzahl - 10) / (double) (250 - 10);
    return relativePunktzahl * 5;
}
```

</details>

Wir möchten nun die Methode für verschiedene Spiele verwenden können die unterschiedliche minimale und maximale Punktzahlen erlauben.

- Verallgemeinere die Methode zu `static double AnzahlSterne(int punktzahl, int minimalpunktzahl, int maximalpunktzahl)`.

<details><summary><b>Lösung</b></summary>

```cs
static double AnzahlSterne(int punktzahl, int minimalpunktzahl, int maximalpunktzahl)
{
    double relativePunktzahl = (punktzahl - minimalpunktzahl) / (maximalpunktzahl - minimalpunktzahl);
    return relativePunktzahl * 5;
}
```

</details>



---

### [Kursinhalt](../README.md)