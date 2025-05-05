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










