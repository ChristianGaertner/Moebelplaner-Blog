Tag 1
==========
Schritte auf dem Weg zum *perfekten* Möbelplaner.

#### Was wollen wir erreichen?


Los ging es mit einem Starter-Template, welches eine einfache API darstellt, im Formen in einen JFrame/Canvas zu zeichnen.

Das ganze war und ist immer noch weit weg von optimal. Probleme mit dem Starter-Set stellten dar:

* Inkonsistente  API
* Schlechte "Aufgaben"-Verteilung (dazu später mehr)
* Umständliche Methoden und Klassen

So musste man nach dem erstellen eines neuen "Stuhl" Objektes mittels einer ```move()``` die Position verändern so ging es mit allen Attributen. Stunden-Aufgabe war es also das ganze zu erleichtern, d.h. Werte sollten beim erstellen eingegeben werden können.

Außerdem sollte das rendern automatisiert werden. Derweil muss man stets ```zeige()``` aufrufen.

Dies ist selbsverständlich eine äußert einfache Aufgabe und kann in wenigen Sekunden so gelöst werden:


    public Stuhl(int x, int y, String farbe, int orientation) {
        xPosition = x;
        yPosition = y;
        sichtbar = true;
        this.farbe = farbe;
        this.orientation = orientation;
        zeige();
    }


Um das ganze noch einfacher zu gestalten werde ich ein paar overloading Konstruktore erstellen:

    public Stuhl(int x, int y) {
        this(x, y, "blau", 0);
    }

    public Stuhl(int x, int y, String farbe) {
        this(x, y, farbe, 0);
    }
    
    public Stuhl() {
        this(0, 0, "blau", 0);
    }


Dies einfach nur, damit man nicht jedes Mal alle Werte angeben muss.

## TODO

* Komplettes Refactoring.


### Refactoring

Was möchte ich neu machen?

**Alles!**

Dieses Programm wurde geschrieben, um Schülern das Programmieren näher zu bringen. Das bringt natürlich mit sich, dass es weder performant, noch test-bar (Unit Tests), geschweige denn erweiterbar ist.

Außerdem macht mich die API-Inkonsequenz verrückt:

    public void drehe(int orientation)

Setzt (```=```) den Wert (aka. *absolut*), während

    public void bewege(int entfernung)

ihn verändernt (```+=```) (aka. *relativ*).


#### Wie soll das neue Setup nun aussehen?

Eine  ```Designer``` rendert ein Bild, dass es von dem ```Renderer``` bekommt. Der ```Renderer``` bekommt die Bildinformation jeweils aus den verschiedenen ```Entites```.

Diese ```Entites``` werden alle von einem ```Grid``` Objekt in einer ```ArrayMap``` gespeichert und 50mal pro Sekunde geupdated:

     for(Entity e : entities) {
         e.update();
     }

Durch dieses ```update()``` Methode werden die Bild-Daten erneut an den ```Renderer``` übergeben, außerdem wird die Position geändert (falls erforderlich).

Die Position einzelener ```Entites``` wird durch einen ```MouseListener``` bestimmt, welcher durch eine ```UI``` die ```Entites``` anspricht.

Das ganze jetzt nur als groben Plan, aber ich möchte mit Sicherheit mehr Abstraktion mit reinbringen und solche Dinge eliminieren:

     public void bewegen(int entfernung) {
          verberge();
          xPosition += entfernung;
          zeige();
     }
     
und wie gesagt durch das aufrufen einer ```update()``` Methode vereinfachen. Mehr dazu aber später.
