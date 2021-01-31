### [Kursinhalt](../README.md)

Enums
======

Was sind Enums?
---------------

Ein Enum ist einer der einfachsten Datentypen in C#, hierbei handelt es sich lediglich um eine Aufzählung von Konstanten.

Für TicTacToe erweisen sich beispielsweise die folgenden beiden Enum-Definitionen als geschickt:

```cs
public enum Symbol 
{
    Keins,
    Kreuz,
    Kreis
}
```

```cs
public enum Spielstand
{
    Offen,
    Unentschieden,
    KreuzIstSieger,
    KreisIstSieger
}
```


Wie verwendet man Enums?
-------------------------

Man kann mit dem Namen des Typs sehr einfach auf die definierten Konstanten zugreifen. Man verwendet die Konstanten oft dazu, sie mit anderen Konstanten zu vergleichen. Beispiel:

```cs
Spielstand spielstand = Spielstand.Offen;

 while (spielstand == Spielstand.Offen)
 {
     // Führe Spielzug aus und setze neuen Spielstand.
 }
```

Enums haben außerdem eine nützliche String-Repräsentation. Solange der Spielstand offen ist gibt der folgende Code "Der Spielstand ist Offen." aus:

```cs
Console.WriteLine($"Der Spielstand ist: {spielstand}."); 
```


Warum gibt es Enums?
--------------------

Die meisten Anwendungsfälle von Enums könnten auch mit Strings programmiert werden, zum Beispiel:

```cs
string spielstand = "offen";

 while (spielstand == "offen")
 {
     // Führe Spielzug aus und setze neuen Spielstand.
 }
```

Allerdings hat dies eine schwächere Semantik da man in einen String jeden beliebigen String-Wert speichern kann. Beispielsweise könnte ein anderer Programmiere auf die Idee kommen die folgende Zeile zu schreiben: 

```cs
string spielstand = "2:1";
```

Dies würde natürlich den Sinn unserer Definition völlig verfehlen.

Durch die Beschränkung auf einzelne Konstanten ist die Bedeutung unseres Enum Typs hingegen klar definiert.

Außerdem ist der Code dadurch weniger fehleranfällig. Beispielsweise würde ein Tippfehler in der while Bedingung zu einer Endlosschleife führen:

```cs
 while (spielstand == "offne")
 {
     // Führe Spielzug aus und setze neuen Spielstand.
 }
```

Interne Repräsentation
----------------------

Intern werden Enum-Konstanten standardmäßig mit einem `int` gespeichert. Die erste Konstante hat hierbei den Wert `0`, die zweite den Wert `1`, u.s.w. Diese Werte können auch mit anderen Werten überschrieben werden, zum Beispiel um auch in der entsprechenden Zahl Bedeutung zu transportieren. Beispielsweise sieht ein Auszug aus der Definition von HttpStatusCode aus der .NET-Bibliothek wie folgt aus:

```cs
public enum HttpStatusCode
{
    OK = 200,
    Moved = 301,
    MovedPermanently = 301,
    Found = 302,
    Redirect = 302,
    Forbidden = 403,
    NotFound = 404,
    InternalServerError = 500,
    BadGateway = 502,
    ServiceUnavailable = 503
    // ... unvollständig
}
```

Wie man sieht kann die gleiche Zahl sogar zweimal vergeben werden. Das heißt `Moved` und `MovedPermanently` sind genauso Synonyme wie `Found` und `Redirect`. 

Eine Enum-Konstante kann explizit in den entsprechenden int-Wert konvertiert werden:

```cs
HttpStatusCode statusCode = MakeRequest("https://someUrl");
Console.WriteLine($"Status = {(int) statusCode}: {statusCode}.")
```

Die Konsolenausgabe wäre dann zum Beispiel:

```sh
Status = 404: NotFound.
```

Auch wenn wir die int-Werte für die Konstanten nicht selbst explizit setzen ist es gut ein Bewusstsein dafür zu haben. Mit dieser Definition des Symbol-Enums

```cs
public enum Symbol 
{
    Keins, // 0
    Kreuz, // 1
    Kreis // 2
}
```

können wir nämlich sicher sein, dass es in der Initialisierung nur mit Symbol.Keins gefüllt wird:

```cs
Symbol[,] spielbrett = new Symbol[3, 3];
```





---
### [Kursinhalt](../README.md)