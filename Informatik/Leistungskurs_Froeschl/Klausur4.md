# Generische Datentypen
[Video](https://www.youtube.com/watch?v=K1iu1kXkVoA)

**Typsicherheit** (Type Safety):  Diese Eigenschaft einer Programmiersprache (oder einer Programm) zielt darauf ab, Fehler zu minimieren oder zu verhindern, die aus der Anwendung von Operationen auf inkompatibler Datentypen resultieren. In einer typsicheren Umgebung dürfen Operationen und Datenmanipulationen nur mit kompatiblen Datentypen durchgeführt werden.

**Generische Datentypen** (Generics) sind ein Konzept in der Programmierung, bei dem Klassen, Schnittstellen oder Methoden mit Platzhaltern für Datentypen definiert werden können. Diese Platzhalter (z. B. `<T>`) werden bei der Verwendung durch konkrete Typen ersetzt, sodass selbe Code mit verschiedenen Datentypen arbeiten kann ohne dabei Typsicherheit zu verlieren.

Wieso kann man nicht einfach Methode mit Parameter von dem Datentyp `Objekt` definieren, dann könnte man es mit jedem Datentyp verwenden?
> Wenn wir ein Objekt als Eingabetyp verwenden, müssen wir oft auch den Ausgabetyp als Objekt definieren. Das kann in Zukunft zu vielen Problemen führen, da wir dadurch Informationen darüber verlieren, welcher Datentyp tatsächlich in diesem Parameter gespeichert ist. Infolgedessen können wir später nicht mehr sagen, welche Operationen mit diesem Objekt kompatibel sind.


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
Box<Integer> integerBox = new Box<>();  // Den Typ muss man zweites Mal nicht wiederholen Box<>()
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
   
### Beispiel  
```java  
Utility.print("Hello");  
Utility.print(10);  
Utility.print(3.14);  
```  
