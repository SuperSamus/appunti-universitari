# Automi

Riconosce `aba` (alfabeto $\{a,b,c\}$) in `abcabbaba`

- Automa di Mealy
	- $z=f_z(s,x)$
	- $s'=f_s(s,x)$
- Automa di Moore
	- $z=f_z(s)$
	- $s'=f_s(s,x)$

Entrambi gli automi hanno bisogno di un registro per memorizzare lo stato.

## Mealy

```mermaid
flowchart LR
s1 -- b/0 --> s1
s1 -- c/0 --> s1
s1(((s1))) -- a/0 --> s2((s2)) -- c/0 --> s1
s2 -- a/0 --> s2
s2 -- b/0 --> s3((s3))
s3 -- a/1 --> s1
s3 -- b,c/0 --> s1
```

## Moore

```mermaid
flowchart LR
s1 -- b --> s1
s1 -- c --> s1
s1(((s1/0))) -- a --> s2((s2/0)) -- c --> s1
s2 -- a --> s2
s2 -- b --> s3((s3/0))
s3 -- b,c --> s1
s3 -- a --> s4((s4/1)) -- a --> s2
s4 -- b,c --> s1
```
