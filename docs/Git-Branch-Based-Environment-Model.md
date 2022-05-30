# Git-Branch-Based-Environment-Model

* [Overview](#Overview)
  * [1_Development](#1_Development)
  * [2_Feature](#2_Feature)
  * [3_Staging](#3_Staging)
  * [4_Production](#4_Production)

---

## Overview

![diagram](https://www.plantuml.com/plantuml/svg/0/VLHTQrj747qt-3zCHHyagW_Qf2-5G9nOj0672Dakb13CwExuQjEzEpVx8Ti9_J6X3w5_eQ_wOvtPUsrP8erU9Eryx3bppkppc32at3ZW3OMDfPlZe--ihrms1EkKslZBR1RmPbhRjCwh72bKx1FvDAsucRKElLPFOZBEhcOldquMUdJv-cpMO4mKvEZgfLRSfcahcST7nqU_lJgTNvrVp9VpDnT_BER3aHw-uEmDXhkXumhT60QlyKEs7i4m68haD-msP3WCHl3f-0Zaiw0GsGyDRSXnIq6A5XGZutu13dQ13vaW1LoXMoDuXiZNwGO3JGUZhkVvdQ1kjASK5IXhZaaxdBJELhZzilsR8R11w856QkI-bhmXNra4OKh1unYkyIFagEYXuUfFlU6lFQQLusoqSxEoCb42OUlpXfeTnHxEDM6In3RmUwhIn6D3KptBWRe_rfTBtU1nkoQxP2UhWBvQGqq1PPG8hGXkTQgU6zBlqZKn_D2V87GbKxWWiOSlLVrjW48KunZG2eT3YcFmEftqVnCHIy3xxUTkV4fs-szXkySrflgGgg2ehQ_LSjDL61oEh7GPWqGBDv7My1Z2zf-Yc8AJRYONwGIvPsyR-r6Ifl0xEcjwKILFMt18SgUNWGo5mIJnHBv6KWUsQHrfg2zGAjTiOLEQ6268jTXDJHQeuIY3qFK2ragiaeuSi4T-mBeDvf3rjzbAQgBQAebN3xZqtubej7DgIpL2jSODYMYgIA3j5vRVEURjvs059Oc5_LgaCJjqSbXX25giMr8UYVPGgDMjO7kxhvJOPSMtFVPt2lujjvLbyUOxMD9N584iagaSOaqEWAxEFaAqUeU04acndt0NRCHGFXLeuhDTduVzEiExgxFxvIfBMXwO4sFctPWki1uExb4DxeDBSlk1CNplhAVpTES8di4fnZMPCpaPZagD55mj7xy-tQDnsT7HlffnsKdRnNuSmQ-oX_s25MvzNlVYz7l-Kv_MvhYVrCMx3NdI9osMZrC4KGbtVdhwzPpJ3bCduC-Z1rrAZj2MTOlFzYRqNAmZh_T_)

## 1 Development
Máquina do desenvolvedor, tudo aqui deve ser independente de qualquer ambiente externo. Todos os critérios de aceite devem ser cobertos com testes unitários e no caso de ser uma API, é importante que ela forneça também testes de contrato.

### Ponto importante para considerar nessa etapa:
Utilizar Mock para dependencias externas. Isso é importante para evitar que alterações em serviços externos acabem invalidando os testes que estão sendo implementados nessa branch (sim, aqui já é uma branch feature, mas estamos falando da máquina local apenas).

## 2 Feature
Ambiente semelhante a máquina do desenvolvedor, mesma branch usada no local, mas executa na núvem. Esse ambiente é dinamico e é gerado de acordo com o nome da branch.

### Exemplo: 
Se o nome da branch é: **feature/login-social**, o evento de criação dessa branch deve fazer deploy dessa branch em um ambiente gerado exclusivamente com base nos dados dela (ainda com mock) e a url gerada seria algo como https://{{project-name}}.{{feature-name}}.internal (e pode executar apenas dentro da VPC)

## 3 Staging
Esse ambiente é um ambiente consolidade, replica de produção (com menor volume de dados, claro) e anonimizado. Esse ambiente para o desenvolvedor deve ser considerado produção, se der erro aqui então o time precisa discutir pra avaliar o motivo de não ter sido possível pegar o problema na etapa anterior. Aqui é apenas para fazer um teste end-to-end e na sequência promover pra produção. A url é algo como: *https://{{project-name}}.staging.com.br*

### Aqui vale uma observação
Se a empresa faz muitos deploys durante o dia, esse ambiente pode ser coordenado por um time de qualidade para garantir que estamos executando testes e liberando o ambiente frequentemente (automatizar end-to-end é muito importante para garantir velocidade nos testes desse ambiente).

## 4 Production
O que dizer? Aqui o desenvolvedor não deve saber qual endereços dos bancos, usuários, senhas, nomes de recursos. Nada, absolutamente nada. Passar no end-to-end em Staging deve ser o necessário para garantir que produção vai se comportar da forma correta. Se algo não der certo nessa etapa é provavel que o ambiente de staging não esteja atualizado com produção ou que algo não previsto também entrou para o ambiente de staging no momento do end-to-end. A url aqui é do endereço de produção do projeto: *https://{{project-name}}.com.br*

## 1_Development

`/1_Development`

[Overview](#Git-Branch-Based-Environment-Model)

![diagram](https://www.plantuml.com/plantuml/svg/0/LP1DJWCn38Nt8yqTJ5SWbSw65Qj2GMn0gf1O8pTnEr7pH-8Kn6qG2mw0EC5S3C-K3h1px9VlFNkU6HCNPq7JZco8ZZpNrP7noXPDq3B7VDuq2Pzd6yDjMPLCIGNFefkfu1hKoQ3VsH9BipWxNLhq_71tsrXaoYojnuMeqNXAioX6TLLNO-TubT2hTWgJow6OZ1K4B_RYrRs1ST5I7mnr08Gr8PT4avE_8EDmG_BxAgWj9HYUFUqYMgEm--ZU0pmL0deXLHWXWEe-jTa4MHoAGzWd-G_L0-oNgYblESIUkwJa38-y17Wm-g8ybU1Er95a2QyCYemfUPp26b-XvC7L2RJtgwjxikCb3elSKC9-siz-UcESwxrfFvwBXLpr6m00)

## 1 Development
Máquina do desenvolvedor, tudo aqui deve ser independente de qualquer ambiente externo. Todos os critérios de aceite devem ser cobertos com testes unitários e no caso de ser uma API, é importante que ela forneça também testes de contrato.

### Ponto importante para considerar nessa etapa:
Utilizar Mock para dependencias externas. Isso é importante para evitar que alterações em serviços externos acabem invalidando os testes que estão sendo implementados nessa branch (sim, aqui já é uma branch feature, mas estamos falando da máquina local apenas).

## 2_Feature

`/2_Feature`

[Overview](#Git-Branch-Based-Environment-Model)

![diagram](https://www.plantuml.com/plantuml/svg/0/NLBDJi904ButuHr6JX21NZnvGj1uqOIOU3R3TeJL_NCxYnhZmnWFFe3n2NWnPrie2RrqzvlfzpFJQSqOELa35Mt8-639SQyuqKwPL16icKDzNfOHNoShpUkqJ3L5vHrBtqHvMs8LDRgDII6LyxFnmg3Z-zkRqY1JpG8zpAKRjQCu2IBKAth5p2TNONmVR88QGJz4_qIAnmujJHu9EKLgBrfqeaFJbwuBkzGYIc2JOJrUHdHg3IkAM7b02993WnoTjvJV3IjxEDqX2Eqd_I5yz0gGfpCsQ2iYCcjRkXDu9rEGoDilq3OOolDf1NT6-yDZCcrnHS9mwTKpHMYkJO1WjCBjp_RRmqiYe3TIYH4ygErlfLTUTW397dmU4rSDuO5PxIjGUvDOUvTb5XIjveu-0kvr_wWUGTvA1W-ms4arEWbbXNS4BYDCLkm4alXEQHIsPXFPr6TUuHsPRchxmDUoYzoGQpkiitpLkidbgP3AZ_0F)

## 2 Feature
Ambiente semelhante a máquina do desenvolvedor, mesma branch usada no local, mas executa na núvem. Esse ambiente é dinamico e é gerado de acordo com o nome da branch.

### Exemplo: 
Se o nome da branch é: **feature/login-social**, o evento de criação dessa branch deve fazer deploy dessa branch em um ambiente gerado exclusivamente com base nos dados dela (ainda com mock) e a url gerada seria algo como https://{{project-name}}.{{feature-name}}.internal (e pode executar apenas dentro da VPC)

## 3_Staging

`/3_Staging`

[Overview](#Git-Branch-Based-Environment-Model)

![diagram](https://www.plantuml.com/plantuml/svg/0/PPA_Rjmm3CRt0-uTM4ztm9szTEgK9Ycw940Ge7F1anYV4ebKPSdf7_HXYWv5vsvT_MAbV9TBqNgnJ58VV_peio5ZoYLui3IIbnY8ytBnmh7nnHBiSux3gwvB-DZsBk_BhWoKZ73MkjP8wD0cXppw4ajtyN9xuv7pk-khpcEc8Mle_OLMesDARTH6oyLoSIw5BQPFgp6Q3JGnoJsPl6KCr2fGxxYlskqkDPf-7NPEkn4m0a-_HmeRq6nKSEVtQ6K3QVePlJEeKu2gsJBzcBvh75dO1VTPYverV5akG9yJpsgNaCrUMvpFX-Pq0c5LqacdR-12z5HjKH50k2FC9L6p_bVC1Un95Ix5F522-NF6dybc8FXG2EWZcP8H1CpqoxfUAdG920UQ_uNjBFYiR9uoC8WlsGdNDZUKWbEJHlHElPqTafInaWkiYEqsorPVQxNbhw4EOFSww9suussBMjDBmWgSACW0TPcgAlKc6bLaDUEuc8hyjUxrblp9qoSxtbB2Mb1pnzXfe3S7AshwJCdqx_W3)

## 3 Staging
Esse ambiente é um ambiente consolidade, replica de produção (com menor volume de dados, claro) e anonimizado. Esse ambiente para o desenvolvedor deve ser considerado produção, se der erro aqui então o time precisa discutir pra avaliar o motivo de não ter sido possível pegar o problema na etapa anterior. Aqui é apenas para fazer um teste end-to-end e na sequência promover pra produção. A url é algo como: *https://{{project-name}}.staging.com.br*

### Aqui vale uma observação
Se a empresa faz muitos deploys durante o dia, esse ambiente pode ser coordenado por um time de qualidade para garantir que estamos executando testes e liberando o ambiente frequentemente (automatizar end-to-end é muito importante para garantir velocidade nos testes desse ambiente).

## 4_Production

`/4_Production`

[Overview](#Git-Branch-Based-Environment-Model)

![diagram](https://www.plantuml.com/plantuml/svg/0/PLBDJXmn3BwljEzWvWJIidFXn8doervQ2I5nHjwCcKb9ujH91b3LXq4SU83UUfqNgxFB3bMRasCxtu-TivHHSl4EEXh9SVGKyd9nO8DnfICOSexfj6q57zUzpKFPb4HYE6JjMnlsBNPYCOoknD9Ud1nVEmpvzkkNrc6cb3LrTw7TQ0F9EYhHSh5Sd7C97ShpuHZD2fee_8rCFWxegMAkDz9e-fFVM6KX20XX-ZsINu6sPkfjnyqH_5WkGCyCVxWH36RGb-VRe9aZuA1ULFZq0jP7HzKbTWm8zuIv23L7_u9PZpqfmYMR1nBONhUgehC6fxVfbU5x8Q0dCYKZC9ZfLsTxrab2yGWxDVy3Trl03sIphq1YLxBbK6ckIRpDCxoeLFoBELAFGGsO0KTAAo0rA3IziSObbUb5B2UediE02QhL_JG938gylmyCknyGgz2VTJatvEP9xeVmcGHhGwszvsORLpk5jNocCdJ5Vm00)

## 4 Production
O que dizer? Aqui o desenvolvedor não deve saber qual endereços dos bancos, usuários, senhas, nomes de recursos. Nada, absolutamente nada. Passar no end-to-end em Staging deve ser o necessário para garantir que produção vai se comportar da forma correta. Se algo não der certo nessa etapa é provavel que o ambiente de staging não esteja atualizado com produção ou que algo não previsto também entrou para o ambiente de staging no momento do end-to-end. A url aqui é do endereço de produção do projeto: *https://{{project-name}}.com.br*