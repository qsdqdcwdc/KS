# Analytische Geometrie
**Analytische Geometrie:** Ein Teilgebiet der Mathematik, der algebraische Methoden nutzt, um geometrische Eigenschaften und Beziehungen in einem Koordinatensystem zu beschreiben. Analytische Geometrie ermöglicht die Lösung geometrischer Probleme durch algebraische Methoden.

## Punkte
- **2D-Punkt:** Ein Objekt in der Ebene, das durch ein geordnetes Paar von Zahlen $(x| y)$ dargestellt wird. Hierbei repräsentiert $x$ die horizontale Position und $y$ die vertikale Position im zweidimensionalen Raum. 
- **3D-Punkt:** Ein Objekt im Raum, das durch ein geordnetes Tripel von Zahlen $(x| y| z)$ charakterisiert wird. $x$, $y$ und $z$ repräsentieren die Positionen entlang der x-, y- und z-Achsen im dreidimensionalen Raum.
- Die Menge der Punkte kann wie folgt angegeben werden: $L = \\{(t \mid t - 5) \mid t \in \mathbb{R} \text{  beliebig} \\}$
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
## Gaußsches Eliminationsverfahren
Das **Gaußsche Eliminationsverfahren**, ist Verfahren zur Lösung linearer Gleichungssysteme. Es transformiert das System in eine obere Dreiecksform, von der aus die Lösungen leicht durch Rückwärtseinsetzen gefunden werden können.

#### Schritte des Gaußschen Eliminationsverfahrens
1. **Auswahl des führenden Elements**: Wähle das erste Element der ersten Spalte, das nicht null ist, als führendes Element.
2. **Zeilenanpassung**: Tausche nötigenfalls die Zeilen, sodass das führende Element in der aktuellen Zeile an der ersten Position steht.
3. **Elimination**: Nutze das führende Element, um alle Einträge unterhalb dessen auf null zu setzen. Subtrahiere dazu ein Vielfaches der führenden Zeile von den darunterliegenden Zeilen, sodass die Elemente unterhalb null werden.
4. **Wiederholung für die nächste Spalte**: Wiederhole die Schritte 1 bis 3 für die nächste Spalte und Zeile, bis das gesamte System auf eine obere Dreiecksform reduziert ist.
5. **Rückwärtseinsetzen**: Beginne bei der letzten Gleichung und löse sie nach der letzten Variablen auf. Setze diesen Wert in die vorherige Gleichung ein, um die nächste Variable zu finden, und fahre so fort, bis alle Variablen bestimmt sind.

 [detaillierte Beschreibung des Algorithmus](https://en.wikipedia.org/wiki/Gaussian_elimination)

## Polynomfunktion n-ten Grades
**Polynomfunktion n-ten Grades**: Eine Polynomfunktion n-ten Grades ist eine Funktion der Form $P(x) = a_nx^n + a_{n-1}x^{n-1} + \ldots + a_1x + a_0$, wobei $a_n, a_{n-1}, \ldots, a_1, a_0$ Koeffizienten sind und $a_n \neq 0$. 


## Polynominterpolation
Ein Polynom vom Grad $n$ kann durch $n+1$ beliebige Punkte $(x_1, y_1), (x_2, y_2), \ldots, (x_{n+1}, y_{n+1})$ eindeutig bestimmt werden, vorausgesetzt, dass keine zwei dieser Punkte dieselben $x$-Koordinaten haben (dass keine zwei Punkte übereinander liegen). [Video](https://www.youtube.com/watch?v=z1YUTRG3ngM)

### Schritte
1. **Aufstellen des Gleichungssystems**: Für jeden Punkt wird eine Gleichung der Form $a_nx_i^n + a_{n-1}x_i^{n-1} + \ldots + a_1x_i + a_0 = y_i$ erstellt.
2. **Lösen des Gleichungssystems**: Das resultierende lineare Gleichungssystem aus n+1 Gleichungen für die n+1 Unbekannten (die Koeffizienten $a_0, a_1, \ldots, a_n$) wird gelöst.

Die gleiche Methode kann auch verwendet werden, um ein Polynom n-ten Grades zu finden, das durch mehr als n + 1 Punkte verläuft. In diesem Fall funktioniert sie jedoch nicht für jeden Satz von Punkten.

Auch, wenn wir eine Polynomfunktion finden wollen, die nicht nur durch eine Reihe von Punkten verläuft, sondern an den Punkten auch bestimmte Eigenschaften aufweist, d. h. beispielsweise an einem der Punkte $(x_p| y_p)$ ein lokales Maximum hat. In diesem Fall erstellen wir auch ein System linearer Gleichungen, wobei wir die Gleichungen jetzt auf der Grundlage der Eigenschaften zusammenstellen, die die Funktion an diesen Punkten haben muss. Beispielsweise wissen wir für einen lokalen Maximumpunkt, dass die Funktion eine Ableitung gleich 0 haben muss und auch durch diesen Punkt verläuft. Das heißt, wir erhalten zwei Gleichungen: $f(x_p)=y_p$ und $f'(x_p)=0$ 


### Beispiel
Betrachten wir die Punkte $(1| 2), (2| 3), (3| 5)$. Ein Polynom 2-ten Grades soll durch diese Punkte bestimmt werden:
$P(x) = ax^2 + bx + c$

#### Aufstellen des Gleichungssystems
Setzen Sie die gegebenen Punkte in das Polynom ein:
``` math
\begin{align*}
a(1)^2 + b(1) + c &= 2 \\
a(2)^2 + b(2) + c &= 3 \\
a(3)^2 + b(3) + c &= 5
\end{align*}
```
Das ergibt das System:
```math
\begin{align*}
1a + 1b + 1c &= 2 \\
4a + 2b + 1c &= 3 \\
9a + 3b + 1c &= 5
\end{align*}
```
#### Lösen des Gleichungssystems
Dieses System kann nun mit Gaußsches Eliminationsverfahren gelöst werden. Nach Lösung erhält man die Koeffizienten $a$, $b$, und $c$, die das gesuchte Polynom definieren $a = 0.5$, $b = -0.5$, und $c = 2$, sodass das resultierende Polynom lautet: $P(x) = 0.5x^2 - 0.5x + 2$ Dieses Polynom verläuft durch alle drei gegebenen Punkte, was durch Einsetzen der $x$-Werte in $P(x)$ überprüft werden kann.


## Kartesisches Koordinatensystem
In einem dreidimensionalen kartesischen Koordinatensystem wird jedes Punkt durch drei Zahlenwerte beschrieben. Komplexere Objekte können durch Gleichungen dargestellt werden, deren Lösungsmengen alle Punkte umfassen, die zu diesen Objekten gehören. In einem zweidimensionalen Koordinatensystem können Sie alle Längen und Winkel direkt von der Zeichnung auf Papier messen und sie werden korrekt sein. Ein Blatt Papier kann den dreidimensionalen Raum jedoch nicht vollständig abbilden. Wenn dreidimensionale Objekte auf Papier gezeichnet werden, sind sie daher nicht geeignet, um Länge, Winkel und die meisten anderen Eigenschaften von diesen Objekte zu messen. Dafür ist die analytische Geometrie erforderlich.

<p align="center">
	<img src="Img/kl3_1.png" width="300"  title="Abb1">
	<br>
	<em>2d Kartesisches Koordinatensystem</em>
</p>
<p align="center">
	<img src="Img/kl3_2.png" width="300"  title="Abb1">
	<br>
	<em>3d Kartesisches Koordinatensystem</em>
</p>


## Vectoren




