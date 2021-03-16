### [Kursinhalt](../README.md)

Verzweigungen mit switch
========================

<iframe width="560" height="315" src="https://www.youtube.com/embed/Vdijo9Haamk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Der Code zum Video:

```cs
using System;
using System.Collections.Generic;

namespace Switch
{
    class Program
    {
        static void Main(string[] args)
        {
            List<int> zahlen = new List<int>() { 1, 2, 3 };

            if (zahlen.Count == 0)
            {
                Console.WriteLine("Die Liste enthält keine Elemente!");
            }
            else if (zahlen.Count == 1)
            {
                Console.WriteLine("Die Liste enthält ein Element!");
            }
            else
            {
                Console.WriteLine("Die Liste enthält mehrere Elemente!");
            }

            // Kostantenmusterabgleich
            //

            string info = string.Empty;

            switch (zahlen.Count)
            {
                case 0:
                    info = "Die Liste enthält keine Elemente!";
                    break;

                case 1:
                    info = "Die Liste enthält ein Element!";
                    break;

                default:
                    info = "Die Liste enthält mehrere Elemente!";
                    break;
            }

            Console.WriteLine(info);

            info = zahlen.Count switch
            {
                0 => "Die Liste enthält keine Elemente!",
                1 => "Die Liste enthält ein Element!",
                _ => "Die Liste enthält mehrere Elemente!"
            };

            Console.WriteLine(info);

            // Typmusterabgleich
            //

            IEnumerable<int> weitereZahlen = new HashSet<int>() { 4, 5, 6 };

            string ausgabe = weitereZahlen switch
            {
                List<int> liste => $"Ich bin eine Liste mit {liste.Count} Elementen!",
                int[] array => $"Ich bin ein Array mit {array.Length} Elementen!",
                _ => $"Ich bin vom Typ {zahlen.GetType().Name}!"
            };

            Console.WriteLine(ausgabe);
        }
    }
}
```

---
### [Kursinhalt](../README.md)