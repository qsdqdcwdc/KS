# Generische Datentypen
[Video](https://www.youtube.com/watch?v=K1iu1kXkVoA)

**Generische Datentypen** (Generics) sind ein Konzept in der Programmierung, bei dem Klassen, Schnittstellen oder Methoden mit Platzhaltern für Datentypen definiert werden können. Diese Platzhalter (z. B. `<T>`) werden bei der Verwendung durch konkrete Typen ersetzt, sodass selbe Code mit verschiedenen Datentypen arbeiten kann ohne dabei Typsicherheit zu verlieren.

**Typsicherheit** (Type Safety):  Diese Eigenschaft einer Programmiersprache (oder einer Programm) zielt darauf ab, Fehler zu minimieren oder zu verhindern, die aus der Anwendung von Operationen auf inkompatibler Datentypen resultieren. In einer typsicheren Umgebung dürfen Operationen und Datenmanipulationen nur mit kompatiblen Datentypen durchgeführt werden.

Wieso kann man nicht einfach Methode mit Parameter von dem Datentyp `Objekt` definieren, dann könnte man es mit jedem Datentyp verwenden?
> Wenn man einen Parameter einfach vom Typ `Objekt` definiert, kann man zwar beliebige Datentypen übergeben, aber das hat Nachteile. Insbesondere verliert man dabei die Information, welcher konkrete Typ tatsächlich übergeben wurde. Das führt oft dazu, dass man auch den Rückgabewert als `Objekt` behandeln muss. Das kann später zu Problemen führen, weil nicht mehr klar ist, welche Operationen auf dem Objekt überhaupt zulässig sind.


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
  
    public void set(T t) {  
        this.t = t;  
    }  
  
    public T get() {  
        return t;  
    }  
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
```  

Verwendung der Methode:
```java  
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
```

**Verwendung:**
```java
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
Man kann auch Schranken an wirecards anwenden: `<? extends Animal>`

