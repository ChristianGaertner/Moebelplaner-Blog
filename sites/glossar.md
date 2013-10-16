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

- ### Kommentar

    Kommentare sind ausschließlich für den Menschen gedacht und Helfen den [*Quelltext*](#quelltext) zu verstehen.
    Sie werden in Java (und vielen anderen Sprachen) so erstellt:
    
    ```java
        // Diese Zeile ist ein Kommentar
        /*
        * Hier werden mehrere Zeilen auskommentiert
        * (bis zum nächsten */)
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
