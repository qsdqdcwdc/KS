# Generische Datentypen
[Video](https://www.youtube.com/watch?v=K1iu1kXkVoA)

**Typsicherheit** (Type Safety):  Diese Eigenschaft einer Programmiersprache (oder einer Programm) zielt darauf ab, Fehler zu minimieren oder zu verhindern, die aus der Anwendung von Operationen auf inkompatibler Datentypen resultieren. In einer typsicheren Umgebung dürfen Operationen und Datenmanipulationen nur mit kompatiblen Datentypen durchgeführt werden.

**Generische Datentypen** (Generics) sind ein Konzept in der Programmierung, bei dem Klassen, Schnittstellen oder Methoden mit Platzhaltern für Datentypen definiert werden können. Diese Platzhalter (z. B. `<T>`) werden bei der Verwendung durch konkrete Typen ersetzt, sodass selbe Code mit verschiedenen Datentypen arbeiten kann ohne dabei Typsicherheit zu verlieren.


Wieso kann man nicht einfach Methode mit Parameter von dem Datentyp `Objekt` definieren, dann könnte man es mit jedem Datentyp verwenden?
> Wenn wir ein Objekt als Eingabetyp verwenden, müssen wir oft auch den Ausgabetyp als Objekt definieren. Das kann in Zukunft zu vielen Problemen führen, da wir dadurch Informationen darüber verlieren, welcher Datentyp tatsächlich in diesem Parameter gespeichert ist. Infolgedessen können wir später nicht mehr sagen, welche Operationen mit diesem Objekt kompatibel sind.



