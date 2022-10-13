# Esercizi inferenza [[OCaml#^8e19a5|tipo]]

$ite(true,λx.x+5,λy.y+2)$

$$
\cfrac{\cfrac{}{∅⊢true:bool} \quad \cfrac{\cfrac{x:num⊢x:num \quad \cfrac{}{x:num⊢5:num}}{x:num⊢x+5:num}}{∅⊢λx.x+5:num→num} \quad ∅⊢λy.y+2:num→num}{∅⊢ite(true,λx.x+5,λy.y+2):num→num}
$$
 ---

$ite(true,λx.x+5,2)$ Errore

$$
\cfrac{\cfrac{}{∅⊢true:bool} \quad \cfrac{\cfrac{x:num⊢x:num \quad \cfrac{}{x:num⊢5:num}}{x:num⊢x+5:num}}{∅⊢λx.x+5:num→num} \quad \cfrac{\text{X}}{∅⊢2:num→num}}{∅⊢ite(true,λx.x+5,2):num→num}
$$

---

$λx.xx$

$$
\cfrac{\cfrac{x:t_1⊢x:U→τ_2 \quad \cfrac{}{x:_1⊢x:U}}{x:τ_1⊢xx:τ_2}}{∅⊢λx.xx:τ_1→τ_2}
$$

Ci vorrebbe un tipo dove $U=U→τ_2