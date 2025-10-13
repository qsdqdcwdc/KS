# Logikgatter

Inf-Schule.de: [Grundgatter](https://schuljahr.inf-schule.de/2019-20/rechner/digitaltechnik/gatter)

<p align="center"><img src="Img/Gatter.png" width="1000"  title="Abb1:Gatter"></p>

### Mnemoniken für die Schaltplan Symbole:
| Gatter        | Symbol                    | Mnemonik                                                      |
|---------------|---------------------------|---------------------------------------------------------------|
| UND-Gatter    | &                         | & = Und                                                       |
| ODER-Gatter   | ≥1                        | ist wahr wenn eins oder mehr Inputs wahr sind.                |
| NICHT-Gatter  | 1 mit einem Kreis draußen | hat einen Input, einen Output, eine 1 drinnen und einen Kreis draußen. |
| XOR-Gatter    | =1                        | ist wahr wenn die Summe der Inputs gleich eins ist.           |


### Priorität der logischen Operationen

`NICHT (¬)` vor `UND (∧)`

`UND (∧)` vor `ODER (∨)` / `XOR (⊕)`


# Manipulation von logischen Ausdruken 

### Disjunktive Normalform
Die disjunktive Normalform (DNF) beschreibt einen besonderen Weg, logische Aussagen aufzuschreiben. Eine Formel der Aussagenlogik ist in disjunktiver Normalform, wenn sie eine Disjunktion (Kette aus einem oder mehreren Termen, verbunden mit ODER-Verknüpfungen; z. B. `T₁ ∨ T₂ ∨ T₃`) von Konjunktionstermen ist, wobei jeder Konjunktionsterm eine **Konjunktion** (Kette aus Verknüpfungen mit UND: Z.b:`A ∧ B ∧ C`) aus **Aussagenvariablen** bildet, die jeweils entweder unnegiert oder negiert auftreten können (`A` bzw. `¬A`).

Beispiel für die disjunktive Normalform: `(¬A ∧ B ∧ C) ∨ (A ∧ ¬C) ∨ (B)`

Beispiele für die Aussagen **nicht** in disjunktiver Normalform:
| Aussage | Warum nicht DNF? |
|----------|------------------|
| `¬(A ∧ B) ∨ C` | Die Negation steht nicht direkt vor Variablen, sondern vor einer Konjunktion. | 
| `A ∨ (B ∧ (C ∨ D))` | Innerhalb eines Konjunktionsterms steckt noch eine Disjunktion. Die Form ist nicht rein „Disjunktion von Konjunktionstermen“. |
| `(A ∨ B) ∧ (C ∨ D)` | Die oberste Verknüpfung ist eine Konjunktion. | 


Eine **kanonische disjunktive Normalform (KDNF)** beschreibt eine disjunktive Normalform, die in jedem seinem Konjunktionsterm alle in dieser Aussage vorhandene Aussagenvariable enthaltet (Praktisch eine Aussage mit nicht gekürzten Termen). Jede logische Aussage kann eindeutig in einer kanonischen disjunktiven normal Form ausgedruckt werden. 

Beispiel für die kanonische disjunktive Normalform: `(¬A ∧ B ∧ ¬C) ∨ (A ∧ B ∧ C) ∨ (¬A ∧ ¬B ∧ C) ∨ (¬A ∧ ¬B ∧ ¬C)` (In diesem Fall beinhaltet die Aussage gesamt drei Aussagevariablen `A`, `B` und `C`. Und jeder der vier vorhandenen Konjunktionsterme beinhaltet alle Aussagevariablen.)

Für einen Algorithmus, wie man aus Wahrheitstabellen kanonische disjunktive Normalform bildet, sehe erste 5 Minuten von diesem Video: [Conjunctive Normal Form (CNF) and Disjunctive Normal Form (DNF)
](https://www.youtube.com/watch?v=2cgHa02s_SA).

Wieso heißt das Zeug Normalform? - Sie heißt **Normalform**, weil sie eine standardisierte, normierte Darstellungsweise für logische Formeln ist.

### Konjunktive Normalform
Als **konjunktive Normalform (KNF)** wird in der Aussagenlogik eine bestimmte Form von Formeln bezeichnet. Es handelt sich um eine Reihe an geklammerten) Oder-Termen auch gennant Disjunktionstermen, die nur aus eventuell negierten Aussagenvariablen bestehen, und diese Oder-Terme/Disjunktionstermen sind wiederum mit Und-Verknüpfungen verbunden.

Beispiel für die konjunktive Normalform:  `(A ∨ ¬B ∨ C) ∧ (¬A ∨ B) ∧ (B ∨ ¬C)`

Die **kanonische konjunktive Normalform (KKNF)** ist eine spezielle Form der KNF, in der jeder Disjunktionsterm alle in der Formel vorkommenden Aussagenvariablen enthält. KKNF ist für jede aussagenlogische Formel eindeutig bestimmbar.

Beispiel für die kanonische konjunktive Normalform:  
`(A ∨ B ∨ C) ∧ (A ∨ ¬B ∨ C) ∧ (¬A ∨ B ∨ ¬C) ∧ (¬A ∨ ¬B ∨ C)`

Für einen Algorithmus, wie man aus Wahrheitstabellen kanonische Konjunktive Normalform bildet, sehe dieses Video ab 5 Minuten: [Conjunctive Normal Form (CNF) and Disjunctive Normal Form (DNF)](https://youtu.be/2cgHa02s_SA?si=z6zOmUrgBpog9pTQ&t=298)
