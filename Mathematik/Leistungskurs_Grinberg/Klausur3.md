# Analytische Geometrie
**Analytische Geometrie:** Ein Teilgebiet der Mathematik, der algebraische Methoden nutzt, um geometrische Eigenschaften und Beziehungen in einem Koordinatensystem zu beschreiben. Analytische Geometrie ermöglicht die Lösung geometrischer Probleme durch algebraische Methoden.

## Punkte
- **2D-Punkt:** Ein Objekt in der Ebene, das durch ein geordnetes Paar von Zahlen $(x| y)$ dargestellt wird. Hierbei repräsentiert $x$ die horizontale Position und $y$ die vertikale Position im zweidimensionalen Raum. 
- **3D-Punkt:** Ein Objekt im Raum, das durch ein geordnetes Tripel von Zahlen $(x| y| z)$ charakterisiert wird. $x$, $y$ und $z$ repräsentieren die Positionen entlang der x-, y- und z-Achsen im dreidimensionalen Raum.

## Lineare Gleichungen
Eine **lineare Gleichung** ist eine algebraische Gleichung, dessen beide Seiten nur aus einer Summe aus Konstanten oder Variablen(im ersten Potenz multipliziert durch konstanten) besteht. 

**Beispiel:** `ax + by + c = 0`, wobei `a`, `b`, und `c` konstante Werte sind und `x` und `y` Variablen.


## Lineare Gleichungssysteme
Ein **lineares Gleichungssystem** besteht aus zwei oder mehr linearen Gleichungen, die gemeinsame Variablen haben.

**Beispiel:**
```
2x - y = 5
 x + y = 7
```

## Lineare Kombination (optionaler Abschnitt)
**Lineare Kombination:** Eine Summe von Produkten, bei der jeder Term das Produkt einer Konstante mit einem anderem Objekt(einer Funktion, einem Vektor, einer Variablen, ...) ist. Alle Objekte in einer Linearkombination müssen von einem und dem gleichen Typ sein, d.h. eine Linearkombination eines Vektors ist nur mit einem Vektor möglich. Eine Linearkombination einer Funktion ist nur mit einer Funktion möglich.

**Beispiel:**
- **Funktionen:** Eine lineare Kombination von Funktionen ist eine Summe der Form $a_1 f_1(x) + a_2 f_2(x) + \dots + a_n f_n(x)$, wobei $a_i$ Skalare und $f_i(x)$ Funktionen sind.
- **Vektoren:** Eine lineare Kombination von Vektoren in einem Vektorraum ist eine Summe der Form $a_1 \mathbf{v}_1 + a_2 \mathbf{v}_2 + \dots + a_n \mathbf{v}_n$, wobei $a_i$ Skalare und $\mathbf{v}_i$ Vektoren sind.

Nehmen wir an, wir haben eine Menge von Vektoren, z.B. $\{\mathbf{v}, \mathbf{w}, \mathbf{u}\}$. Nehmen wir auch an, wir haben einen weiteren Vektor $\mathbf{p}$. Wir sagen, $\mathbf{p}$ ist eine lineare Kombination der Vektoren $\mathbf{v}$, $\mathbf{w}$, $\mathbf{u}$, wenn es Konstanten $a$, $b$, $c$ gibt, sodass $a\mathbf{v} + b\mathbf{w} + c\mathbf{u} = \mathbf{p}$. Mit anderen Worten, wir sagen, dass ein Vektor $\mathbf{p}$ eine lineare Kombination der Vektoren $\mathbf{v}$, $\mathbf{w}$, $\mathbf{u}$ ist, wenn wir den Vektor $\mathbf{p}$ durch eine lineare Kombination der Vektoren $\mathbf{v}$, $\mathbf{w}$, $\mathbf{u}$ ausdrücken können. Auf die gleiche Weise können wir über Funktionen und unabhängige Variablen sprechen:

- Nehmen wir an, wir haben die unabhängigen Variablen $x$, $y$, und $z$. Ein Beispiel für eine lineare Kombination dieser Variablen könnte folgender Ausdruck sein: $3x - 2y + 5z$
- Nehmen wir an, wir haben die Funktionen $f(x) = x^2$, $g(x) = \sin(x)$ und $h(x) = e^x$. Eine lineare Kombination dieser Funktionen könnte wie folgt aussehen: $2f(x) + 3g(x) - 4h(x) = 2x^2 + 3\sin(x) - 4e^x$

Wenn wir Gruppen von Objekten haben, wobei kein Objekt eine lineare Kombination anderer Objekte aus derselben Gruppe ist, dann nennen wir diese Objekte **linear unabhängig zu zueinander**. 

## Lösen eines linearen Gleichungssystems
Beim Lösen eines linearen Gleichungssystems besteht das Ziel darin, die Werte für die Variablen zu finden, die alle Gleichungen des Systems gleichzeitig erfüllen. Am häufigsten wird zur Lösung linearer Gleichungssysteme das Substitutionsverfahren oder das Gauß-Verfahren verwendet. Substitutionsmethode passt für Gleichungssysteme mit zwei Variablen und Gauss-Verfahren für größere Systeme mit mehr Variablen.

### Substitutionsmethode
**Substitutionsmethode:** Ein algebraisches Verfahren zur Lösung linearen Gleichungssystems, indem der Wert einer Variablen aus einer Gleichung in andere Gleichungen eingesetzt wird. Dies vereinfacht das Gleichungssystem zu einer einzelnen Gleichung mit einer Variablen, die dann gelöst werden kann. Schritte der Substitutionsmethode:

1. **Isolieren einer Variablen:** Wähle eine der Gleichungen und löse sie nach einer Variablen auf.
3. **Einsetzen:** Ersetze die isolierte Variable in alle andere Gleichungen (Dies eliminiert die erste Gleichung aus dem System).
4. Wiederholen Sie die Schritte 1 und 2, bis entweder nur noch eine Gleichung übrig ist oder die verbleibenden Gleichungen keine Variablen mehr gemeinsam haben.
   - Wenn der Substitutionsprozess zu einer nicht wahren Gleichung (`1=0`, `3=-4`) führte, dann hat dieses Gleichungssystem keine Lösungen.
   - Wenn im Substitution Prozess eine der Gleichungen zu einer Ware Gleichung ohne Variablen kürzt (`1=1`, `0=0`), dann entfernen Sie diese Gleichung aus dem System, sie ist redundant.
5. **Lösen der neuen Gleichung:**
   - Wenn Sie nur noch eine Gleichung mit einer Variablen haben, lösen Sie diese. Auf diese Weise erhalten Sie den Wert einer der Variablen. Suchen Sie dann in den vorherigen Schritten die Gleichung, die die Variable enthält, deren Wert Sie gerade gelernt haben, und eine weitere Variable, ersetzen Sie den Wert und lösen Sie diese. Wiederholen Sie den letzten Schritt, bis Sie die Werte aller Variablen gefunden haben.
   - Wenn Sie eine Gleichung mit mehreren Variablen übrig haben, sind alle Werte der Variablen, die diese Gleichung erfüllen, Lösungen des Systems.

[weitere Informationen zu Substitutionsmethode](https://en.wikipedia.org/wiki/System_of_linear_equations#Elimination_of_variables)
### Gaußsches Eliminationsverfahren
Die **Additions- oder Eliminationsmethode** reduziert das System auf eine einzige Variable, indem die Gleichungen so addiert oder subtrahiert werden, dass eine Variable eliminiert wird. [detaillierte Beschreibung des Algorithmus](https://en.wikipedia.org/wiki/Gaussian_elimination)



