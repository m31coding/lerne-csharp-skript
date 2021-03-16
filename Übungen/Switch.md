### [Kursinhalt](../README.md)

Übungen zu switch
==================

In dieser Übung möchten wir den TicTacToe-Code verbessern indem wir *if-else*-Ausdrücke mit mehr als zwei Zweigen suchen und durch *switch*-Befehle und -Ausdrücke ersetzen.

Ein erster Kandidat ist die Methode *VerkündeErgebnis* in der Datei *Program.cs*:

```cs
private static void VerkündeErgebnis(Spielstand spielstand)
{
    Console.WriteLine();
    Symbol sieger = SpielstandKonvertierung.NachSymbol(spielstand);

    if (sieger == Symbol.Kreuz)
    {
        Console.WriteLine("Kreuz hat gewonnen!");
    }
    else if (sieger == Symbol.Kreis)
    {
        Console.WriteLine("Kreis hat gewonnen!");
    }
    else
    {
        Console.WriteLine("Unentschieden!");
    }
}
```

Diese können wir durch einen *switch*-Ausdruck umschreiben zu: 

```cs
private static void VerkündeErgebnis(Spielstand spielstand)
{
    Console.WriteLine();
    Symbol sieger = SpielstandKonvertierung.NachSymbol(spielstand);

    string ausgabe = sieger switch
    {
        Symbol.Kreuz => "Kreuz hat gewonnen!",
        Symbol.Kreis => "Kreis hat gewonnen!",
        _ => "Unentschieden!"
    };

    Console.WriteLine(ausgabe);
}
```

Finde im Code alle weiteren *if-else*-Ausdrücke mit mehr als zwei Zweigen und schreibe diese in kompakter Form mittels *switch*, falls dies möglich ist.

<details>
<summary><b>Stellen im Code</b></summary>
<br>

1.: *SpielstandKonvertierung.cs*, Methode *NachSymbol*.

2.: *Spielstellung.cs*, Methode *AlsZeichen*.

3.: *MinMaxSpieler.cs*, Methode *BewerteSpielzug*.

4.: *Partie.cs*, Methode *ErhalteNächstenSpielzug*.

Bemerkung: Die Methode *ErhalteSpielstand* in *Stellungsanalyse.cs* kann nicht umgeschrieben werden, da die Bedingungen aus Ergebnissen von unterschiedlichen Methodenaufrufen bestehen.

</details>

<details>
<summary><b>Lösung Stelle 1</b></summary>
<br>

```cs
public static Symbol NachSymbol(Spielstand spielstand)
{
    return spielstand switch
    {
        Spielstand.KreuzIstSieger => Symbol.Kreuz,
        Spielstand.KreisIstSieger => Symbol.Kreis,
        _ => Symbol.Keins
    };
}
```
</details>

<details>
<summary><b>Lösung Stelle 2</b></summary>
<br>

```cs
private char AlsZeichen(Symbol symbol)
{
    return symbol switch
    {
        Symbol.Kreuz => 'X',
        Symbol.Kreis => 'O',
        _ => ' '
    };
}
```
</details>

<details>
<summary><b>Lösung Stelle 3</b></summary>
<br>

```cs
private double BewerteSpielzug(Spielzug spielzug, Spielstellung stellung)
{
    stellung.FühreSpielzugAus(spielzug);
    Spielstand spielstand = new Stellungsanalyse(stellung).ErhalteSpielstand();

    return spielstand switch
    {
        Spielstand.KreuzIstSieger => 1,
        Spielstand.KreisIstSieger => -1,
        Spielstand.Unentschieden => 0,
        _ => ErhalteDenBestenZug(stellung).Wertung
    };
}
```
</details>

<details>
<summary><b>Lösung Stelle 4</b></summary>
<br>

```cs
private Spielzug ErhalteNächstenSpielzug(Spielstellung stellung)
{
    return stellung.SpielerAmZug switch
    {
        Symbol.Kreuz => spieler1.BerechneNächstenSpielzug(stellung),
        Symbol.Kreis => spieler2.BerechneNächstenSpielzug(stellung),
        _ => throw new ArgumentException("Kein Spieler ist am Zug")
    };
}
```
</details>


---

### [Kursinhalt](../README.md)