<!-- 13.11.2013-->
Tag 6
==========
Schritte auf dem Weg zum *perfekten* Möbelplaner.

Ein Stuhl so im leerem Raum sieht man selten; aus diesem Grund sollte eine Factory her,
die es für uns übernehmen sollte 4 Stühle und einen Tisch zu platzieren.

Die Stühle sollten hierbei so angeordnet werden:

```
      +---+   +---+
      |   |   |   |
      +---+   +---+
        +--------+
        |        |
        +--------+
      +----+  +----+
      |    |  |    |
      +----+  +----+
```

(Hierbei soll der Tisch natürlich rund sein!)


Die Umsetzung des Factory-Patterns wer sehr einfach:

```java

final class Tischgruppe extends Moebelstueck
{

  private Moebelstueck s1;
  private Moebelstueck s2;
  private Moebelstueck s3;
  private Moebelstueck s4;
  private Moebelstueck t1;
  
  public Tischgruppe(int x, int y, [...])
  {
    s1 = new Stuhl(x, y [...]);
    // [...]
  }
  
  @Override
  public void dreheAuf(int neuerWinkel)
  {
    super(neuerWinkel);
    s1.dreheAuf(neuerWinkel);
    // [...]
  }
  
  // [...]

  @Override
  protected Shape gibAktuelleFigur()
  {
    return null;
  }

}
```

Hierbei ist die Factory ebenfalls ein `Moebelstueck`, da sie die gleichen Methoden wie ein solches implementiert.
Alle Methoden werden zwar überschrieben, aber das Interface bleibt bestehen!

Die abstrakte Methode `gibAktuelleFigur()` gibt hier einfach nur `null` zurück,
da die Figuren durch die Möbelstücke selber generiert und gerendert werden.
