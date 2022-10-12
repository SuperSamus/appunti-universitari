# Automi

Riconosce `aba` (alfabeto $\{a,b,c\}$) in `abcabbaba`

- Automa di Mealy
	- $z=f_z(s,x)$
	- $s'=f_s(s,x)$
- Automa di Moore
	- $z=f_z(s)$
	- $s'=f_s(s,x)$

## Mealy

```mermaid
flowchart LR
s1 -- b/0 --> s1
s1 -- c/0 --> s1
s1(((s1))) -- a/0 --> s2((s2)) -- c/0 --> s1
s2 -- a/0 --> s2
s2 -- b/0 --> s3((s3))
s3 -- a/1 --> s1
s3 -- b/0 --> s1
s3 -- c/0 --> s1
```

## Moore
