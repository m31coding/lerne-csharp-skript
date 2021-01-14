### [Kursinhalt](../README.md)

Benutzereingaben
=================

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
    Console.WriteLine($"Die Zahl {zahl} wurde erfolgreich eingegeben.");
}
else
{
    Console.WriteLine($"Die Eingabe {eingabe} ist keine Zahl!");
}
```

Die `TryParse`-Methode hat einen `bool`-Rückgabewert und einnen sogenannten `out`-Parameter. In diesen wird im Falles des Erfolges die konvertierte Zahl gespeichert.

Console.ReadKey()
-----------------------



### [Kursinhalt](../README.md)