# 3_Staging

![diagram](https://www.plantuml.com/plantuml/svg/0/PPA_Rjmm3CRt0-uTM4ztm9szTEgK9Ycw940Ge7F1anYV4ebKPSdf7_HXYWv5vsvT_MAbV9TBqNgnJ58VV_peio5ZoYLui3IIbnY8ytBnmh7nnHBiSux3gwvB-DZsBk_BhWoKZ73MkjP8wD0cXppw4ajtyN9xuv7pk-khpcEc8Mle_OLMesDARTH6oyLoSIw5BQPFgp6Q3JGnoJsPl6KCr2fGxxYlskqkDPf-7NPEkn4m0a-_HmeRq6nKSEVtQ6K3QVePlJEeKu2gsJBzcBvh75dO1VTPYverV5akG9yJpsgNaCrUMvpFX-Pq0c5LqacdR-12z5HjKH50k2FC9L6p_bVC1Un95Ix5F522-NF6dybc8FXG2EWZcP8H1CpqoxfUAdG920UQ_uNjBFYiR9uoC8WlsGdNDZUKWbEJHlHElPqTafInaWkiYEqsorPVQxNbhw4EOFSww9suussBMjDBmWgSACW0TPcgAlKc6bLaDUEuc8hyjUxrblp9qoSxtbB2Mb1pnzXfe3S7AshwJCdqx_W3)

## 3 Staging
Esse ambiente é um ambiente consolidade, replica de produção (com menor volume de dados, claro) e anonimizado. Esse ambiente para o desenvolvedor deve ser considerado produção, se der erro aqui então o time precisa discutir pra avaliar o motivo de não ter sido possível pegar o problema na etapa anterior. Aqui é apenas para fazer um teste end-to-end e na sequência promover pra produção. A url é algo como: *https://{{project-name}}.staging.com.br*

### Aqui vale uma observação
Se a empresa faz muitos deploys durante o dia, esse ambiente pode ser coordenado por um time de qualidade para garantir que estamos executando testes e liberando o ambiente frequentemente (automatizar end-to-end é muito importante para garantir velocidade nos testes desse ambiente).