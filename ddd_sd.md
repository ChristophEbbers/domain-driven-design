# Strategisches Design
Beim Strategischen Design werden die "groben" Grundlagen geschaffen, für die spätere Detailarbeit. Es sollen die Haupt-Domänen und Sub-Domänen herausgearbeitet werden, die wichtig für das Unternehmen sind und voneinander abgegrenzt werden.

## Strategisches Design Schritt für Schritt
1. Bounded Context herausarbeiten
2. Eine Ubiquitous Language entwerfen
3. Einbinden von Domänen-Experten und Entwicklern
4. Domänen schneiden in Core- und Sub-Domänen
5. Integration und Beziehungen mehrerer Bounded Contexts


## Definitionen
![Strategisches Design](image/sd/bd.png "Bounded Context")

* Bounded Context
  * Soll Domänen-Modelle voneinander abgrenzen
  * Innerhalb eines Bounded Context existiert ein Modell mit einer entwickelten Semantik
  * Domänen-Experten und Entwickler sprechen innerhalb des Context die gleiche Sprache
  
* Ubiquitous Language
  * Jeder im Team versteht den Begriff, präzise und mit allen Bedingungen
  * Begriff und Sprache sind allgegenwärtig und wird auf das Modell übertragen
  * Nicht mehrere Teams sollten an einem Bounded Context arbeiten

* Haupt-Domäne
  * Ist das Herzstück des Unternehmens
  * Soll das Unternehmen einen Wettbewerbsvorteil gegenüber Konkurrenten bieten
  * Fokus auf die Haupt-Domäne legen, man kann nicht in allen Bereichen gut sein 


## Wozu benötigt man einen Bounded Context?
* Worauf legt das Team den Fokus?
* Bündeln der Konzepte, welche im Kern der Unternehmensstrategie liegen
* Weitere Vorteil kleinere Modelle lassen sich einfacher testen
* Soll den "Big Ball of Mudd" verhindern, da man sich immer wieder hinterfrägt, ob es zum Kontext passt