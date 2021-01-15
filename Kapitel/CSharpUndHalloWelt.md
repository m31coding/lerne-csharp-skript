### [Kursinhalt](../README.md)

C# und Hallo Welt
==================

Sprache und Programm
---------------------

C# ist eine moderne Sprache dies sich immer größerer Beliebtheit erfreut: [https://octoverse.github.com/](https://octoverse.github.com/). Ein großer Vorteil der Sprache ist dass sie **sehr flexibel** einsetzbar ist. Man kann sowohl Programme für Windows, Linux und Mac entwickeln, als auch Mobile-Apps für Android und iOS. Außerdem stellt Microsoft mit **Visual Studio** eine der besten Entwicklungsumgebungen zur Verfügung sodass man mit C# äußerst produktiv entwickeln kann. 

Wir können mithilfe einer Programmiersprache wie C# ein Programm schreiben welches vom Computer ausgeführt werden kann. Analog zu einer Fremdsprache muss man in einer Programmiersprache Vokabeln und Grammatik lernen und einen **korrekten Syntax** einhalten. Dies ist bei Programmiersprachen noch wichtiger als bei einer Fremdsprache, denn ein einzelnes falsches Zeichen kann dazu führen dass der Computer das Programm nicht versteht.

Ein Programm besteht im Wesentlichen aus **Datenstrukturen** und **Algorithmen**. Eine Datenstruktur dient der Speicherung und Organisation von Daten. Ein Algorithmus verwendet Datenstrukturen um ein vorgegebenes Problem Schritt für Schritt zu lösen.

Hallo Welt
-----------

In der Vorbereitung habt ihr euer erstes Projekt erstellt, das **Hello World** Projekt.

Startet das Programm indem ihr den grünen Pfeil drückt.

Das schwarze Fenster das sich öffnet nennt sich **Konsole**. Auf der Konsole kann das Programm Nachrichten ausgeben und auch Eingabe vom Benutzer eingelesen werden. Wir beschäftigen uns zunächst ausschließlich mit Konsolenprogrammen.

Der Befehl `Console.WriteLine` lässt euch Text auf die Konsole schreiben. Text muss in C# in Anführungszeichen gesetzt werden. Beachte außerdem dass jeder Befehl mit einem Semikolon `;` abgeschlossen werden muss.

Ändert nun den Text zu einer **individuellen Begrüßung**, z.Bsp: "Herzlich willkommen zum Programmierkurs!" Startet das Programm neu.

 Wir wollen in allen Projekten die neuste **.NET 5.0** Version und stellen das Projekt nun auf diese um. Mache hierzu einen Rechtsklick auf das Projekt *Hello World* im Projektmappenexplorer und wähle *Eigenschaften* aus. Als Zeilframework .NET 5.0.

 Außerdem wollen wir auch das neue Feature '**Nullwerte bei Referenztypen**' freischalten. Dazu machen wir einen Doppelklick auf das Projekt 'HelloWorld' und fügen die Zeile `<Nullable>enable</Nullable>` ein, sodass die Datei den folgenden Inhalt hat:

 ```
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <Nullable>enable</Nullable>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
 ```

 Speichere das Projekt indem du STRG+S drückst.

Syntax
-------

```cs
using System;

namespace HelloWorld
{
  class Program
  {
    static void Main(string[] args)
    {
      Console.WriteLine("Herzlich willkommen zum Programmierkurs!");    
    }
  }
}
```

Das Hallo Welt Programm hat die folgenden Komponenten:

- Codeblöcke
- Main Methode
- Befehl für Konsolenausgabe
- Namensraum
- Klasse
- Leerzeilen und Leerzeichen

Das Programm besteht aus drei Codeblöcken die jeweils durch geschweifte Klammern `{}` begrenzt werden. Die `Main`-Methode stellt den **Einstiegspunkt** des Programms dar. Alle Befehle die dort enthalten sind werden **der Reihe nach** von oben nach unten ausgeführt. 

**Namensräume** dienen der **Codeorganisation**, ähnlich Ordnern auf eurem Computer. Im HalloWelt Programm wird ein Namensraum definiert (`namespace HelloWorld`) und ein anderer Namensraum importiert (`using System`). Der letztere wird benötigt um die Methode `Console.WriteLine` aufrufen zu können.

Da es sich bei C# um eine **objektorientierte Sprache** handelt wird sämtlicher Code Klassen zugeordnet. Eine **Klasse** repräsentiert ein **Objekt** und ist äußert hilfreich um Sachverhalte und Dinge zu **modellieren**. Im HalloWelt Programm wird die Klasse `Program` definiert, welche das Programm selbst darstellt. Außerdem wird auf die Klasse `Console` zugegriffen, um eine Ausgabe zu erzeugen, die der Benutzer auf der Konsole lesen kann.

Zu Beginn könnt ihr noch nicht alles in diesem Programm verstehen aber wir werden uns Schritt für Schritt ein größeres Verständnis erarbeiten.


Kommentare 
-----------

Ihr könnt Code mit einzeiligen oder mehrzeiligen Kommentaren versehen. Für einzeiligen Code verwendet ihr einen doppelten Schrägstrich:

```cs
// Begrüßung
Console.WriteLine("Herzlich willkommen zum Programmierkurs!");  
```

Um einen Kommentar über mehrere Zeilen zu verfassen verwendet ihr den folgenden Syntax:

```cs
/*
 * Folgender Code gibt auf der Konsole "Herzlich willkommen
 * zum Programmierkurs!" aus.
 */
Console.WriteLine("Herzlich willkommen zum Programmierkurs!");  
```

Geht mit Kommentaren sparsam um und achtet darauf dass sie sinnvoll sind. Der mehrzeilige Kommentar an dieser Stelle ist wenig sinnvoll, da die gesamte Information bereits in der darauffolgenden Codezeile enthalten ist.

Erfahrene Programmierer können Code schreiben der auch ganz ohne Kommentare sehr sprechend ist und sich gut lesen lässt.

---

### [Kursinhalt](../README.md)