### Entity
 - Jede Entity hat eine eindeutige ID
 - Anhand der ID können Objekte unterschieden werden
 - Zustand kann sich über die Zeit ändern
  
### Value Object
- Ist ein unveränderliches Werte Objekt
- Besitzt keine ID
- Beschreibt häufig eine Entity

### Transaktion
- Steuern die Modifikation von Aggregates
- Stellt sicher das Aggregates immer in einem vollständigen und gütligen Zustand sind


### Wie schneidet man ein Aggregate?
1. Innerhalb von Aggregate-Grenzen gilt es die Fachlichkeit zu schützen <br/>
![Rule_1](image/td/rule_1.png "Rule_1")
Am Ende einer bestimmten Transaktion muss die ganz bestimmte Fachlichkeit erfüllt sein.<br/><br/>

2. Die Aggregates sollten möglichst klein sein<br/>
![Rule_2](image/td/rule_2_1.png "Rule_2")
Das Problem daran ist, das die Liste an Sprint- oder ProduktBacklogItem-Objekte sehr groß werden kann. Die Folge der Speicherverbrauch und der Transaktionsumfang können zu groß werden.
Besser wäre es für jedes Objekt ein Aggregate einzuführen, z.B. Sprint-Aggregate welches als Root den Sprint selbst inne hat. Kleinere Aggregates lassen sich auch leichter ändern bzw. testen.<br/><br/>

1. Referenz der Aggregates nur über die Id<br/>
![Rule_3](image/td/rule_3.png "Rule_3")
Dies soll dabei helfen, die Aggregates klein zu halten und mehrere Aggregates in der gleichen Transaktion zu verändern. Ein weiterer Vorteil ist, dass einfache und schnelle speichern der Aggregates.<br/><br/>

1. Anwendung von Eventual Consistency
Wie wird der Status in einem anderen Aggregate aktualisiert, bzw. wie bekommt er die Statusänderung in einem anderen Aggregate mit?<br/><br/>
![Rule_4](image/td/rule_4.png "Rule_4")
Ein Domänen-Event wird erzeugt und publiziert, in diesem Fall das "BackgroundItemCommitted". Der Empfänger "Sprint Aggregate" startet daraufhin eine Transaktion und aktualisiert den Zustand des Sprints. Vergleich zu Context Mapping im Strategischen Design.

### Aggregates modellieren
!!! Anemic Domain Model verhindern !!!
Dies geschieht hauptsächlich dann, wenn die Geschäfts- oder Fachlogik nicht innerhalb des Aggregates implementiert wird. 
1. Klasse für das Aggregate Root erstellen
2. Jede Aggregate Root Entity muss eine eindeutige Id besitzen (Dabei sollte die Id ein als Value Object modelliert werden, da immutable)
3. Anlegen aller wesentlichen Attribute oder Felder
4. Einfaches Verhalten hinzufügen
5. Komplexes Verhalten hinzufügen


#### Die richtige Größe finden
1. Regel 2 anwenden und kleine Aggregates bilden. Nur die Attribute und Felder mit aufnehmen, die am stärksten mit der Root Entity verknüpft sind.
2. Regel 1 schützen der Fachlichkeit innerhalb der Aggregate Grenze. Für jedes erstellte Aggregate, Konsistenzregeln aufstellen (Zeitrahmen für reaktionsbasierte Updates)
3. Die Fachexperten müssen vorgeben, wie viel Zeit für jedes Update vergehen darf
4. Falls Entities einen Rattenschwanz an Änderungen mit sich ziehen, dann können auch Aggregates zusammengeführt werden
5. Allen anderen Aggregates mit der Regel 4 behandeln

