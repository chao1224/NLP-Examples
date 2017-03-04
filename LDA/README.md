## Algorithm

使用LDA进行文本生成的过程：

写M篇文章，一共涉及了K个主题，每一个topic下的词部分为一个$\beta$的Dirichlet先验分布中sample出来的Multinomial分布。

对于每一篇文章，会从一个泊松分布中sample一个长度作为文章的长度，再从一个参数为$\alpha$的Dirichlet先验分布中sample出一个Multinomial分布作为该文章在每一个topic下词的概率。

当想写某一篇文章中的第n个词的时候，首先从该文章中出现每一个Topic的Multinomial分布中sample一个Topic，然后再在这个Topic对应当词的Multinomial分布中sample一个词，作为要填写的词。

```
# Topic plate
for all topics $k \in [1,K]$:
    sample mixture components $\phi_k \sim Dir(\beta)$
# Document plate
for all documents $m \in [1,M]$:
    sample mixture proportion $\theta_m \sim Dir(\alpha)$
    sample document length $N_m \sim Poiss(\zeta)$
    # Word plate
    for all words in $n \in [1,N_m]$ in document m do:
        sample topic index $z_{m,n} \sim Mult(\theta_m)$
        sample term for word $w_{m,n} \sim Multi(\phi_{m,n})$
```

公式推导的博客链接: [CSDN博客](http://blog.csdn.net/miss_snow_m/article/details/60459166)
