<p align="center">
	<img src="Img/qr_klas4.png" width="250"  title="qr code">
	<br>
	<em>QR-Code scannen um dieses Dokument auf dem iPad zu öffnen</em>
</p>

1. <code>Aktualisieren Sie die Seite bei jedem Aufruf, um die neueste Version dieses Dokuments zu erhalten.</code>

2. <code>Korrekturen und Ergänzungen zu diesem Dokument sind erwünscht. Bitte fügen Sie diese in [Google Docs](https://docs.google.com/document/d/12Gqtnn5DdQmN6GDQs-ADqzZjTsvVcVF5w9dpGsSQXM4/edit?usp=sharing) ein (oder senden Sie mir die persönlich). Ich werde versuchen, sie so schnell wie möglich zu integrieren.</code>


# Inhaltsangabe

- [Inhaltsangabe](#inhaltsangabe)  
- [Generische Datentypen](#generische-datentypen)  
- [Rekursion](#rekursion)  
- [Schnittstellen](#schnittstellen)  
- [Java Collections Framework](#java-collections-framework)  
- [Sortierverfahren](#sortierverfahren)  


# Generische Datentypen
[Video](https://www.youtube.com/watch?v=K1iu1kXkVoA)

**Generische Datentypen** (Generics) sind ein Konzept in der Programmierung, bei dem Klassen, Schnittstellen oder Methoden mit Platzhaltern für Datentypen definiert werden können. Diese Platzhalter (z. B. `<T>`) werden bei der Verwendung durch konkrete Typen ersetzt, sodass selbe Code mit verschiedenen Datentypen arbeiten kann ohne dabei Typsicherheit zu verlieren.

**Typsicherheit** (Type Safety):  Diese Eigenschaft einer Programmiersprache (oder einer Programm) zielt darauf ab, Fehler zu minimieren oder zu verhindern, die aus der Anwendung von Operationen auf inkompatibler Datentypen resultieren. In einer typsicheren Umgebung dürfen Operationen und Datenmanipulationen nur mit kompatiblen Datentypen durchgeführt werden.

Wieso kann man nicht einfach Methode mit Parameter von dem Datentyp `Objekt` definieren, dann könnte man es mit jedem Datentyp verwenden?
> Wenn man einen Parameter einfach vom Typ `Objekt` definiert, kann man zwar beliebige Datentypen übergeben, aber das hat Nachteile. Insbesondere verliert man dabei die Information, welcher konkrete Typ tatsächlich übergeben wurde. Das führt oft dazu, dass man auch den Rückgabewert als von Typ `Objekt` behandeln muss. Das kann später zu Problemen führen, weil nicht mehr klar ist, welche Operationen auf dem Objekt überhaupt zulässig sind.


### Vorteile von Generischen Datentypen
- **Keine Typumwandlung notwendig**.
- **Typprüfung zur Compile-Zeit:** Fehler werden früher erkannt.
- **Code-Wiederverwendbarkeit**: Durch die Verwendung von Generics kann derselbe Code für verschiedene Datentypen verwendet werden.

   
### Generische Klassen  
**Generische Klasse**: Eine generische Klasse in Java ermöglicht es, Klassen mit einem Typen-Platzhalter zu definieren, der beim Erstellen von Objekten der Klasse durch einen spezifischen Typ ersetzt wird.  
   
```java  
public class Box<T> {  
    // T steht für "Type"  
    private T t;  
    ... 
}  
```  
   
Deklaration und Initialisierung von einer generischer Klasse:
```java  
// Deklaration
Box<Integer> integerBox;

// Initialisierung
integerBox = new Box<>()

// Deklaration und Initialisierung
Box<Integer> integerBox = new Box<>();  // Den Typ muss man in Box<>() zweites Mal nicht wiederholen 

integerBox.set(123);  
Integer someInteger = integerBox.get();  
```  
Achtung: Generische Klassen darf man nicht einfach mit elementaren Datentypen (int, float, boolean) deklarieren dafür braucht man sog. „Wrapper Classes” für elementare Datentypen. Wrapper-Klassen ermöglichen die Verwendung von primitiven Datentypen als Objekte.  Die folgende Tabelle zeigt den primitiven Datentyp und die entsprechende Wrapper-Klasse:
| Primitive Data Type | Wrapper Class |
|---------------------|---------------|
| byte                | Byte          |
| short               | Short         |
| int                 | Integer       |
| long                | Long          |
| float               | Float         |
| double              | Double        |
| boolean             | Boolean       |
| char                | Character     |
   
### Generische Methoden  

**Generische Methode**: Eine Methode, die mit einem Typen-Platzhalter definiert wird.
   
```java  
public class Utility {  
    // Generische Methode  
    public static <T> void print(T t) {  
        System.out.println(t);  
    }  
}  
 
Utility.print("Hello");  
Utility.print(10);  
Utility.print(3.14);  
```  



### Begrenzung von Generischen Typen (Generic Bounds)

**Bounded Type Parameters**: Mit **Bounds** kann man einschränken, welche Typen für den Platzhalter zulässig sind. Man kann sicherstellen, dass ein generischer Typ nur Klassen oder Interfaces einer bestimmten Hierarchie verwendet.
Verwendet man `extends`, beschränkt man den generischen Typ auf eine Oberklasse oder ein Interface.

**Syntax:** `<T extends KlasseOderInterface>`

**Beispiel:**
```java
public class DataProcessor<T extends Number> {
    public double doubleValue(T value) {
        return value.doubleValue();  // Nur möglich, weil T garantiert ein Number ist
    }
}

DataProcessor<Integer> dp1 = new DataProcessor<>();
DataProcessor<Double> dp2 = new DataProcessor<>();
DataProcessor<String> dp3 = new DataProcessor<>();  // Fehler, da String nicht von Number erbt
```




### Mehrere Schranken (Multiple Bounds)
Ein generischer Typ kann **eine Klasse** und **beliebig viele Interfaces** erben/implementieren – **die Klasse muss zuerst stehen**.

**Beispiel:**
```java
public class KlassName<T extends Klass1 & Interface1 & Interface> {
    public void process(T doc) {
        ...
    }
}
```




## Mehrere Generische Typen
Man kann einer Klasse oder Methode **mehrere Typ-Platzhalter** geben.

**Syntax:** `<T, U, V>`

**Beispiel – Klasse mit mehreren Typen:**
```java
public class Pair<T, U> {
    private T first;
    private U second;
    ...
}

Pair<String, Integer> p = new Pair<>("Alter", 30);
```
### Wildcards in Generics
**Wildcards** (`<?>`) sind Platzhalter für unbekannte Typen in generischen Typangaben. Ohne Wildcards kann man z. B. keine Methode schreiben, die **alle** `List<T>`-Typen akzeptiert, z. B. `List<Integer>`, `List<Double>` usw., da `List<Object>` **nicht** Oberklasse von `List<Integer>` ist. Wildcards lösen dieses Problem mit `List<?>`.

Akzeptiert **beliebigen Typ**.
```java
public void printList(List<?> list) {
    for (Object elem : list) {
        System.out.println(elem);
    }
}
```
Man kann auch Schranken an Wirecards anwenden: `<? extends Animal>`

### Untere Schranke – `super`

**Unterschranke** (Lower Bound) in Generics wird mit dem Schlüsselwort `super` angegeben. Sie wird hauptsächlich bei **Wildcards (`<?>`)** verwendet und bedeutet: "Akzeptiere den angegebenen Typ oder einen seiner Obertypen".

Dabei steht `T` für eine bestimmte Klasse, und `? super T` erlaubt:
- `T`
- Oberklassen von `T` (z. B. `Object`, `Number`, …)

#### Beispiel: Verwendung in Methodenparametern
```java
public static void addNumbers(List<? super Integer> list) {
    list.add(42);  // Hinzufügen ist erlaubt
}
```

### Fachbegriffe zu generischen Datentypen 
| Begriff                                  | Beispiel                                                 |
|------------------------------------------|----------------------------------------------------------|
| parametrisierter Typ<br>(engl. parameterized type)     | `List<Integer>`                                          |
| formaler Typparameter<br>(engl. formal type parameter) | `E`  in `List<>`                                        |
| konkreter Typparameter<br>(engl. actual type parameter)| `Integer` in  `List<Integer>`                            |
| Originaltyp<br>(engl. raw type)                        | `List`                                                   |



# Rekursion

[Video](https://www.youtube.com/watch?v=k-7jJP7QFEM)[


**Definition**: Rekursive Funktionen zeichnen sich dadurch aus, dass sie sich in ihrem Verlauf selbst aufrufen können. Bei einem rekursiven Aufruf (**Rekursionsschritt**) wird das zu lösende Problem (d.h. die Parameter des Aufrufs) typischerweise verkleinert, bis die Problemgröße irgendwann so gering ist, dass das Problem direkt gelöst werden kann (**Rekursionsbasis**).

Der **Rekursionsbasisfall** einer rekursiven Funktion $R(p)$ mit einem oder mehreren Parametern $p$ beschreibt jene Werte von $p$, für die $R(p)$ ohne weitere direkte oder indirekte Selbstaufrufe ausgeführt wird. z.B für eine rekursive Funktion der fibonacci Reihe $Fib(n)$ sind $Fib(0)$ und $Fib(1)$ die Basisfälle, weil die einfach nach Definition gleich 0 und gleich 1 sind. 

Man kann garantieren dass eine rekursive Funktion  $R(p)$  für irgendeine spezifischen parametenwert $p$  terminieren wird, nur dann wenn man zeigt dass alle Rekursionszweige die bei Aufrufen von $R(p)$ entstehen in einem Basisfall enden. Daher lohnt es sich, beim Entwurf einer rekursiven Funktion darauf zu achten, dass jeder rekursive Aufruf mit einem kleineren Parameterwert erfolgt und der Basisfall dem kleinsten möglichen Wert entspricht, mit dem die Funktion aufgerufen werden kann. So lässt sich die Termination der Rekursion zuverlässig garantieren. 

Eine rekursive Funktion, die bei einem Durchlauf höchstens einen rekursiven Aufruf ausführt, wird **lineare Rekursion** genannt. Sind mehrere Rekursionsaufrufe möglich, spricht man von **kaskadenförmiger Rekursion**.

## Was passiert beim rekursiven Aufruf im Speicher?

Wenn eine rekursive Funktion ausgeführt wird, merkt sich der Computer bestimmte Informationen über jeden Funktionsaufruf, bevor der nächste beginnt. Dies passiert automatisch und folgt dem sogenannten **Stack-Prinzip**.

### Stack (Stapelprinzip)

**Stack** bezeichnet eine spezielle Speicherstruktur, bei der das **Last-In-First-Out (LIFO)**-Prinzip gilt: Die zuletzt gespeicherte Information wird als erstes wieder entfernt.

Bei jedem Funktionsaufruf – ob rekursiv oder nicht – wird folgendes gespeichert:
- Die Stelle im Programm, an der es nach dem Funktionsaufruf weitergehen soll.
- Die Werte der Parameter, die an die Funktion übergeben wurden.
- Die lokalen Variablen innerhalb der Funktion.

Diese Informationen werden **aufeinander gestapelt**, d.h. jeder neue Aufruf wird oben auf dem Stapel gelegt. Sobald eine Funktion fertig ist, wird sie vom Stack entfernt, und das Programm setzt an der gespeicherten Rücksprungstelle fort.

### Stack-Überlauf (Stack Overflow)

Da bei jedem rekursiven Aufruf Speicherplatz im Stack belegt wird, kann es passieren, dass der Stack voll wird – besonders wenn:
- keine **Abbruchbedingung** existiert (Endlosschleife)
- die Startparameter sehr groß sind 

Das führt zu einem **Stack Overflow**, einer Laufzeitfehler-Meldung, die signalisiert, dass zu viele Funktionsaufrufe gleichzeitig im Speicher liegen. 


# Schnittstellen
[Video](https://youtu.be/HvPlEJ3LHgE?feature=shared&t=255)

**Schnittstelle (Interface)**: Eine Schnittstelle in Java ist eine Referenztyp-Definition, die nur Konstanten, abstrakte Methoden, statische Methoden oder `default`-Methoden enthalten kann. Es dient als Vertrag, den implementierende Klassen erfüllen müssen.

### Eigenschaften von Interfaces
- Konnen Abstrakte Methoden/(Methodensignaturen) enthalten. **Abstrakte Methoden** sind Methodendeklarationen ohne Implementierung. Sie zwingen implementierende Klassen dazu, eine konkrete Implementierung bereitzustellen.
- Konnen Default-Methoden enthalten. Default-Methoden sind Methoden mit einer Standardimplementierung in einem Interface. Wenn eine Klasse ein Interface mit einer Default-Methode implementiert, muss sie diese Methode nicht überschreiben, sofern sie die Standardimplementierung verwenden will.
- Konnen Statische Methoden enthalten. **Statische Methoden** sind Methoden, die zur Klasse und nicht zur Instanz gehören. Sie können über den Interfacenamen direkt aufgerufen werden und haben Zugriff nur auf andere statische Mitglieder. Die implementieren den Klassen vererben nicht statische Methoden von dem Interface.
- Können Konstanten (`public static final`) enthalten. **Konstanten** sind unveränderliche Werte, die mit den Modifizierern `public static final` deklariert werden. Sie sind zur Compile-Zeit festgelegt und können nicht mehr geändert werden. Die implementieren den Klassen vererben nicht Konstanten von dem Interface. Aber die Konstanten sind ohne Namenpräfix innerhalb von der implementierenden Klasse zugänglich.
- Unterstützen Mehrfachvererbung (eine Klasse kann mehrere Interfaces implementieren).  
- Können nicht instanziiert werden.
- Können nicht Konstruktoren enthalten.

### Unterschiede zwischen Interface und abstrakter Klasse

| Kriterium                | Interface                           | Abstrakte Klasse                    |
|-------------------------|-------------------------------------|-------------------------------------|
| Schlüsselwort           | `interface`                         | `abstract class`                    |
| Methoden                | Standardmäßig alle abstrakt         | Kann konkrete und abstrakte Methoden enthalten |
| Felder                  | Nur Konstanten                      | Instanzvariablen und Konstanten     |
| Konstruktoren           | Keine                               | Kann Konstruktoren enthalten        |
| Mehrfachvererbung       | Ja (mehrere Interfaces)             | Nein (nur eine Klasse)              |
| Zugriffsmodifikatoren   | Methoden sind implizit `public`     | Frei wählbar                        |

- Interfaces sollte man nutzen, wenn: Mehrere Klassen dieselbe Fähigkeit teilen sollen, aber sonst nicht verwandt sind (z. B. `Comparable`, `Serializable`)
- Abstrakte Klassen sollte man nutzen, wenn:  man **Teilimplementierungen** in einer Oberklasse bereitstellen möchte, die von Unterklassen genutzt oder überschrieben werden können.


### Syntax eines Interface
```java
public interface BeispielInterface {
  // Konstante
  int KONSTANTE = 100; // automatisch public static final

  // Abstrakte Methode
  void macheEtwas(); // automatisch abstrakt

  // Default-Methode
  default void macheStandard() {
    System.out.println("Standardverhalten");
  }

  // Statische Methode
  static void hilfsMethode() {
    System.out.println("Hilfsmethode");
  }
}

class MyClass implements BeispielInterface, SecondInterface {

    // muss abstrakte-Methoden implementieren
    // hat default-methode vererbt
    // hat statische Methode nicht vererbt
    // hat zugang ohne namenspräfix auf die Konstanten von dem Interface aber vererbt die nicht.
}
```

# Java Collections Framework
**Sammlung (Collection)** ist ein allgemeiner Begriff für eine Gruppe von Objekten, die zusammen als eine Einheit behandelt werden. In Java bezeichnet eine Sammlung typischerweise eine Datenstruktur wie eine Liste, ein Set oder eine Warteschlange, die mehrere Elemente enthält.
Eine **Datenstruktur** ist eine bestimmte Art, Daten in einem Computer so zu organisieren, zu speichern und zu verwalten, dass sie effizient genutzt und verarbeitet werden können.

In Java ist **Java Collections Framework** eine Sammlung von Interfaces, Implementierungen und Algorithmen für die Arbeit mit Datenstrukturen.
- Collections Framewo enthält Interfaces wie `List`, `Set`, `Queue` und `Map`, die definieren, was grundlegende Datenstrukturen leisten können und sollen. Diese Interfaces legen einen Standard fest, den jede Implementierung erfüllen muss. 
- Collections Framewor bietet auch eine Reihe von hoch effizienten und gut getesteten Implementierungen dieser Interfaces, wie etwa `ArrayList`, `HashSet` oder `TreeSet`.
- Weiterer wichtiger Bestandteil des Frameworks ist eine Sammlung von hocheffizienten Algorithmen, etwa Sortieren oder Suchen, die auf den verschiedenen Datenstrukturen angewendet werden können. 


## ArrayList
**ArrayList** ist eine dynamische Liste, die Elemente in der Reihenfolge ihrer Einfügung speichert. Sie erlaubt Duplikate und bietet schnellen Zugriff auf Elemente per Index. 
```java
import java.util.ArrayList;
ArrayList<String> liste = new ArrayList<>();
```

### Nützliche Methoden aus `java.util.Collections` für ArrayList

Bevor man diese Methoden nutzen kann, muss man das Java Collections-Paket importieren mit `import java.util.*;`.

- **Collections.sort(List<T> list)** sortiert die Elemente der Liste in ihrer natürlichen Reihenfolge, wobei kein Rückgabewert (void) geliefert wird.  
- **Collections.reverse(List<?> list)** kehrt die Reihenfolge der Elemente in der Liste um, ebenfalls ohne Rückgabewert.  
- **Collections.shuffle(List<?> list)** mischt die Elemente der Liste zufällig durch und liefert ebenfalls keinen Rückgabewert.  
- **Collections.swap(List<?> list, int i, int j)** vertauscht die Elemente an den angegebenen Positionen `i` und `j`, wobei die Methode keinen Rückgabewert hat.  
- **Collections.max(Collection<? extends T>)** gibt das größte Element der übergebenen Collection zurück, basierend auf natürlicher Ordnung oder einem übergebenen Comparator.  
- **Collections.min(Collection<? extends T>)** gibt entsprechend das kleinste Element der Collection zurück.  
- **Collections.frequency(Collection<?> c, Object o)** zählt, wie oft das angegebene Objekt `o` in der Collection `c` vorkommt, und gibt diese Anzahl als `int` zurück.


## Set
[Video](https://www.youtube.com/watch?v=QvHBHuuddYk)

**Menge(Set)** ist eine Sammlung, die **keine Duplikate** erlaubt. Nachfolgend finden Sie drei verschiedene Implementierungen des Sets mit leicht unterschiedlichen Eigenschaften.


### HashSet
**HashSet** ist ein Set, das die Einfügereihenfolge **nicht garantiert**(die Reihenfolge von Elementen kann sich nach der Addition von neuen Elementen komplett verändern die neuen Elementen werden an eine zufällige Stelle addiert).

```java
import java.util.HashSet;
HashSet<Integer> zahlen = new HashSet<>();
```
### TreeSet
**TreeSet** ist ein Set, das die Elemente **automatisch sortiert** (aufsteigend) speichert.

```java
import java.util.TreeSet;
TreeSet<String> namen = new TreeSet<>();
```

### LinkedHashSet
**LinkedHashSet** ist wie HashSet, aber **erhält die Einfügereihenfolge**.
```java
import java.util.LinkedHashSet;
LinkedHashSet<String> tiere = new LinkedHashSet<>();
```

### Nützliche Methoden aus `java.util.Collections` für Mengen (`Set`)

Bevor man diese Methoden nutzen kann, muss man das Java Collections-Paket importieren mit `import java.util.*;`.

- **Collections.max(Collection<? extends T>)** gibt das größte Element der übergebenen Menge zurück, basierend auf natürlicher Ordnung oder einem angegebenen Comparator.  
- **Collections.min(Collection<? extends T>)** gibt entsprechend das kleinste Element in der Menge zurück.  
- **Collections.disjoint(Collection<?> c1, Collection<?> c2)** prüft, ob zwei Collections keine gemeinsamen Elemente enthalten, und gibt `true` zurück, wenn sie disjunkt sind.
- **Set.retainAll(Collection<?> c)**  Behalte nur die Elemente im Set, die auch in der angegebenen Collection enthalten sind (Schnittmenge). Rückgabewert: `true`, wenn sich das Set dadurch verändert hat.
- **Set.removeAll(Collection<?> c)**  Entfernt alle Elemente aus dem Set, die auch in der angegebenen Collection vorkommen (Differenzmenge).
- **Set.addAll(Collection<? extends E> c)**  Fügt alle Elemente aus einer anderen Collection hinzu (Vereinigungsmenge). Rückgabewert: `true`, wenn sich das Set verändert hat.


## Hilfsoperationen und Eigenschaften Vergleich
| Operation                            | ArrayList | HashSet | TreeSet | LinkedHashSet |
|-------------------------------------|-----------|---------|---------|----------------|
| `.add(E e)`                          | ✅        | ✅      | ✅      | ✅             |
| `.get(int index)`                    | ✅        | ❌      | ❌      | ❌             |
| `.contains(Object o)`                | ✅ | ✅  | ✅ | ✅      |
| `.remove(Object o)`                  | ✅        | ✅      | ✅      | ✅             |
| `.remove(int index)`                  | ✅        | ❌      | ❌      | ❌             |
|`.isEmpty()`                         | ✅        | ✅      | ✅      | ✅             |
|`.clear()`                         | ✅        | ✅      | ✅      | ✅             |
| Duplikate erlaubt                   | ✅        | ❌      | ❌      | ❌             |
| Reihenfolge erhalten                | ✅        | ❌      | ❌  | ✅         |
| automatisch Sortiert                | ❌        | ❌      | ✅      | ❌             |
| Zugriff nach Index möglich          | ✅        | ❌      | ❌      | ❌             |
| Null erlaubt                        | ✅        | ✅        | ❌     | ✅             |


- **`.add(E e)`**  Fügt ein Element zur Sammlung hinzu. Gibt `true` zurück, wenn das Element erfolgreich eingefügt wurde (bei `Set` nur wenn es nicht schon enthalten war).
- **`.get(int index)`**  Gibt das Element am angegebenen Index zurück. Nur bei Listen wie `ArrayList` verfügbar. Rückgabewert: das Element an der Position.
- **`.contains(Object o)`**   Prüft, ob ein bestimmtes Element enthalten ist. Gibt `true` zurück, wenn das Element vorhanden ist, sonst `false`.
- **`.remove(Object o)`**  Entfernt das angegebene Objekt, falls es enthalten ist. Gibt `true` zurück, wenn ein Element entfernt wurde.
- **`.remove(int index)`**  Entfernt das Element am angegebenen Index. Nur bei `ArrayList` möglich. Rückgabewert: das entfernte Element.
- **`.isEmpty()`**  Prüft, ob die Sammlung leer ist. Gibt `true` zurück, wenn keine Elemente vorhanden sind.
- **`.clear()`**  Entfernt alle Elemente aus der Sammlung. Rückgabewert: keiner (void).


### For-Each
Die `for-each`-Schleife, auch bekannt als erweiterte `for`-Schleife, wird verwendet, um durch Elemente in einem Array oder Set zu iterieren. Man braucht die `for-each`-Schleife, für Iteration durch Mengen weil, Mengen Zugang durch Index nicht erlauben.
```java
import java.util.HashSet;

HashSet<String> namen = new HashSet<>();
namen.add("Anna");
namen.add("Ben");
namen.add("Clara");

for (String name : namen) {
    System.out.println("Name ist " + name);
}
```

## Iterator
[Documentation](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Iterator.html)

**Iterator** ist ein Objekt, das verwendet wird, um **durch eine Collection** wie `List`, `Set` oder andere **iterativ durchzugehen**, ohne sich um die interne Struktur kümmern zu müssen. Ein Iterator kann auf **alle Collection-Typen** angewendet werden, die das Interface `java.util.Collection` implementieren, also z. B. `ArrayList`, `HashSet`, `LinkedHashSet`, `TreeSet`.

### Methoden eines Iterators
- **`.hasNext()`**  Gibt `true` zurück, wenn noch weitere Elemente im Iterator verfügbar sind.
- **`.next()`**  Gibt das nächste Element zurück und bewegt den Iterator einen Schritt weiter.
- **`.remove()`** entfernt das zuletzt mit .next() zurückgegebene Element aus der zugrunde liegenden Collection. Dadurch kann man während der Iteration Elemente sicher löschen, ohne eine ConcurrentModificationException zu riskieren.

### Beispiel Iterator
```java
import java.util.HashSet;
import java.util.Iterator;

HashSet<String> namen = new HashSet<>();
namen.add("Anna");
namen.add("Ben");
namen.add("Clara");

Iterator<String> it = namen.iterator();
while (it.hasNext()) {
    String name = it.next();
    System.out.println("Name ist " + name);
}
```

### Beispiel .remove()
```java
List<String> namen = new ArrayList<>(List.of("Anna", "Bob", "Clara"));
Iterator<String> it = namen.iterator();

while (it.hasNext()) {
    if (it.next().equals("Bob")) {
        it.remove(); // entfernt "Bob" aus der Liste
    }
}
System.out.println(namen); // Ausgabe: [Anna, Clara]
```


# Sortierverfahren
[Video](https://www.youtube.com/watch?v=gcRUIO-8r3U)


## Bubblesort

[info-bw.de](https://info-bw.de/faecher:informatik:oberstufe:algorithmen:sortieren:bubblesort:start)

**Bubblesort** ist ein einfacher Sortieralgorithmus, der wiederholt benachbarte Elemente einer Liste vergleicht und vertauscht, wenn sie in der falschen Reihenfolge sind. Dies geschieht so lange, bis die Liste vollständig sortiert ist.


### Verfahren
1. Vergleiche das erste und das zweite Element. Wenn das erste größer ist als das zweite, tausche sie. Fahre fort mit dem nächsten Paar: zweites und drittes Element und so weiter, bis zum Ende des Arrays. (Nach dem ersten Durchlauf ist das größte Element am Ende) 
2. Falls während dem Schritt-1 Elemente vertauscht wurden wiederhole den Schritt-1. Falls während dem Essen Durchlauf keine Elemente vertauscht wurden, dann ist die Liste sortiert, beende das Algorithmus.


### Imperlimentationsbeispiel

```java
import java.util.*;

public static ArrayList<Integer> bubbleSort(ArrayList<Integer> list) {
  boolean swapped;
  for (int i = 0; i < list.size() - 1; i++) {
      swapped = false;
      for (int j = 0; j < list.size() - i - 1; j++) {
          if (list.get(j) > list.get(j + 1)) {
              Collections.swap(list, j, j + 1);
              swapped = true;
          }
      }
      if (!swapped) {
          break;
      }
  }
  return list;
}
```



## Selectionsort

[info-bw.de](https://info-bw.de/faecher:informatik:oberstufe:algorithmen:sortieren:selectionsort:start)

**Selectionsort** ist ein Sortieralgorithmus, der das gegebene Array durch wiederholtes Finden des Minimums aus einem unsortierten Teil und das Verschieben dieses Minimums an den Anfang des unsortierten Teils sortiert.  

### Verfahren  
- Suche im gesamten (unsortierten) Array das kleinste Element.
- Tausche dieses Element mit dem ersten Element des Arrays.
- Suche im verbleibenden (unsortierten) Teil das nächste kleinste Element.
- Tausche es mit dem zweiten Element des Arrays.
- Wiederhole diesen Vorgang für alle restlichen Positionen(3,4,5,...,n) im Array, bis die Liste vollständig sortiert ist.

### Imperlimentationsbeispiel
```java
import java.util.*;

public static ArrayList<Integer> selectionSort(ArrayList<Integer> list){
  for (int i=0; i<list.size(); i++){
      int minInd = i;
      for (int j=i; j<list.size(); j++){
          if (list.get(j)<list.get(minInd)){
              minInd = j;
          }
      }
      Collections.swap(list, i, minInd);
  }
  return list;
}
```

## Insertionsort
[info-bw.de](https://info-bw.de/faecher:informatik:oberstufe:algorithmen:sortieren:insertionsort:start)

**Insertionsort** ist ein einfacher Sortieralgorithmus, der eine Liste sortiert, indem er jedes Element nacheinander an der richtigen Stelle in den bereits sortierten Teil der Liste einfügt.

### Verfahren
1. Beginne mit dem zweiten Element (aktuelle Element) der Liste. Das erste Element gilt als der bereits sortierte Teil.
2. Danach muss man das aktuelle Element an der richtigen Stelle im bereits sortierten Teil einfügen.  Dabei wird das aktuelle Element von rechts nach links mit benachbarten Elementen des sortierten Bereichs vertauscht, solange es kleiner ist als diese.
3. Nach dem Einfügen wird der Index des aktuellen Elements um eins erhöht.
4. Die Schritte zwei und drei werden so lange wiederholt, bis alle Elemente der Liste an der richtigen Stelle eingefügt sind (also solange der Index des aktuellen Elements kleiner ist als die Länge der Liste).

### Imperlimentationsbeispiel
```java
import java.util.*;
public static ArrayList<Integer> insertionSort(ArrayList<Integer> list) {
     for (int i = 1; i < list.size(); i++) {
         int j = i;
         while (j > 0 && list.get(j) < list.get(j - 1)) {
             Collections.swap(list, j, j - 1);
             j--;
         }
     }
     return list;
 }


```

## Vergleich von `==` und `equals()`
In Java vergleicht der Operator `==` bei Objekten **die Referenzen** (ob beide Variablen auf exakt dasselbe Objekt im Speicher zeigen), während die Methode `equals()`  den **objektinternen Zustand** vergleicht. Bei primitiven Datentypen (z. B. `int`, `boolean`) hingegen vergleicht `==` immer direkt die **Werte**.

```java
// Objektvergleich mit String
String a = new String("hallo");
String b = new String("hallo");

System.out.println(a == b);         // false, da unterschiedliche Objekte
System.out.println(a.equals(b));    // true, da gleiche Zeichenfolge

// Vergleich von primitiven Typen
int x = 5;
int y = 5;

System.out.println(x == y);         // true, da gleiche Werte
```
