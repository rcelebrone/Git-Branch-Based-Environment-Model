# 1_Development

![diagram](https://www.plantuml.com/plantuml/svg/0/LP1DJWCn38Nt8yqTJ5SWbSw65Qj2GMn0gf1O8pTnEr7pH-8Kn6qG2mw0EC5S3C-K3h1px9VlFNkU6HCNPq7JZco8ZZpNrP7noXPDq3B7VDuq2Pzd6yDjMPLCIGNFefkfu1hKoQ3VsH9BipWxNLhq_71tsrXaoYojnuMeqNXAioX6TLLNO-TubT2hTWgJow6OZ1K4B_RYrRs1ST5I7mnr08Gr8PT4avE_8EDmG_BxAgWj9HYUFUqYMgEm--ZU0pmL0deXLHWXWEe-jTa4MHoAGzWd-G_L0-oNgYblESIUkwJa38-y17Wm-g8ybU1Er95a2QyCYemfUPp26b-XvC7L2RJtgwjxikCb3elSKC9-siz-UcESwxrfFvwBXLpr6m00)

## 1 Development
Máquina do desenvolvedor, tudo aqui deve ser independente de qualquer ambiente externo. Todos os critérios de aceite devem ser cobertos com testes unitários e no caso de ser uma API, é importante que ela forneça também testes de contrato.

### Ponto importante para considerar nessa etapa:
Utilizar Mock para dependencias externas. Isso é importante para evitar que alterações em serviços externos acabem invalidando os testes que estão sendo implementados nessa branch (sim, aqui já é uma branch feature, mas estamos falando da máquina local apenas).