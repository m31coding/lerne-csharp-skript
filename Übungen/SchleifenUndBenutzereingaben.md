### [Kursinhalt](../README.md)


Übungen zu Schleifen und Benutzereingaben
=========================================

Zahlen rückwärts
-----------------

Schreibe eine Methode `static void ZähleRückwärts()` die die Zahlen von 10 bis 0 (in absteigender Reihenfolge) mittels einer Schleife auf der Konsole ausgibt.

<details><summary><b>Hinweis 1</b></summary>

- Weise der Iterationsvariablen zunächst den Wert 10 zu.
</details>

<details><summary><b>Hinweis 2</b></summary>

- Am Ender einer Iteration muss die Zahl um eins verringert werden. Verwende also den Ausdruck `i--`.
</details>

<details><summary><b>Lösung</b></summary>

```cs
static void ZähleRückwärts()
{
    for (int i = 10; i >= 0; i--)
    {
        Console.WriteLine(i);
    }
}
```
</details>

Passwortabfrage
-----------------

Schreibe eine Methode `static void FragePasswortAb()` welche den Benutzer dazu auffordert ein Passwort einzugeben. Überprüfe ob das eingegebene Passwort "ninja" lautet. Teile dem Benutzer mit ob das eingegebene Passwort korrekt ist. Falls es falsch ist, fordere ihn dazu auf es erneut einzugeben.

Die Ausgabe könnte wie folgt aussehen:


```sh
Wie lautet das Passwort?
1234
Falsches Passwort!
Wie lautet das Passwort?
qwer
Falsches Passwort!
Wie lautet das Passwort?
ninja
Korrekt!
```

<details>
  <summary><b>Hinweis</b></summary>

  - Verwende eine `while(true)`-Schleife.
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

        if(eingabe == "ninja")
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

Fakultät
--------

Schreibe eine Funktion `static int BerechneFakultät(int n)` die die Fakultät einer Zahl berechnet. Die Fakultät von n ist n * (n-1) * (n-2) * ... * 1. Außerdem gilt per Definition Fakultät(0)=1. 

Teste deine Methode mit den folgenden Fällen: 

```cs
Console.WriteLine(BerechneFakultät(0)); // 1
Console.WriteLine(BerechneFakultät(1)); // 1
Console.WriteLine(BerechneFakultät(2)); // 2
Console.WriteLine(BerechneFakultät(3)); // 6
Console.WriteLine(BerechneFakultät(4)); // 24

```

<details><summary><b>Lösung 1</b></summary>

Die Lösung für eine Abwärtsiteration (`i--`) lautet:

```cs
static int BerechneFakultät(int n)
{
    if (n == 0) return 1;

    int result = n;

    for (int i = n - 1; i>= 1; i--)
    {
        result = result * i;
    }

    return result;
}
```

</details>

<details><summary><b>Lösung 2</b></summary>

Die Lösung für eine Aufwärtsiteration (`i++`) ist:

```cs
static int BerechneFakultät(int n)
{
    int result = 1;

    for(int i = 2; i<=n; i++)
    {
        result = result * i;
    }

    return result;
}
```

</details>

Programmiere nun die Fakultät ohne eine Schleife zu verwenden. 

Die Lösung ist nicht naheliegend wenn man sie nicht kennt. Wenn du beim besten Willen nicht verstehen kannst wie das gehen soll scheue dich nicht die Hinweise anzusehen.

<details><summary><b>Hinweis 1</b></summary>

Bei genauer Betrachtung gilt für die Fakultät für den Fall dass n ungleich 0 ist: Fakultät(n) = n * Fakultät(n-1).
</details>

<details><summary><b>Hinweis 2</b></summary>

Du musst also in der Methode `BerechneFakultät` die Methode selbst wieder aufrufen. Dies nennt sich Rekursion.
</details>

<details><summary><b>Lösung</b></summary>

```cs
static int BerechneFakultät(int n)
{
    if (n == 0)
    {
        return 1;
    }
    else
    {
        return n * BerechneFakultät(n - 1);
    }
}

```
</details>

Passwortabfrage ohne Schleife
--------------------------------

Kannst du die Übungsaufgabe Passwortabfrage auch ohne eine Schleife programmieren?

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
    if (eingabe == "ninja")
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
