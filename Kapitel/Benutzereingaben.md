### [Kursinhalt](../README.md)

Benutzereingaben
=================

Eingabe von Text
----------------

Über die Konsole kann einem Programm **Text übergeben** werden. Der folgende Code wartet darauf, dass der Benutzer Text in die Konsole eingibt und anschließend die Eingabetaste drückt:

```cs
string eingabe = Console.ReadLine();
```

Oft muss die Eingabe zur weiteren Verarbeitung in einen anderen Datentyp konvertiert werden. Hierfür gibt es für die primitiven Datentypen nützliche `Parse`-Methoden. Das **konvertieren** in eine ganze Zahl ist zum Beispiel wie folgt möglich:

```cs
int zahl = int.Parse(eingabe);
```

Dieser Ansatz funktioniert hervorragend, solange die Eingabe auch wirklich eine ganze Zahl ist. Ist dies nicht der Fall tritt eine Ausnahme auf und das Programm bricht ab. Ausnahmen werden wir allerdings zu einem späteren Zeitpunkt behandeln. 

Um Ausnahmen zu verhindern können wir stattdessen die `TryParse`-Methoden verwenden:

```cs
if(int.TryParse(eingabe, out int zahl))
{
    // Texteingabe wurde erfolgreich zu einer Zahl konvertiert.
}
else
{
    // Konvertierung nicht möglich.
}
```

Die `TryParse`-Methode hat einen `bool` Rückgabewert und einen sogenannten `out` Parameter. In dessen Variable wird im Falles des Erfolges die konvertierte Zahl gespeichert und kann zur weitern Verarbeitung verwendet werden.

Abfragen einzelner Tasten
--------------------------

Um einzelne Tasten abzufragen wird die Methode `Console.ReadKey()` verwendet:

```cs
ConsoleKeyInfo info = Console.ReadKey();

if (info.Key == ConsoleKey.UpArrow)
{
    // Pfeiltaste nach oben wurde gedrückt.
}
else if (info.Key == ConsoleKey.DownArrow)
{
    // Pfeiltaste nach unten wurde gedrückt.
}
else
{
    // Eine andere Taste wurde gedrückt.
}
```

Diese Methode gibt ein Objekt der Klasse `ConsoleKeyInfo` zurück, auf dem wir die Eigenschaft `Key` aufrufen können. Diese ermöglicht es uns auf einfache Weise zu überprüfen um welche Taste es sich bei der Gedrückten handelt. 

Es existiert außerdem die Überladung `ReadKey(bool intercept)` mit der wir zusätzlich steuern können, ob die gedrückte Taste auf der Konsole ausgegeben werden soll. 

---

### [Kursinhalt](../README.md)