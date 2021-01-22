### [Kursinhalt](../README.md)

Schleifen
==========

Um Befehle wiederholt ausführen zu lassen können wir sie in eine Schleife schreiben. Es gibt `while` Schleifen, `for` Schleifen, und `foreach` Schleifen, wobei wir diesen Typ erst Später behandeln werden.

while Schleife
--------------- 

```cs

while(bedingung) // bedingung liefert bool Wert
{
    // führe diesen code aus
}
```

Zu Beginn einer while Schleife wird geprüft, ob die Bedingung `true` oder `false` liefert. Liefert die Bedingung `false`, so wird der Codeblock `{}` der Schleife einfach ausgelassen. Andernfalls wird der Codeblock ausgeführt. Am Ende des Blocks wird die Bedingung erneut überprüft und falls diese immer noch `true` liefert wird der Block erneut ausgeführt. Dies geschieht so lange, bis die Bedingung `false` liefert.

```cs
while(!SpielIstBeendet())
{
    // Führe nächsten Spielzug aus
}

Console.WriteLine("Das Spiel ist aus!");
```

Es gibt außerdem noch eine leicht abgewandelte Form, die do-while Schleife:

```cs
do
{
    // führe diesen code aus

} while (bedingung);
```

Der Unterschied zur normalen while Schleife besteht darin, dass der Codeblock `{}` mindestens einmal ausgeführt wird. Diese Form kommt allerdings eher selten zur Anwendung.

for Schleife
------------- 

Mithilfe einer for Schleife können wir sehr einfach steuern wie oft ein Block ausgeführt wird. Hierzu definieren wir eine `int` Zahl (Iterationsvariable), eine Bedingung an diese Zahl, und was mit dieser Zahl am Ende einer Iteration geschehen soll. Zum Beispiel:



```cs
for(int i = 0; i<=10; i++)
{
    Console.WriteLine(i);
}
```

Diese Schleife gibt einfach die Zahlen von 0 bis 10 auf der Konsole aus. Würden wir anstatt `i++` den Ausdruck `i=i+2` schreiben, oder kurz `i+=2`, so erhielten wir nur von jeder zweiten Zahl eine Ausgabe.


Schleifenbefehle
----------------

Innerhalb einer Schleife kann man mit dem Befehl `break` die Schleife abbrechen. Der Befehl `continue` dient dazu die aktuelle Iteration zu beenden und in die nächste zu springen.

Beispielsweise kann die while Schleife oben auch wie folgt geschrieben werden:

```cs
while(true)
{
    if(SpielIstBeendet())
    {
        break;
    }

    // Führe nächsten Spielzug aus
}

Console.WriteLine("Das Spiel ist aus!");
```

Um alle Zahlen außer die Zahl 3 auszugeben könnte man schreiben 

```cs
for(int i = 0; i<=10; i++)
{
    if(i == 3)
    {
        continue;
    }

    Console.WriteLine(i);
}
```

---

### [Kursinhalt](../README.md)