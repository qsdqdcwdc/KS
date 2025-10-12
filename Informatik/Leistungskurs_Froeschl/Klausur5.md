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

### Konjunktive Normalform
Als **konjunktive Normalform (KNF)** wird in der Aussagenlogik eine bestimmte Form von Formeln bezeichnet. Vereinfacht gesagt handelt es sich um eine Reihe an (geklammerten) Oder-Termen, die nur aus eventuell negierten Variablen bestehen, und diese Oder-Terme sind wiederum mit Und-Verknüpfungen verbunden.

Beilspiel:
```
(A ∨ ¬B ∨ ¬C) ∧ (A ∨ B ∨ ¬C) ∧ (¬A ∨ B ∨ C)
```


