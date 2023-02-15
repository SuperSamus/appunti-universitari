# Modello matematico di Drouant

Per calcolare consumo energetico, emissione e riciclabilità di un sistema ICT.

## Consumo energetico

$E=E_i+E_u+E_f$
- $E_i$ (iniziale) è l'energia per la progettazione $E_p$, la manifattura $E_m$ e il trasporto $E_{t_i}$
- $E_u$ è l'energia per l'uso del sistema ICT ($P_u(t)$: potenza nel tempo)
- $E_f$ è l'energia per trasporto, smantellamento e dismissione (riciclo, riuso, etc.)

$E=(E_p+E_m+E_{t_i})+\int_{t=0}^{t=\text{fine vita}} P_u(t)dt+(E_{t_f}+E_r)$

$P∪E=\cfrac{P_\text{IT}+P_{\text{non IT}}}{P_\text{IT}}=1+\cfrac{P_{¬\text{IT}}}{P_\text{IT}}$
- Non IT: non legata al calcolo (es. raffreddamento)

$E_u=\int_{t=0}^{t=\text{fine vita}}dt≃P∪E∑\limits_{i∈S}ε_ih_i\;[kWh]$
- $ε_i$ potenza componente $i$-esimo
- $h_i$ ore di uso attese del componente $i$-esimo nel periodo

Esempio: switch in una rete LAN
- $P_u=0+σ∑\min\limits_{i∈\text{porta}}\{1,δω_i\}$
- Stato idle + potenza di 1 porta al 100% * somma di uso della porta $i$-esima
- δ: ≃18, aumento potenza dovuto al traffico (gain) 

## Emissioni di $CO_2$

$C=C_i+C_u+C_f$

$C=(α_pE_p+α_mE_m+a_{t_i}E_{t_i})+αu\int_{t=0}^{t=\text{fine vita}} P_u(t)dt+(α_{t_f}E_{t_f}+α_rE_r)$

Ipotesi: facciamo finta che vada tutto a corrente elettrica:
- $C=\cfrac{α_i}{τ_i}C_i+α_uC_u+α_fC_f$