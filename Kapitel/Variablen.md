### [Kursinhalt](../README.md)

Variablen
=========

Variablen als Schubladen
-----------------------------------------

**Computerspeicher** können wir uns wie ein riesiges **Schubladenregal** vorstellen. In jeder Schublade können wir etwas ablegen um es später wieder hervorzuholen. Damit wir keine Probleme haben die Dinge später wiederzufinden, beschriften wir jede Schublade mit dem **Namen** und dem **Typ** des Objekts.

Definition und Zuweisung 
-------------------------

Eine **Schublade** ist eine Metapher für eine **Variable**. Wir können eine Variable für den Text "Willkommen!" wie folgt anlegen:

```cs
string begrüßung = "Willkommen!";
```

Zunächst muss der Typ der Variablen angegeben werden, in unserem Fall wollen wir eine Zeichenkette speichern. Wir wählen also den Typ `string`. Als nächstes überlegen wir uns einen aussagekräftigen Namen, zum Beispiel `begrüßung`. Durch das Gleichheitszeichen (Zuweisungsoperator) weisen wir der Variablen den Wert "Willkommen!" zu. Da es sich um einen Befehl handelt, müssen wir diesen außerdem mit dem Semikolon `;` abschließen.

Und schon haben wir unsere erste Variable definiert und einen Wert abgelegt!

Die Definition und Zuweisung kann übrigens auch in zwei Schritten erfolgen:


```cs
string begrüßung;
begrüßung = "Willkommen!"
```

Beim zweiten Befehl müssen wir nur den Namen der Variablen verwenden, da wir den Typ bereits mit dem ersten Befehl bekannt gegeben haben. 

Da das Programm alle Befehle Schritt für Schritt abarbeitet dürften die beiden Zeilen allerdings nicht vertauscht werden. Die Variable muss zuerst definiert werden bevor wir eine Zuweisung machen können.

Änderung von Werten
-------------------

Der Wert einer Variable kann zu jeder Zeit verändert werden. Im Bild der Schubladen hieße das, dass wir die Schublade aufmachen, den alten Wert rausholen, und einen neuen Wert ablegen. Im Programm wird der Wert der Variablen jedoch einfach überschrieben. Hier ist ein Beispiel:

```cs
string begrüßung = "Willkommen!";
Console.WriteLine(begrüßung); 
begrüßung = "Herzlich willkommen!";
Console.WriteLine(begrüßung) 
```

Dieser Code gibt die folgenden beiden Zeilen auf der Konsole aus.

```sh
"Willkommen!"
"Herzlich Willkommen!"
````

Benennung von Variablen
------------------------

Variablen sollten mit einem kleinen Buchstaben anfangen und zusammengeschrieben werden. Falls der Name aus mehreren Wörtern besteht beginnt man jedes weitere Wort mit einem Großbuchstaben. Diese Schreibweise nennt sich Camel-Case-Schreibweise (Kamelschreibweise). Hier sind einige Beispiele:

- begrüßung
- kurzeBegrüßung
- begüßungAnAlle

---

> Perfekt!, mit diesem Wissen bist du sehr gut gerüstet für die weiteren Kapitel.

### [Kursinhalt](../README.md)