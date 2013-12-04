<!-- 04.12.2013 -->
Tag 8
==========
Schritte auf dem Weg zum *perfekten* Möbelplaner.

### Analyse von Compiler Fehlern.

Sollten Syntax Fehler auftreten, werden diese sofort Compiler angeprangert
und dieser legt seine Arbeit nieder.

Angefangen hat es mit dem wohl einfachsten Fehler:

```java
farbe = "blau"
xPosition = 0;
```

Das fehlende Semicolon in Linie 1.

> ";" expected

Hier ist die Lösung vom Compiler direkt vorgegeben.

Weiter ging es mit falsch aufgerufenen Methoden:

```java
stuhl.moveTo(0);
```

> no suitable method found for moveTo(int)

Ist ja auch richtig. Tatsächlich sieht die Methode so aus:

```java
moveTo(int,int);
```

Ähnliches gab es auch gegen Ende nochmal

```java
leinwand.warte();
```

> method warte in class Leinwand cannot be applied to given types;
>
>    required: int found: no arguments reason: actual and formal argument list differ in length

Sonst ging es fröhlich weiter mit nicht richtig deklarierten Variablen:

```java
xPosition = 0;
```

> cannot find symbol - variable xPosition

Lösung hier ist es das Attribute hinzuzufügen oder die Variable irgendwie in den Scope
zu bekommen.

Es gab natürlich auch falsch deklarierte Variablen:

```java
Tisch tisch = new Ellipse2D.Double(0, 0, 0);
```

> incompatible types

Der Typ der Variable tisch sollte natürlich auch `Ellipse2D` sein:

```java
Ellipse2D tisch = new Ellipse2D.Double(0, 0, 0);
```

Selbstverständlich durften vergessene curly-braces auch nicht fehlen:


```java  
public class Foo {
    
  public void doStuff() {
    // do Stuff
    
}
```

> reached end of file while parsing

Hier fehlt die schließende Klammer der Methode.

Aber auch die klassische fehlerhafte Verwendung von doppelten `=` war dabei:

```java
farbe == "blaue";
```

> not a statement

Lösung 1 (eheste):

```java
farbe = "blau";
```

Lösung 2 (wahrscheinlich nicht gewollt, aber möglich):

```java
boolean assert = (farbe == "blau");
```

Besonders weil man String nicht mit `==` vergleichen kann. Dies vergleicht die Objekte
und nicht den String Inhalt. Dies würde so gehen:

```java
boolean assert = (farbe.equals("blau"));
```

> Dat war jo net too schwer!
