### [Kursinhalt](../README.md)

Operatoren der Wahrheitswerte
==============================

Für die Wahrheitswerte `true` und `falls` gibt es die Vergleichsoperatoren `==` und `!=`, den Verneinungsoperator `!`, und Operatoren für logische Verknüpfungen:

- und-Operator: `&&`
- oder-Operator: `||`
- exklusiv-oder-Operator: `^`

Vergleichsoperatoren
---------------------

```cs
true == true // true
false == false // true
true == false // false
```

```cs
true != true // false
false != false // false
true != false // true
```

Verneinungsoperator
--------------------

```cs
!true // false
!false // true
```


Und-Operator &&
-----------------

<table>
<tr>
    <td><b>&&<b></td>
    <td><b>true<b></td>
    <td><b>false<b></td>
</tr>
<tr>
    <td><b>true<b></td>
    <td>true</td>
    <td>false</td>
</tr>
<tr>
    <td><b>false<b></td>
    <td>false</td>
    <td>false</td>
</tr>
</table>

Eine Bedingung bestehend aus zwei mit *und* verknüpften Bedingungen ist nur genau dann wahr, wenn beide Bedingungen wahr sind. Beispiel:

```cs
bool spielzugIstGültig = !spielIstBeendet && FeldIstFrei("A3");
```

Oder-Operator ||
-----------------

<table>
<tr>
    <td><b>||<b></td>
    <td><b>true<b></td>
    <td><b>false<b></td>
</tr>
<tr>
    <td><b>true<b></td>
    <td>true</td>
    <td>true</td>
</tr>
<tr>
    <td><b>false<b></td>
    <td>true</td>
    <td>false</td>
</tr>
</table>

Eine Bedingung bestehend aus zwei mit *oder* verknüpften Bedingungen ist genau dann wahr falls eine oder beide Bedingungen wahr sind. In unserem Sprachgebrauch könnte man sagen es muss also die eine Bedingung wahr sein *und-oder* die andere. Zum Beispiel:

```cs
bool spielBeendet = Spieler1IstAmZiel() || Spieler2IstAmZiel();
```

Exklusiv-Oder-Operator ^
-------------------------

<table>
<tr>
    <td><b>^<b></td>
    <td><b>true<b></td>
    <td><b>false<b></td>
</tr>
<tr>
    <td><b>true<b></td>
    <td>false</td>
    <td>true</td>
</tr>
<tr>
    <td><b>false<b></td>
    <td>true</td>
    <td>false</td>
</tr>
</table>

Eine Bedingung bestehend aus zwei mit *exklusiv-oder* verknüpften Bedingungen ist genau dann wahr, wenn eine aber nicht beide der Bedingungen wahr sind. 
Ein Beispiel für den Exklusiv-Oder-Operator könnte wie folgt aussehen:

```cs
bool siegerStehtFest = spieler1HatVollePunktzahl ^ spieler2HatVollePunktZahl;
```

Ein Sieger kann nur dann feststehen wenn genau einer der beiden Spieler die volle Punktzahl erreicht hat. Haben beide die volle Punktzahl erreicht so gibt es keinen Sieger.

Präzedenz
---------

Die Rangfolge der Wahrheitsoperatoren ist `!`, `==`, `!=`, `^`, `&&`, `||`. So gilt beispielsweise:

```cs
true || true && false // true
```

Man sagt auch der Und-Operator bindet stärker als der Oder-Operator. Um ein anderes Verhalten zu erzielen kann man entsprechend einfach Klammern verwenden:

```cs
(true || true) && false // false
```

Umformungen
-----------

Es ist hilfreich ein paar Umformungen im Kopf zu haben die deinen Code besser lesbar machen können:

```cs
!(b1 && b2) <=> !b1 || !b2
!(b1 || b2) <=> !b1 && !b2
```

Dies sind die de-morganschen Gesetze der Aussagenlogik! Das untere der beiden Gesetze besagt zum Beispiel dass die folgenden beiden Codezeilen äquivalent sind:

```cs
bool spielGehtWeiter = !(spieler1HatGewonnen || spieler2HatGewonnen);
```

```cs
bool spielGehtWeiter = !spieler1HatGewonnen && !spieler2HatGewonnen;
```

-  "Das Spiel geht weiter falls nicht Spieler 1 oder Spieler 2 gewonnen hat."
- "Das Spiel geht weiter falls Spieler 1 nicht gewonnen hat und Spieler 2 nicht gewonnen hat".

In diesem Beispiel ist die erste Formulierung meiner Meinung nach etwas besser lesbar.

> Welche Form besser lesbar ist hängt sehr stark vom Einzelfall ab. Es lohnt sich beim Programmieren kurz innezuhalten und sich bewusst für eine der Formen zu entscheiden.

---

### [Kursinhalt](../README.md)
