## Deterministische endliche Automaten (DEA)

(DFA eng. für (deterministic finite Automata))

Ein nicht formales Beispiel:

Ein Aufzug mit zwei Stockwerken

mögliche Eingaben:

1. im Aufzug möchte jemand nach oben
2. oben wartet jemand
3. im Aufzug möchte jemand nach unten
4. unten wartet jemand

Wir unterscheiden zwei Zustände:

	"oben":der Aufzug ist oben

	"unten":der Aufzug ist unten

![[Im3.png]]

Ein eindeutiger Automat hat Zustände und Übergänge. 

#### Definition 1.3.3

Ein (deterministischer) endlicher Automat A ist ein 5-Tupel

$A=(Q,\Sigma,\delta,q_0,F)$

wobei:

1) $Q$ ist eine endliche nicht leere Menge $:=$ Zustandsmenge
2) $\Sigma$ ist eine endliche nicht leere Menge an Zeichen des Alphabets
3) $\delta$ ist eine Funktion: $\delta:=Q\times\Sigma\Rightarrow Q$ mit der Voraussetzung $Q\cap\Sigma=\emptyset$ 
4) $q_0\in Q$ ist der Start Zustand von A
5) $F\subseteq Q$ ist die Menge von FInalzuständen von A

#### <u>Beispiel 1</u>: 
Wir wählen $\sum=\{0,1\}$ 

Wir legen fest: $w=_{df}~0110\in\Sigma^*$ 

Wir konstuieren einen endlichen Automaten $A_1$, der dieses "$w$" erkennt.

Darstellung als Graph:

1) Knoten:Zustände
2) Kanten:sind gerichtet und markiert gemäß $\delta$ 

![[Im4.png]]


Dabei ist also:

$Q=\{q_0,q_1,q_2,q_3,q_4,q_5\}$ 

$\Sigma=\{0,1\}$ 

$\delta...$ gemäß des Graphen

$q_0,F=\{q_4\}$

- Die Überfürhungsfunktion $\delta$ ist total definiert.
- Der Automat akzeptiert ein Eingabewert $w$ $\leftrightarrow$ ein Finalzustand erreicht wird

An unserem Beiseispiel: Die einzige Eingabe, die $A_1$ akzeptiert ist $w=0110$ 

Die von $A_1$ akzeptierte Sprache ist $L(A_1)=\{0110\}~\square$    

#### <u>Beispiel 2</u>:

Dasselbe Alphabet $\Sigma=\{0,1\}$

Wir konstuieren einen endlichen Automaten $A_2$, der unendlich viele Wörter der Form $w=0110u$ für $u\in\{0,1\}^*$ erkennt, also alle Wörter über $\{0,1\}$, für die $0110$ Präfix ist.

$A_2$ ist eine Modifikation von $A_1$ mit $L(A_2)=\{0110u|u\in\{0,1\}^*\}$

Ein endlicher Automat $A=(Q,\Sigma,\delta,q_0,F)$ 

###### Frage: "Wieso können 5-Tupel rechnen?" 

Dazu geben wir eine formale Definition der Berechnung eines Automaten A bei Eingabe $w$.

###### Definition 1.3.4 

Gegeben sei ein (deterministischer) endlicher Automat $A=(Q,\Sigma,\delta,q_0,F)$  und eine Eingabe $w\in\Sigma^*$.

Eine Konfiguration K von A bei Eingabe w ist ein Paar $K=(p,a)$, wobei $p\in Q$ (aktueller Zustand von $A$) und $u\in\Sigma^*$ (der noch zu lesende "Rest" der Eingabe $w$) 

Damit ist eine Konfiguration eine vollständige Beschreibung einer Momentansituation von $A$ bei Eingabe $w$.

Erläuterung am Beispiel $A_1$ mit 0110

Start:    $K_0(q_0, 0110)$  
		$\vdash K_1(q_1, 011)$ 
		$\vdash K_2(q_2, 01)$ 
		$\vdash K_3(q_3, 0)$ 
		$\vdash K_4(q_4, \lambda)$ 

##### Definition 1.3.5 

Wieder sei $A=(Q,\Sigma,\delta,q_0,F)$ ein endlicher Automat und $w\in\Sigma^*$ eine Eingabe. Wir definieren eine binäre Relation $\vdash$ über der Menge der Konfurationen.

$\vdash\subseteq(Q\times\Sigma^*)\times(Q\times\Sigma^*)$ auf folgende Weise:

Es gilt $K\vdash K'$ für zwei Konfigurationen $K$ und $K'$ mit $K=(p,a)$ und $K=(q,v)$ $\leftrightarrow_{df}\underset{x\in\Sigma}{V}(u=xa~und~\delta(p,x)=q)$. $K'$ heißt unmittelbaree Nachfolge Konfiguration von $K$. Der Übergang von $K$ zu $K'$ entspricht einem Berechnungschnitt von $A$ mit $w$ und erfolgt gemäß $\delta$, $\vdash$ heißt Übergangsrelation

