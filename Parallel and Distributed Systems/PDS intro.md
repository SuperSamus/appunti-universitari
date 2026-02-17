```mermaid
flowchart LR
a((Internet)) --> Frontend --> Switch
Switch --> M1
Switch --> M2
Switch --> M3
subgraph Homogeneous
  M1
  M2
  M3
  b[...]
end
Switch --> GPU
```
