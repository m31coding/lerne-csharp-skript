### [Kursinhalt](../README.md)


Übungen zu Benutzereingaben
===========================

Übung 1: Passwort abfragen
---------------------------

Schreibe eine Methode `static void FragePasswortAb()` welche den Benutzer dazu auffordert ein Passwort einzugeben. Überprüfe ob das eingegebene Passwort "correct horse battery staple" lautet. Ist das Passwort korrekt? Dann teile dies dem Benutzer mit. Andernfalls fordere ihn dazu auf es erneut einzugeben

<details>
  <summary><b>Hinweis 1</b></summary>

  - Verwende eine `while`-Schleife.
  - Verwende die Methode `Console.ReadLine()`.
</details>

<details>
    <summary><b>Teillösung</b></summary>

```cs
static void FragePasswortAb()
{
    while(true)
    {
        Console.WriteLine("Wie lautet das Passwort?");

        string eingabe = Console.ReadLine();
        
        // Überprüfe die Eingabe.
    } 
}
```
</details>

<details>
    <summary><b>Lösung</b></summary>

```cs
static void FragePasswortAb()
{
    while(true)
    {
        Console.WriteLine("Wie lautet das Passwort?");

        string eingabe = Console.ReadLine();
        if(eingabe == "correct horse battery staple")
        {
            Console.WriteLine("Passwort korrekt!");
            break;
        }
        else
        {
            Console.WriteLine("Falsches Passwort!");
        }
    } 
}
```
</details>


### [Kursinhalt](../README.md)
