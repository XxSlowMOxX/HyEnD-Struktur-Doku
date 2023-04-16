#CFK #Struktur #HyEnD 

Diese Dokumentation ist aus einer Erklär Session mit Phillip entstanden, bei der ich versucht habe mir alles zu merken, aber an der Wirrheit wird man merken das das nicht zwingend funktioniert hat.

## Warum Fasern?

Materialien sind nicht perfekt, man hat immer Defekte. Deswegen kann man die theoretisch durch die Chemie vorhergesagten Kennwerte nie erreichen, da die Defekte failen, bevor der Rest vom Werkstück failt. Die Grundidee eines Faserverbundwerkstoffes ist, das wir auf einen gegebenen Querschnitt immer eine gewisse menge an Defekten haben. Wenn man aber einen großen blob hat und da irgendwo ein Riss entsteht dann ist halt der ganze blob im Arsch. Bei Fasern reißt Vllt eine Faser, aber die anderen können die Last übernehmen. Deswegen sind Fasern auch besser je dünner die einzelnen Haare sind.

## Warum das Harz?

Leider können die Fasern nur Kräfte in die Zug-Richtung entlang der Faser aufnehmen, das heißt sie sind sehr anisotrop. Um Lasten in andere Richtungen, Schubspannungen aufzunehmen und die Formstabilität des Bauteils zu gewährleisten wird eine sogenannte "Matrix" benutzt, also halt getrocknetes Harz um die Fasern herum, die die miteinander verklebt und so.

## Wie verhält sich die Harz Faser Kombi?

Die Fasern sind sehr steif (dehnen sich also kaum unter Belastung aus), und reißen erst unter sehr hoher Last. Das harz ist nicht so steif, und reißt schon unter substantiell geringerer Last. Die Steifigkeit und festigkeit der Kombination werden größtenteils von der Faser bestimmt, sind aber ganz leicht schlechter als eine reine Faser, da sowas ja im Prinzip in Relation zum Querschnitt angegeben wird, und man halt nicht mehr zu 100% aus Fasern besteht. Sobald die Fasern in der Kombination reißen, reißt auch das Harz weil dieses sehr viel weniger fest ist.

# Klassische Laminats Theorie
#CLT

Der ungefähre Ablauf der Auslegung mit CLT ist wie folgt:
1. Die Materialkennwerte wie $E$ (E-Modul, also Steifigkeit), $G$ (Schehrmodul, also elastizität in scher Richtung) und $\gamma$ (Poisson-Ratio, also wie sehr sich das zusammenzeiht wenn man dran zieht) für jedes individuelle Laminat werden bestimmt, wenn immer das gleiche Laminat benutzt wird dann muss man das nicht machen.
2. Mit den Materialkennwerten kann man die unrotierte Steifigkeitsmatrix $Q$ bestimmen, die dann die Steifigkeit einer einzelnen Lage des Laminats in alle Richtungen angibt.
3. Da die Lagen in echt aber in verschiedene Richtungen zeigen muss man die Steifigkeitsmatrix für jede Lage rotieren um die rotierte Steifigkeitsmatrix $\bar{Q}$ zu erhalten.
4. Damit werden dann die $A, B, D$ Matrizen für das Gesamtlaminat berechnet, Was die einzelnen Matrizen aussagen kann man im Rocketscience Paper nachlesen, oder in dem NASA Artikel in der Nextcloud unter Stern IV/Literatur. Diese Matrizen assembled man dann zu $\begin{pmatrix} A & B \\ B & D \end{pmatrix}$ . und hat damit die gesamtsteifigkeitsmatrix des Laminats. Wenn das Laminat symmetrisch ist, also die Lagen entlang der Mitte gespiegelt ist reicht es manchmal nur mit dem A Teil zu rechnen, aber darauf gehe ich Vllt später ein.
6. Die Äußeren Belastungen $F_{Außen}, M_{Außen}$ werden bestimmt.