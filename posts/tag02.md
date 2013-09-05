<!-- 04.09.2013 -->
Tag 2
==========
Schritte auf dem Weg zum *perfekten* Möbelplaner.

#### Was wollen wir erreichen?

Nachdem wir unsere `Stuhl` Klasse verbessert hatten, sollte nun ein neues Möbelstück her:

Ein Schrank:

Dieser sollte in etwa so aussehen:
```
   +------------------------------------+
   |--                               -- |
   |        --               --         |
   |                -- --               |
   |                -- --               |
   |        --               --         |
   |--                              --  |
   +------------------------------------+
```

#### Erreichen des Zieles

Begonnen wurde mit dem Kopieren der Stuhl-Klasse und ein einfaches Search&Replace:

    "Stuhl" -> "Schrank"

Somit hatten wir schon einen Schrank, der wie ein Stuhl aussah.

Einzig alleine musste die "Zeichnung" der Geometrie angepasst werden.

Angefangen wurde mit einem Rechteck:

      GeneralPath schrank = new GeneralPath();
      Rectangle2D rec = new Rectangle2D.Double(0, 0, breite, tiefe);
      schrank.append(rec, false);

Das Kreuz selber war im nachhinein auch furchtbar einfach umzusetzten:

      schrank.moveTo(0, 0);
      schrank.lineTo(breite, tiefe);
      schrank.moveTo(0, breite);
      schrank.lineTo(0, tiefe);

Doch um da hinzukommen musste man die Funktionsweise der Library erstmal verstehen (dies ist mir und anderen zunächst etwas schwer gefallen).

Man muss sich daran gewöhnen, dass man sozusagen an den vorherigen method-call anschließt. Rufen wir `moveTo(int x, int y)` auf,
so bewegen wir einen "Cursor" an diese Stelle und der nächste call gibt die nächste Koordinate an. Dort wird dann eine Linie hingezeichent:

     lineTo(int x, int y)
     
Hat man dieses Prinzip einmal verstanden, dann geht alles andere auch leicht von statten.

Ich selber fände es schön wenn die `GeneralPath` Klasse aus dem Java AWT Geom package (`java.awt.geom.GeneralPath`)
[Method Chaining](http://en.wikipedia.org/wiki/Method_chaining)
unterstützen würde, so dass man folgendes machen könnte:

    GeneralPath p = new java.awt.geom.GeneralPath();
    p.moveTo(0, 0).lineTo(5, 4).lineTo(8, 4).moveTo(5, 5).lineTo(0, 0);

So würde es für **mich** klarer werden, dass die jeweiligen "calls" sich auf den vorherigen beziehen.

**Hinweis:** Die zweite Linie des obigen Code-Snippets ist **nicht** korrekt. Die genutzen Methoden geben `void`,
also nichts, zurück, sodass Method Chaining **nicht** möglich ist (dafür müssten sie das Objekt selber returnen):

    public class ChainMe {
      public ChainMe() {
       // set up some stuff
      }
      
      public ChainMe with() {
        return this;
      }
      
      public ChainMe ease() {
        return this;
      }
    }
    // Usage:
    ChainMe chainme = new ChainMe();
    chainme.with().ease();
    
