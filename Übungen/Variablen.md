### [Kursinhalt](../README.md)

Übungen zu Variablen
====================

Lege direkt über der Begrüßungszeile

```cs
Console.WriteLine("Herzlich willkommen zum Programmierkurs!");
```

eine Variable an, in der du deinen Namen speichert.


<details>
  <summary><b>Hinweis</b></summary>

  - Ein Name ist eine Zeichenkette und benötigt den Typ `string` um gespeichert zu werden.
</details>

<details>
  <summary><b>Lösung</b></summary>

```cs
string name = "Kevin";
Console.WriteLine("Herzlich willkommen zum Programmierkurs!");
```
</details>


 Gib den Namen in einer zweiten Zeile auf der Konsole aus. Dein Programm sollte also in etwa Folgendes ausgeben:

 ```sh
"Herzlich willkommen zum Programmierkurs!"
"Kevin"
 ```

<details>
  <summary><b>Hinweis</b></summary>

- Ihr benötigt eine weitere Zeile mit dem `Console.WriteLine` Befehl.
</details>

<details>
  <summary><b>Lösung</b></summary>

```cs
string name = "Kevin";
Console.WriteLine("Herzlich willkommen zum Programmierkurs!");
Console.WriteLine(name);
```
</details>

Hast du die richtige Lösung programmiert? Hervorragend! Wir wollen diese persönliche Begrüßung nun in einer einzelnen Zeile ausgeben. Hierzu können wir den `+` Operator verwenden, um aus zwei Zeichenketten eine zu machen, zum Beispiel
ergibt `"Hallo" + " Welt"` den String `Hallo Welt`.


<details>
  <summary><b>Lösung</b></summary>

```cs
string name = "Kevin";
Console.WriteLine("Herzlich willkommen zum Programmierkurs!, " + name);
```
</details>

Es gibt jedoch noch eine deutlich elegantere Art wie wir Strings miteinander verketten können, die sogenannte Stringinterpolation. Hierzu schreibt ihr ein `$` vor den String und könnt dann in den String Variablen mit `{}` wie folgt einsetzen:

<details>
  <summary><b>Zeig mir die Stringinterpolation!</b></summary>

```cs
string name = "Kevin";
Console.WriteLine($"Herzlich willkommen zum Programmierkurs {name}!");
```
</details>

Lege zuletzt zwei weitere Namenvariablen an und gib diese in der Konsole aus. Die Ausgabe sollte ungefähr so aussehen:

```sh
Herzlich willkommen zum Programmierkurs Kevin, Alice, und Bob!
```


<details>
  <summary><b>Hinweis</b></summary>

- Auch die beiden neuen Variablen brauchen einen Variablenname, allerdings ist der Name `name` schon vergeben. Ihr könnt die neuen Variablen einfach `name2` und `name3` nennen.

</details>

<details>
  <summary><b>Lösung</b></summary>

```cs
string name = "Kevin";
string name2 = "Alice";
string name3 = "Bob";
Console.WriteLine($"Herzlich willkommen zum Programmierkurs {name}, {name2}, und {name3}!");
```

</details>

---

### [Kursinhalt](../README.md)