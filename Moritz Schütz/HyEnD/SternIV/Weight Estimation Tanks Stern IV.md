#Struktur #SternIV #CLT 

Das Gewicht der Tanks wird Volumenabhängig berechnet. Dazu werden die folgenden Erleichterungen angenommen:
- Da die Tanks aus zwei Isotensoiden Enden und einer zylindrischen Mitte bestehen ist es möglich die Tanks als eine Kugel und eine Röhre zu approximieren.
- Das Gewicht des Liners ist vernachlässigbar, bzw. mit einem simplen Sicherheitsfaktor $S_{Liner}$ abbildbar.
- Die Endcaps sind als kleinere Kugel aus Aluminium modellierbar.
- Da unsere Rakete ca. $D = 180mm$ dick wird, ist hier davon ausgegangen.
- Ethanol Druck am Triebwerk ca. $80 - 100 bar$. Mit dem Arbiträren Sicherheitsfaktor $S_{Druck} = 1.5$ muss unser Tank einen Druck von ca.  $150 bar$ aushalten.
- Alle Alu Teile sind $2mm$ dick, was genug ist um sie zu schweißen

![[Tank_Loadcase.png]] Die Spannung $\sigma_{1}$ ("Hoop Spannung") beträgt $\sigma_{1} = \frac{(p_{innen} - p_{aussen}) r}{t}$ wobei t die Wandstärke ist. Die Spannung $\sigma_2$ beträgt genau $\sigma_2 = 2 \cdot \sigma_1$. 

>[!Warning]
>Jetzt wird es wirklich hässlich. Das ist wirklich eine extreme Vereinfachung.

Die maximale Spannung ist also circa die Hypothenuse eines Dreiecks mit den Seitenlängen $2 \cdot \sigma_1$ und $\sigma_1$, also gleich $\sqrt{5} \cdot \sigma_1$. Als Yield Strength des fast Uni-direktionales CFK der Wickelmaschine werden hier $1500 MPa$  angenommen. Weil das einfach eine räudige Vereinfachung ist wird hier der Sicherheitsfaktor $S_{Müll} = 1.5$ aufgeschlagen.
$1500 MPa = \sqrt{5} \cdot \sigma_1$ , was unter Vernachlässigung des Außendrucks zu $t = S_{Müll} \cdot \frac{\sqrt{5} \cdot r \cdot p_{innen}}{\sigma_{yield}}$ führt. Unsere Werte eingesetzt ergibt das ca. $5mm$ Wandstärke.
Phillip hatte aber mit einem sinnvollen Laminatrechner ca. 3.5mm Wandstärke berechnet.
![[Tankgewicht.jpg]]Diese Rechnung führt zu der Formel: $M_{Tank} = 132.1 \cdot V_{Tank} \frac{kg}{m^3} + 0.71 kg$. 
Diese Formel gilt nur für linerlose Tanks.
