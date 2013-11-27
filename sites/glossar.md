# Glossar


In diesem Glossar werden Grundlegende Begriffe erklärt.


- ### Quelltext

    Der Quelltext ist der für den Menschen lesbare Programmcode.
- ### Klasse

    Eine Klasse ist eine Art Bauplan für ein [*Objekt*](#objekt).
    
    Diese Klasse ist festgeschrieben im [*Quelltext*](#quelltext).
    Es gibt auch sogennante **anonyme Klassen**, sie beruhen auf einer abstrakte Klasse oder eines Interfaces.
    
- ### Objekt

    Ein Objekt ist eine Instanz einer Klasse und existiert nur auf dem Heap der JavaVM.
    Objekte werden genutzt, um die Klasse zu nutzen.

- ### Methoden

    Methoden sind ein Teil einer [*Klasse*](#klasse). Sie führen Aktion durch und können die [*Variablen*](#variabel)
    des Objektes modifizieren. Sie können Parameter benötigen und Werte zurück geben.
    Sie können eine von 3 verschiedenen Sichtbarkeits-Stufen haben:
    ```
    public
    protected
    private
    ```
    Hierbei sagt `public` aus, dass die Methode von überall aufgerufen werden kann.
    `private` hingegen verbietet den externen Zugriff und nur die Klasse selber hat Zugriff dadrauf,
    `protected` ist da sehr ähnlich, lässt jedoch Zugriff von Kind (child) Klassen zu.
    
    #### Sichtbarkeiten kann man sich so vorstellen:
    
    
    Wenn du zu McDonald's gehst und einen BigMac bestellst, "rufst" du die Methode `getBigMac()` auf.
    
    Im Restaurant werden jetzt viele andere Methoden ausgeführt (wie z.B. `getSalad()` or even `killCow()`).
    
    All diese Operation musst du als Nutzer gar nicht kennen und solltest diese eigentlich auch nicht "stand-alone" ausführen.

- ### Kommentar

    Kommentare sind ausschließlich für den Menschen gedacht und Helfen den [*Quelltext*](#quelltext) zu verstehen.
    Sie werden in Java (und vielen anderen Sprachen) so erstellt:
    
    ```java
        // Diese Zeile ist ein Kommentar
        /*
        * Hier werden mehrere Zeilen auskommentiert
        * (bis zum nächsten:
        */
        
        /**
         * Diese Art von Kommentar Deklaration wird für JavaDoc
         * über Klassen, Variablen und Methoden verwendet.
         */
    ```

- ### Compiler

    Der Compiler "konvertiert" den [*Quelltext*](#quelltext) in Maschienen Code, der von dem Computer
    verstanden wird. Diesen Vorgang nennt sich "compilation". Maschienen Code ist nicht lesbar für den
    Menschen.

- ### Variabel

  Variablen werden in der Klasse deklariert:
  ```java
      public int count = 5;
      public int count;
      private int count;
      private static int count;
      private static final int count;
  ```
  Variablen dienen der Speicherung von Information in einem Objekt.
  
  Sie können wie [*Methoden*](#methoden) unterschiedliche
  [*Sichtbarkeiten*](#sichtbarkeiten-kann-man-sich-so-vorstellen) haben.

- ### Vererbung

    Vererbung kann genutzt werden um eine *Is-a* Beziehung herzustellen. Die einfachste Art der Vererbung ist die
    Erstellung einer Child-Class mittels des `extends` Schlüsselwortes, z. B.:
    
    ```java
    public class Foo extends Bar
    { }
    ```
    
    In dem Beispiel erbt `Foo` alle Eigenschaften von `Bar` (außer `private`). Sollte `Bar` eine Methode `baz` haben,
    so könnte man diese auch von `Foo` aufrufen.
    
    ```java
    public class Bar
    {
        public void baz() {
            // do-nothing
        }
    }
    
    public class Foo extends Bar
    {
        @Override
        public void baz() {
            this.child();
        }
        
        protected void child() {
            // do-nothing
        }
    }
    ```
    
    In dem obigen Beispiel wird gezeigt, wie Methoden im *child* noch geändert werden können.
    
    Mittels der `@Override` Annotation.

- ### Beziehungen

    Eine **Hat-Beziehung** ist eine Bezeichung von einer Relation zwischen, streng genommen, zwei Objekten.
    In einer Komposition oder Zerlegung (die Hat-Beziehung) *besitzt* Objekt A Objekt B,
    letzteres kann nicht ohne Objekt A existieren.
    
    Beispiel:
    
    > Ein Blogpost **hat** mehrere Kommentare. Ein solches Kommentar kann ohne den Blogpost nicht existieren.
    
    Diese Art nennt man **Komposition**. Nun stellt sich die Frage wie es aussieht mit lockeren Beziehung.
    Das Beispiel wäre hier:
    
    > Ein Blogpost hat ein Bild eingebunden. Das Bild kann auch ohne den Blogpost existieren.
    
    Eine solche Beziehung nennt man **Aggregation**.
    
    Neben der **Hat-Beziehung** existiert auch noch eine sogenannte **Kennt-Beziehung** (*Assoziation*).
    
    Das Beispiel hierzu wäre analog:
    
    > // Kommt noch!
