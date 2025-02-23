# Die objektorientierte Programmierung (OOP)
Video: [OOP Klassen und Objekte](https://www.youtube.com/watch?v=c6RrcEvIix0)

**Objektorientierte Programmierung (OOP)** ist ein Programmierparadigma, das auf dem Konzept von "Objekten" basiert, welche Daten in Form von Attributen sowie Verhalten in Form von Methoden enthalten. OOP modelliert Situationen als eine Sammlung von Objekten, die miteinander interagieren. OOP basiert auf vier Grundprinzipien: Kapselung, Abstraktion, Vererbung und Polymorphismus.

**Klasse** ist eine Vorlage, die Attribute und Methoden zur Erstellung spezifischer Instanzen von Objekten definiert.

**Objekt** ist eine Instanz einer Klasse, die spezifische Werte für die in der Klasse definierten Attribute enthält und Methoden gemäß dieser Definitionen aufweist.

### Prinzipien der OOP
Artikel: [4 Principles](https://khalilstemmler.com/articles/object-oriented/programming/4-principles/)
- **Vererbung** ist ein Mechanismus, bei dem eine neue Klasse (Unterklasse) die Eigenschaften und Verhaltensweisen einer vorhandenen Klasse (Oberklasse/Superklasse) übernimmt. Dies ermöglicht Code duplizierung zu vermeiden, indem Methoden und Attribute wiederverwendet werden, die in der Basisklasse definiert sind[^1]. [Video](https://youtu.be/gifpyGpD-fE?si=VKiJZwBEaFKjVaAg&t=352)
- **Kapselung** bezeichnet das Prinzip, durch welches der interne Zustand eines Objekts vor direktem Zugriff von außen geschützt wird. Dies wird erreicht, indem man Attribute eines Objekts als privat deklariert und den Zugriff auf diese Daten über öffentliche Methoden regelt[^2]. [Video](https://www.youtube.com/watch?v=bnPSLyxvaUY)
- **Polymorphismus** ist die Fähigkeit von Objekten verschiedener Klassen, auf dieselben Methodenaufrufe zu reagieren, wobei jedes Objekt gemäß seiner Klassenimplementierung unterschiedliche Verhaltensweisen zeigen kann. Dies ermöglicht es, Methoden zu definieren, die in der Basisklasse deklariert sind, jedoch in abgeleiteten Klassen unterschiedlich implementiert werden, wodurch die Funktionalität überladen oder überschrieben wird[^3]. [Video](https://www.youtube.com/watch?v=jhDUxynEQRI)
- **Abstraktion** ist der Prozess, bei dem für den Nutzer relevanten Attribute und Verhaltensweisen eines Objekts hervorgehoben werden, wären die technische Implementierung verborgen bleibt.

[^1]: https://roberta-home.de/fileadmin/user_upload/WebBooks/JavaBand/RobertaBuchch7.html#x8-800007.2
[^2]: https://roberta-home.de/fileadmin/user_upload/WebBooks/JavaBand/RobertaBuchch7.html#x8-810007.3
[^3]: https://roberta-home.de/fileadmin/user_upload/WebBooks/JavaBand/RobertaBuchch7.html#x8-830007.4

### Vorteile von OOP [^4]
- **Modularität**: Die Kapselung in OOP fördert die Modularität, indem sie die Isolierung von Fehlerquellen erleichtert. Dies vereinfacht das Debugging, da sich Entwickler auf die fehlerhafte Klasse konzentrieren können.
- **Code-Wiederverwendung**: OOP ermöglicht die Wiederverwendung von Code durch Vererbung. Klassen können Merkmale und Methoden erben, was die Notwendigkeit reduziert, duplizierenden Code zu schreiben, was Zeit spart und Fehlerquellen reduziert.
- **Flexibilität**: Durch Polymorphismus bietet OOP die Flexibilität, Methoden anzupassen, die ihr Verhalten abhängig vom Kontext ändern können. Dies erleichtert die Entwicklung, indem der Code leichter an neue Anforderungen angepasst werden kann.
- **Abstraktion**: OOP ermöglicht es, große Projekte effektiv zu verwalten, indem Klassen als logische Repräsentationen von größeren Codeblöcken dienen.

### Nachrteile von OOP [^4]
- **Größere Programme**: Mit OOP geschriebene Programme sind tendenziell größer als solche, die prozedurale Programmierung verwenden. Dies kann zu einer langsameren Ausführung führen, da ihre Ausführung mehr Zeit in Anspruch nimmt.
- **Nicht für jedes Problem**: OOP ist nicht immer die beste Lösung. Es funktioniert am besten für Aufgaben, die durch Objekte ausgedrückt werden können, aber das Beispiel ist nicht geeignet für Einfache Skripte.

[^4]: https://www.xpheno.com/blogs/advantages-of-object-oriented-programming/

# Java Spickzettel
### Primitive Datentypen [^5]
Primitive Datentypen werden direkt in Variablen gespeichert. [Video](https://www.youtube.com/watch?v=WQ7mvQFSmYc)

| Type    | Values              | Default | Size                | Range                                     |
|---------|---------------------|---------|---------------------|-------------------------------------------|
| byte    | signed integers     | 0       | 8 bits              | -128 to 127                               |
| short   | signed integers     | 0       | 16 bits             | -32.768 to 32.767                           |
| int     | signed integers     | 0       | 32 bits             | -2.147.483.648 to 2.147.483.647                 |
| long    | signed integers     | 0       | 64 bits             | -9223372036854775808 to 9223372036854775807|
| float   | IEEE 754 floating point | 0.0   | 32 bits             | +/-1.4E-45 to +/-3.4028235E+38, +/-infinity, +/-0, NaN |
| double  | IEEE 754 floating point | 0.0   | 64 bits             | +/-4.9E-324 to +/-1.7976931348623157E+308, +/-infinity, +/-0, NaN |
| char    | Unicode character   | \u0000  | 16 bits             | \u0000 to \uFFFF                         |
| boolean | true, false         | false   | 1 bit used in 32 bit integer | NA                                |

[^5]: https://latestjavatutorials.blogspot.com/2013/05/java-data-types.html
### Implizites vs Explizites Casting
Implizites Casting in Java erfolgt automatisch, wenn der Compiler „niedrigeren“ Typ in den „höheren“, ohne Datenverlust-Risiko, während explizites Casting manuell durchgeführt werden muss, um größere Datentypen in kleinere zu konvertieren, oft mit einem Risiko des Datenverlusts.

### Implizites Casting [^7]
Wenn wir arithmetische oder mathematische Operationen mit Operanden unterschiedlichen Typs durchführen, führt der Java-Compiler intern eine implizite Konvertierung durch. Die folgende Abbildung zeigt, welche implizite Konvertierungen Java zulässt:
<p align="center"><img src="Img/k3_abb1.png" width="600"  title="Abb1"></p>

#### Implizites Casting Beispiel
```java
int intVal = 42;
double doubleVal = intVal;
```
### Explizites Casting [^7]
Konvertierung eines höheren Datentyps in einen niedrigeren Datentyp wird als einschränkende Konvertierung bezeichnet. Da diese Art der Konvertierung vom Programmierer und nicht automatisch vom Compiler durchgeführt wird, wird sie in Java auch als explizite Typumwandlung bezeichnet.

#### Explizites Casting Beispiel 
```java
double d = 100.9;
long l = (long) d; // Explicit type casting.
```

[^7]: https://www.scientecheasy.com/2020/07/type-conversion-casting-java.html/

## Listen (Arrays)
In Java, `Array` ist eine statische Struktur fester Größe, die homogene Datentypen enthält. Einmal erstellt, kann die Größe eines Arrays nicht geändert werden.

#### Deklaration
```java
int[] einArray = new int[10];
String[] stringArray = new String[5];
```

#### Deklaration und Initialisierung
```java
int[] zahlen = {1, 2, 3, 4, 5};
String[] worte = {"Hallo", "Welt"}; 
```

#### Zugriff auf Elemente
```java
int ersteZahl = zahlen[0];
zahlen[1] = 20;
```

#### Länge des Arrays
```java
int laenge = zahlen.length;
```

#### Durchlaufen mit einer Schleife
```java
for(String name : namen) {
    System.out.println(name);
}
```

## ArrayList
`ArrayList`, ist eine dynamische Struktur, die Objekte verschiedener Typen speichern kann und deren Größe automatisch anpasst, wenn Elemente hinzugefügt oder entfernt werden. Video: [Array vs ArrayList](https://www.youtube.com/watch?v=NbYgm0r7u6o)

#### Import
```java
import java.util.ArrayList;
```

#### Deklaration und Initialisierung
```java
ArrayList<String> namen = new ArrayList<>();
ArrayList<Integer> num = new ArrayList<>();
```
Achtung ` ArrayList<int> num = ... ` ist falsch !!!

#### Elemente hinzufügen
```java
namen.add("Anna");
namen.add("Bernd");
```

#### Zugriff auf Elemente
```java
String erstesElement = namen.get(0); 
```

#### Elemente entfernen
```java
// Entfernt "Bernd" aus der Liste
namen.remove(String.valueOf("Bernd"));

// Entfernt das Element an Index 0
namen.remove(0);
```

#### Größe der ArrayList
```java
int groesse = namen.size();
```

## 2D-Listen (2D Arrays)

#### Deklaration
```java
// Eine 2x3 Matrix (zwei Zeilen drei Spalten)
int[][] matrix = new int[2][3];
```

#### Deklaration und Initialisierung
```java
int[][] positionen = {
    {0, 0, 3},
    {1, 1, 2},
};
```

#### Zugriff auf Elemente
```java
// Zugriff auf das Element in Zeile 0, Spalte 1
int element = positionen[0][1]; 

// Setzen des Elements in Zeile 1, Spalte 1 auf 5
positionen[1][1] = 5; 
```

## Zugriffsmodifikatoren [^6]

| Modifikator  | Klassenintern | Paketintern | Subklassen | Weltweit |
|--------------|---------------|-------------|------------|----------|
| **public**   | Ja            | Ja          | Ja         | Ja       |
| **protected**| Ja            | Ja          | Ja  | Nein  |
| *(kein Modifikator)* | Ja   | Ja          | Nein       | Nein     |
| **private**  | Ja            | Nein        | Nein       | Nein     |

*_(alle Klassen ohne explizit angegebenes Paket gehören zum Standardpaket)_

#### Beschreibung

- **public**: Das Element ist von überall her zugänglich.
- **protected**: Das Element ist innerhalb derselben Klasse, im selben Paket und in abgeleiteten Klassen zugänglich.
- **(kein Modifikator)**: Auch bekannt als "package-private", das Element ist nur innerhalb des eigenen Pakets zugänglich.
- **private**: Das Element ist nur innerhalb der Klasse zugänglich, in der es deklariert wurde.

[^6]: https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html

# Java Kommentare
#### Einzeilige Kommentare

```java
// Dies ist ein einzeiliger Kommentar
int number = 5;
```

#### Mehrzeilige Kommentare
```java
/* Dies ist ein
   mehrzeiliger Kommentar */
int number = 5;
```
### Javadoc
Javadocs sind eine spezielle Form von Kommentaren, die verwendet werden, um eine offizielle Dokumentation in HTML-Format zu generieren. Hier sind einige häufig verwendete Tags in Javadocs:
Javadoc-Kommentare beginnen mit `/**` und enden mit `*/`, jede Javadocs Kommentar Zeile soll ein Stern am Anfang haben.

#### @param
Das `@param`-Tag wird verwendet, um einen Parameter zu beschreiben, der von einer Methode angenommen wird. 

#### @return
Das `@return`-Tag beschreibt den Rückgabewert einer Methode.

#### @throws
Das `@throws`-Tag beschreibt die Ausnahmen, die von einer Methode geworfen werden können.

Beispiel für eine Javadoc-Kommentierung:

```java
/**
 * Berechnet die Division zweier Ganzzahlen.
 * @param divisor Der Divisor.
 * @param dividend Der Dividend.
 * @return Das Ergebnis der Division.
 * @throws ArithmeticException wenn der Divisor gleich 0 ist.
 */
public int divide(int dividend, int divisor) {
    if (divisor == 0) {
        throw new ArithmeticException("Divisor cannot be zero");
    }
    return dividend / divisor;
}
```


