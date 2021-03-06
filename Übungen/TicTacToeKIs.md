### [Kursinhalt](../README.md)

Übung: TicTacToe KIs
=====================

In dieser Übung wollen wir mehrere KIs für TicTacToe schreiben. Für jede KI erstellt ihr am besten im Ordner *Spieler* eine neue Datei.
Dies erreicht ihr wir folgt: Rechtsklick auf den Order -> Hinzufügen -> Neues Element. Dort wählt ihr Klasse aus und nennt die Datei der KI entsprechend, zum Beispiel MisterBoring.cs. 

Außerdem soll jede KI die Schnittstelle `ISpieler` implementieren. Die Klasse einer KI namens `MisterBoring` sollte also die folgende Struktur haben:

```cs
using System;
using TicTacToe.Spiel;

namespace TicTacToe.Spieler
{
    public class MisterBoring : ISpieler
    {
        public Spielzug BerechneNächstenSpielzug(Spielstellung stellung)
        {
            throw new NotImplementedException(); // todo
        }
    }
}
```

MisterBoring
-------------

Schreibe eine KI namens *MisterBoring*. MisterBoring führt immer den ersten Zug aus der möglich ist.

<details>
<summary><b>Lösung</b></summary>

```cs
using System.Collections.Generic; 
using TicTacToe.Spiel;

namespace TicTacToe.Spieler
{
    public class MisterBoring : ISpieler
    {
        public Spielzug BerechneNächstenSpielzug(Spielstellung stellung)
        {
            List<Spielzug> möglicheZüge = stellung.MöglicheZüge();
            return möglicheZüge[0];
        }
    }
}
```
</details>

MissRandom
-----------

Schreibe eine KI names *MissRandom*, die immer einen zufälligen Zug ausführt.

<details>
<summary><b>Lösung</b></summary>

```cs
using System;
using System.Collections.Generic;
using TicTacToe.Spiel;

namespace TicTacToe.Spieler
{
    public class MissRandom : ISpieler
    {
        private readonly Random zahlengenerator;

        public MissRandom(Random zahlengenerator)
        {
            this.zahlengenerator = zahlengenerator;
        }

        public Spielzug BerechneNächstenSpielzug(Spielstellung stellung)
        {
            List<Spielzug> spielzüge = stellung.MöglicheZüge();
            int zufälligerZug = zahlengenerator.Next(spielzüge.Count);
            return spielzüge[zufälligerZug];
        }
    }
}
```
</details>

Siegertyp
----------

Schreibe eine KI namens *Siegertyp*. Falls es einen Zug gibt der sofort zum Sieg führt wählt er diesen Zug aus. Andernfalls wählt er den ersten Zug aus der möglich ist.

### Allgemeine Hinweise 

Bevor du einen Zug in deiner KI ausführst achte darauf dass du die Spielstellung mittels der `Kopie`-Methode kopierst.  Dies ist wichtig, da ein Zug nicht mehr rückgängig gemacht werden kann. 

Verwende die Klasse `Stellungsanalyse` und `SpielstandKonvertierung` um zu überprüfen ob ein Zug nach Ausführung zum Sieg geführt hat.

### Los geht`s

Lege zunächst eine Methode `private bool SpielzugGewinnt(Spielzug spielzug, Spielstellung stellung)` an ohne sie zu implementieren.
 
Verwende diese Methode um `BerechneNächstenSpielzug` zu programmieren und tue einfach so, als hättest du die Methode `SpielzugGewinnt` schon fertig geschrieben (Top-Down Programmierung).

<details>
<summary><b>Teillösung</b></summary>

```cs
namespace TicTacToe.Spieler
{
    public class Siegertyp : ISpieler
    {
        public Spielzug BerechneNächstenSpielzug(Spielstellung stellung)
        {
            List<Spielzug> möglicheZüge = stellung.MöglicheZüge();
            List<Spielzug> gewinnerZüge = 
                möglicheZüge.Where(z => SpielzugGewinnt(z, stellung.Kopie())).ToList();

            if(gewinnerZüge.Count > 0)
            {
                return gewinnerZüge[0];
            }
            else
            {
                return möglicheZüge[0];
            }
        }

        private bool SpielzugGewinnt(Spielzug spielzug, Spielstellung stellung)
        {
            throw new NotImplementedException(); // todo
        }
    }
}
```
</details>

Programmiere die Methode `SpielzugGewinnt` fertig.

<details>
<summary><b>Lösung</b></summary>

```cs
using System.Collections.Generic;
using System.Linq;
using TicTacToe.Spiel;

namespace TicTacToe.Spieler
{
    public class Siegertyp : ISpieler
    {
        public Spielzug BerechneNächstenSpielzug(Spielstellung stellung)
        {
            List<Spielzug> möglicheZüge = stellung.MöglicheZüge();
            List<Spielzug> gewinnerZüge = 
                möglicheZüge.Where(z => SpielzugGewinnt(z, stellung.Kopie())).ToList();

            if(gewinnerZüge.Count > 0)
            {
                return gewinnerZüge[0];
            }
            else
            {
                return möglicheZüge[0];
            }
        }

        private bool SpielzugGewinnt(Spielzug spielzug, Spielstellung stellung)
        {
            Symbol aktuellerSpieler = stellung.SpielerAmZug;
            stellung.FühreSpielzugAus(spielzug);
            Stellungsanalyse analyse = new Stellungsanalyse(stellung);
            Spielstand spielstand = analyse.ErhalteSpielstand();
            Symbol sieger = SpielstandKonvertierung.NachSymbol(spielstand);
            return sieger == aktuellerSpieler;
        }
    }
}
```
</details>




---

### [Kursinhalt](../README.md)
