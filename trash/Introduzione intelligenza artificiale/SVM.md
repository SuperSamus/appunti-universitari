"Estensione" del [[perceptron]], cercando di massimizzare i margini (invece che di trovare semplicemente l'iperpiano).

### Margine

https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote09.html

Dato l'iperpiano $H=\{x:w^Tx+b=0\}$
Sii $d$ il vettore più piccolo che va da un punto all'iperpiano. La proiezione verso l'iperpiano è:
$x^P=x-d$
$d$ è parallelo a $w$, quindi esiste $α∈ℝ$ tale che $d=αw$
Dato che $x^P∈H$, quindi $w^Tx^P+b=0$.
Quindi $w^Tx^P+b=w^T(x-d)+b=w^T(x-αw)+b=0$
$α=\frac{w^Tx+b}{w^Tw}$

#### Trova il margine massimo

La lunghezza di $d$:
$∥d∥_2=\sqrt{d^Td}=\sqrt{α^2w^Tw}=α\sqrt{w^Tw}=\frac{w^Tx+b}{w^Tw}\sqrt{w^Tw}=\frac{w^Tx+b}{\sqrt{w^Tw}}=\frac{w^Tx+b}{∥w∥_2}$

Il margine dell'iperpiano è quindi definito da $γ(w,b)=\min_{x∈D}\frac{∣w^Tx+b∣}{∥w∥_2}$

Quindi:
Funzione obiettivo: $\max_{w,b}γ(w,b)=\max_{w,b}\frac{1}{∥w∥_2}\min_{x∈D}∣w^Tx+b∣$
Vincolo: $y_i(w^Tx_i+b)≥0$

Dato che l'iperpiano (e quindi il margine) non dipende dalla scala (cioè $γ(βw,βb)=γ(w,b),∀β≠0$), si può impostare una scala tale che $\min_{x∈D}∣w^Tx+b∣=1$

Quindi:
Funzione obiettivo: $\max_{w,b}γ(w,b)=\max_{w,b}\frac{1}{∥w∥_2}=\min_{w,b}∥w∥_2$
Vincoli:
- $y_i(w^Tx_i+b)≥0 \quad ∀i$
- $\min_i∣w^Tx_i+b∣=1$

Vincolo che combina entrambi: $y_i(w^Tx_i+b)≥1 \quad ∀i$

Abbiamo ottenuto un *problema di ottimizzazione quadratico*.

#### Margine debole

È possibile che il rumore faccia sì che l'iperpiano sia posizionato influenzato da un singolo punto anomalo, o che l'iperpiano non possa esistere proprio.

Si può rimuovere il vincolo, modificando la funzione obiettivo.
Scegliendo una penalità $C$:
Funzione obiettivo: $\min_{w,b}∥w∥_2+C∑ξ_i$
Dove $ξ_i=\max(1-y_i(w^Tx_i+b),0)$
