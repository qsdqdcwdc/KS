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

## Zugriffsmodifikatoren

| Modifikator  | Klassenintern | Paketintern | Subklassen | Weltweit |
|--------------|---------------|-------------|------------|----------|
| **public**   | Ja            | Ja          | Ja         | Ja       |
| **protected**| Ja            | Ja          | Ja  | Nein  |
| *(kein Modifikator)* | Ja   | Ja          | Nein       | Nein     |
| **private**  | Ja            | Nein        | Nein       | Nein     |

#### Beschreibung

- **public**: Das Element ist von überall her zugänglich.
- **protected**: Das Element ist innerhalb derselben Klasse, im selben Paket und in abgeleiteten Klassen zugänglich.
- **(kein Modifikator)**: Auch bekannt als "package-private", das Element ist nur innerhalb des eigenen Pakets zugänglich.
- **private**: Das Element ist nur innerhalb der Klasse zugänglich, in der es deklariert wurde.

## Listen (Arrays)
In Java, `Array` ist eine statische Struktur fester Größe, die homogene Datentypen enthält. Einmal erstellt, kann die Größe eines Arrays nicht geändert werden.

### Deklaration
```java
int[] einArray = new int[10]; // Ein Array mit 10 Integern
String[] stringArray = new String[5]; // Ein Array mit 5 Strings
```

### Initialisierung
```java
int[] zahlen = {1, 2, 3, 4, 5}; // Initialisierung mit Werten
String[] worte = {"Hallo", "Welt"}; // Initialisierung mit Strings
```

### Zugriff auf Elemente
```java
int ersteZahl = zahlen[0]; // Zugriff auf das erste Element
zahlen[1] = 20; // Setzen des zweiten Elements auf 20
```

### Länge des Arrays
```java
int laenge = zahlen.length; // Gibt die Länge des Arrays zurück
```

## 2D-Listen (2D Arrays)

### Deklaration
```java
int[][] matrix = new int[2][3]; // Eine 2x3 Matrix (zwei Zeilen drei Spalten)
```

### Initialisierung
```java
int[][] positionen = {
    {0, 0},
    {1, 1},
    {2, 2}
}; // Initialisierung mit Werten
```

### Zugriff auf Elemente
```java
int element = positionen[0][1]; // Zugriff auf das Element in Zeile 0, Spalte 1
positionen[1][1] = 5; // Setzen des Elements in Zeile 1, Spalte 1 auf 5
```

## ArrayList
`ArrayList`, ist eine dynamische Struktur, die Objekte verschiedener Typen speichern kann und deren Größe automatisch anpasst, wenn Elemente hinzugefügt oder entfernt werden.

### Import
```java
import java.util.ArrayList; // Importiert die ArrayList-Klasse
```

### Deklaration und Initialisierung
```java
ArrayList<String> namen = new ArrayList<>(); // Erstellt eine neue ArrayList für Strings
```

### Elemente hinzufügen
```java
namen.add("Anna"); // Fügt "Anna" am Ende der Liste hinzu
namen.add("Bernd");
```

### Zugriff auf Elemente
```java
String erstesElement = namen.get(0); // Zugriff auf das erste Element
```

### Elemente entfernen
```java
namen.remove("Bernd"); // Entfernt "Bernd" aus der Liste
namen.remove(0); // Entfernt das Element an Index 0
```

### Größe der ArrayList
```java
int groesse = namen.size(); // Gibt die Größe der ArrayList zurück
```

### Durchlaufen der ArrayList mit einer Schleife
```java
for(String name : namen) {
    System.out.println(name);
}
```

