# Logikgatter

Inf-Schule.de: [Grundgatter](https://schuljahr.inf-schule.de/2019-20/rechner/digitaltechnik/gatter)

<p align="center"><img src="Img/Gatter.png" width="1000"  title="Abb1:Gatter"></p>


### Mnemoniken für die Schaltplan Symbole:
| Gatter        | Symbol/Schreibweise       | Mnemonik                                      |
|---------------|---------------------------|---------------------------------------------------------------|
| UND-Gatter    | &                         | & = Und                                                       |
| ODER-Gatter   | ≥1                        | ist wahr wenn eins oder mehr Inputs wahr sind.                |
| NICHT-Gatter  | 1 mit einem Kreis draußen | hat einen Input ein Output und ein Kreis draußen.             |
| XOR-Gatter    | =1                        | ist wahr wenn die Summe der Inputs gleich eins ist.           |


# Konjunktive Normalform
Als **konjunktive Normalform (KNF)** wird in der Aussagenlogik eine bestimmte Form von Formeln bezeichnet. Vereinfacht gesagt handelt es sich um eine Reihe an (geklammerten) Oder-Termen, die nur aus eventuell negierten Variablen bestehen, und diese Oder-Terme sind wiederum mit Und-Verknüpfungen verbunden.

Beilspiel:
```
(A ∨ ¬B ∨ ¬C) ∧ (A ∨ B ∨ ¬C) ∧ (¬A ∨ B ∨ C)
```


