# Modello matematico di Drouant

Per calcolare consumo energetico, emissione e riciclabilità di un sistema ICT.

## Consumo energetico

1. Consumo energetico
   $E=E_i+E_u+E_f$
	- $E_i$ (iniziale) è l'energia per la progettazione $E_p$, la manifattura $E_m$ e il trasporto $E_{t_i}$
	- $E_u$ è l'energia per l'uso del sistema ICT ($P_u(t)$: potenza nel tempo)
	- $E_f$ è l'energia per trasporto, smantellamento e dismissione (riciclo, riuso, etc.)

$E=(E_p+E_m+E_{t_i})+\int_{t=0}^{t=\text{fine vita}} P_u(t)dt+(E_{t_f}+E_r)$

$P∪E=\cfrac{P_{it}+P_{\max it}}{P_{it}}=$

$E_u=\int_{t=0}^{t=\text{fine vita}}dt≃P∪E∑\limits_{i∈S}ε_ih_i\;[kWh]$
- $ε_i$ potenza componente $i$-esimo
- $h_i$ ore di uso attese del componente $i$-esimo nel periodo