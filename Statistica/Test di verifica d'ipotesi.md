Dato un insieme di parametri $H$, abbiamo motivo di credere che il parametro $θ$:
- $θ∈H_0$ (l'insieme dei parametri dell'ipotesi, *ipotesi nulla*)
- $θ∉H_1=H∖H_0$ (l'insieme dei parametri dell'ipotesi alternativa).

Bisogna effettuare un test statistico: dati dei dati di un campione $X_1,...,X_n$, è una procedura per verificare se accettare $H_0$ (se i valori del campione sono compatibili) o rifiutarlo (se sono incompatibili).

Dato lo spazio campionario $Ω$, si fissa un sottoinsieme $C$ che rappresenta la *regione critica* (di rifiuto) per $H_0$, tale che $P_θ(C)$ sia piccola $∀θ∈H_0$.

Per esempio, se il parametro è la media, $C=\{|\bar{X}-θ|>d\}$, con $d$ da determinare.
## Errore di 1° specie

Consiste nel rifiutare l'ipotesi quando in realtà $θ∈H_0$.
Quando si fa un test statistico, si sceglie a priori un *livello* $α$ ($0≤α≤1$), che indica il quanto si è disposti a rischiare di avere un errore di 1° specie a causa della sfortuna con i dati del campione, e si sceglie $C$ tale che $P_θ(C)=α$.
Più piccolo è $α$ (meno si è disposti a rischiare), maggiore è l'evidenza richiesta per rifiutare $H_0$.

Dopo aver ottenuto i dati del campione, si può misurare la p-value: indica che per tutti gli $α≤p$, l'ipotesi verrà accettata.
Un p-value basso (cioè, l'ipotesi viene accettata solo se proprio non ci si può può permettere un errore di 1° specie) vuol dire che l'ipotesi è improbabile.

### Test parametro media

Se non si conosce la varianza $σ^2$, si può sostituire con $S^2=\frac{1}{n-1}∑\limits^n_{i=1}(X_i-\bar{X})^2$. Ricorda che $\frac{\sqrt{n}}{S}(\bar{X}-m)$ converge alla CDF t di Student (con $n-1$ gradi di libertà), non alla gaussiana.
#### Test bilatero

Per esempio, se il parametro è la media:
$α=P_{m_0}\{|\bar{X}-m_0|>d\}=P_{m_0}\{\frac{\sqrt{n}}{σ}|\bar{X}-m_0|>\frac{\sqrt{n}}{σ}d\}=P_{m_0}\{|z∼\mathcal{N}(0,1)|>\frac{\sqrt{n}}{σ}d\}=1-P_{m_0}\{-\frac{\sqrt{n}}{σ}d<z<\frac{\sqrt{n}}{σ}d\}=1-(Φ(\frac{\sqrt{n}}{σ}d)-Φ(-\frac{\sqrt{n}}{σ}d))=2(1-Φ(\frac{\sqrt{n}}{σ}d))$
Quindi:
- $Φ(\frac{\sqrt{n}}{σ}d)=1-\frac{α}{2}$
- $\frac{\sqrt{n}}{σ}d=q_{1-\frac{α}{2}}$
- $d=\frac{σ}{\sqrt{n}}q_{1-\frac{α}{2}}$

La formula per ottenere il p-value è semplicemente: $\bar{α}=2(1-Φ(\frac{\sqrt{n}}{σ}|\bar{X}-m_0|))$

#### Test unilatero

- $H_0: m≤m_0$
- $H_1: m>m_0$

$α=P_{m_0}\{\bar{X}-m_0>d\}=P_{m_0}\{\frac{\sqrt{n}}{σ}(\bar{X}-m_0)>\frac{\sqrt{n}}{σ}d\}=P_{m_0}\{z∼\mathcal{N}(0,1)>\frac{\sqrt{n}}{σ}d\}=1-Φ(\frac{\sqrt{n}}{σ}d)$

Quindi:
- $Φ(\frac{\sqrt{n}}{σ}d)=1-α$
- $\frac{\sqrt{n}}{σ}d=q_{1-α}$
- $d=\frac{σ}{\sqrt{n}}q_{1-α}$

La formula per ottenere il p-value è semplicemente: $\bar{α}=1-Φ(\frac{\sqrt{n}}{σ}|\bar{X}-m_0|)$

Nel caso opposto (cioè, se si vuole $H_0: m≥m_0$), si rovesciano le disuguaglianze e si rimpiazza $q_{1-α}$ con $q_α$.

### Test parametro varianza
#### Test unilatero
- $H_0: σ≤σ_0$
- $H_1: σ>σ_0$

Usiamo che $\frac{n-1}{σ_0^2}S^2∼χ^2_{n-1}$ (chi-quadrato a $n-1$ gradi di libertà).

$α=P_{σ_0}\{S^2>d\}=P_{σ_0}\{\frac{n-1}{σ_0^2}S^2>\frac{n-1}{σ_0^2}d\}=P_{σ_0}\{X∼χ_{n-1}^2>\frac{n-1}{σ_0^2}d\}=1-G_{n-1}(\frac{n-1}{σ_0^2}d)$

Quindi:
- $G_{n-1}(\frac{n-1}{σ_0^2}d)=1-α$
- $\frac{n-1}{σ_0^2}d=χ_{1-α,n-1}^2$
- $d=\frac{σ_0^2}{n-1}χ_{1-α,n-1}^2$

La formula per ottenere il p-value è semplicemente: $\bar{α}=1-G_{n-1}(\frac{n-1}{σ_0^2}s^2)$

## Errore di 2° specie

Consiste nell'accettare l'ipotesi quando in realtà $θ∈H_1$.
Si misura la probabilità di commetterlo con $β(θ)$ (da fare per ogni $θ∈H_1$).

Con la media, se la vera media è $m$, ma si pensa che è $m_0$:
$β(m)=P_m(C^c)=P_m\{\frac{\sqrt{n}}{σ}|\bar{X}-m_0|≤q_{1-\frac{a}{2}}\}=P_m\{-q_{1-\frac{a}{2}}≤\frac{\sqrt{n}}{σ}|\bar{X}-m|+\frac{\sqrt{n}}{σ}|m-m_0|≤q_{1-\frac{a}{2}}\}=P_m(C^c)P_m\{\frac{\sqrt{n}}{σ}|m-m_0|-q_{1-\frac{a}{2}}≤z≤\frac{\sqrt{n}}{σ}|m-m_0|+q_{1-\frac{a}{2}}\}=Φ(\frac{\sqrt{n}}{σ}(m-m_0)+q_{1-\frac{a}{2}})-Φ(-\frac{\sqrt{n}}{σ}(m-m_0+q_{1-\frac{a}{2}})$
Che equivale a $h(\frac{\sqrt{n}}{σ}(m-m_0))$