## LDS process:

### topic plate
> for all topics $k \in [1,K]$
    sample mixture components $\phi_k \sim Dir(\beta)$

### document plate
> for all documents $m \in [1,M]$,
    sample mixture proportion $\theta_m \sim Dir(\alpha)$
    sample document length $N_m \sim \Poisson()$

> for all words $n \in [1,N_m]$ in documents m do
    sample topic index $z_{m,n} \sim Multi(\theta_m)$
    sample term for word $w_{m,n} \sim Multi(\phi_{m,n})$ 
