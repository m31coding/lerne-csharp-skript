### [Kursinhalt](../README.md)

Übung: Vier gewinnt Ki
=======================

Wir haben den MinMax-Algorithmus und den Einsatz von Heuristiken besprochen. In dieser Übung wollen wir eine eigene Heuristik schreiben, die zu einer KI führt, die besser ist als eine KI mit der Heuristik `EinfacheHeuristik`.

Ich habe dir hierzu bereits eine Klasse namens `MeineHeuristik` angelegt damit du sofort loslegen kannst. Schaue dir die Klasse `EinfacheHeuristik` an und überlege wie man diese verbessern könnte.

<details>
<summary><b>Hinweis 1</b></summary>

Die Klasse `EinfacheHeuristik` gewichtet die Anzahl Steine, die Zweier- und die Dreierverbindungen gleich um eine Wertung zu berechnen. 

</details>

<details>
<summary><b>Hinweis 2</b></summary>

Zweierverbindungen sind sicherlich mehr Wert als einzelne Steine, und eine Dreierverbindung ist besser als eine Zweierverbindung.

</details>

<details>
<summary><b>Hinweis 3</b></summary>

Multipliziere jeden Summand der Wertung mit einem Faktor.
</details>

Hier ist eine von vielen möglichen Lösungen um die Heuristik stark zu verbessern:

<details>
<summary><b>Lösung</b></summary>

```cs
using VierGewinnt.Spiel;

namespace VierGewinnt.Spieler.Heuristiken
{
    class MeineHeuristik : IHeuristik
    {
        public double BewerteSpielstellungFürRot(Spielstellung stellung, Stellungsanalyse analyse)
        {
            if (analyse.Spielstand != Spielstand.Offen)
            {
                return HeuristikHelfer.BewerteAusgangFürRot(analyse.Spielstand);
            }

            double wertung = 0;

            wertung += analyse.AnzahlRoteSteine;
            wertung += 3 * analyse.VerbindungenRot.AnzahlZweierverbindungen;
            wertung += 20 * analyse.VerbindungenRot.AnzahlDreierverbindungen;

            wertung -= analyse.AnzahlGelbeSteine;
            wertung -= 3 * analyse.VerbindungenGelb.AnzahlZweierverbindungen;
            wertung -= 20 * analyse.VerbindungenGelb.AnzahlDreierverbindungen;

            return wertung;
        }
    }
}
```
</details>

---
### [Kursinhalt](../README.md)