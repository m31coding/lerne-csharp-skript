### [Kursinhalt](../README.md)


Übungen zu Benutzereingaben
===========================

TODO: berechne Grundrechenarten: Zahl eingeben

Übungen zu Benutzereingaben
----------------------------

Schreibe eine Methode `static void FragePasswortAb()` welche den Benutzer dazu auffordert ein Passwort einzugeben. Überprüfe ob das eingegebene Passwort "1234" lautet. Ist das Passwort korrekt? Dann teile dies dem Benutzer mit. Andernfalls fordere ihn dazu auf es erneut einzugeben

<details>
  <summary><b>Hinweis</b></summary>

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
  <summary><b>Hinweis</b></summary>

  - Verwende `if-else`.
  - Beende die Schleife im Erfolgsfall.
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
        if(eingabe == "1234")
        {
            Console.WriteLine("Korrekt!");
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


Hast du die Aufgabe erfolgreich gelöst? Gratulation! Als Bonusaufgabe denke bitte darüber nach, ob man diese Methode auch ohne eine Schleife schreiben könnte.

<details>
  <summary><b>Hinweis</b></summary>

  - Du musst in der Methode die Methode selbst wieder aufrufen (Rekursion).
</details>

<details>
    <summary><b>Lösung</b></summary>

```cs
static void FragePasswortAb()
{
    Console.WriteLine("Wie lautet das Passwort?");

    string eingabe = Console.ReadLine();
    if (eingabe == "1234")
    {
        Console.WriteLine("Korrekt!");
    }
    else
    {
        Console.WriteLine("Falsches Passwort!");
        FragePasswortAb();
    }
}
```
</details>

---

### [Kursinhalt](../README.md)
