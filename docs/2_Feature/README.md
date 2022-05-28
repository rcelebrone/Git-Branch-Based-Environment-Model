# 2_Feature

`/2_Feature`

![diagram](https://www.plantuml.com/plantuml/svg/0/NLBDJi904ButuHr6JX21NZnvGj1uqOIOU3R3TeJL_NCxYnhZmnWFFe3n2NWnPrie2RrqzvlfzpFJQSqOELa35Mt8-639SQyuqKwPL16icKDzNfOHNoShpUkqJ3L5vHrBtqHvMs8LDRgDII6LyxFnmg3Z-zkRqY1JpG8zpAKRjQCu2IBKAth5p2TNONmVR88QGJz4_qIAnmujJHu9EKLgBrfqeaFJbwuBkzGYIc2JOJrUHdHg3IkAM7b02993WnoTjvJV3IjxEDqX2Eqd_I5yz0gGfpCsQ2iYCcjRkXDu9rEGoDilq3OOolDf1NT6-yDZCcrnHS9mwTKpHMYkJO1WjCBjp_RRmqiYe3TIYH4ygErlfLTUTW397dmU4rSDuO5PxIjGUvDOUvTb5XIjveu-0kvr_wWUGTvA1W-ms4arEWbbXNS4BYDCLkm4alXEQHIsPXFPr6TUuHsPRchxmDUoYzoGQpkiitpLkidbgP3AZ_0F)

## 2 Feature
Ambiente semelhante a máquina do desenvolvedor, mesma branch usada no local, mas executa na núvem. Esse ambiente é dinamico e é gerado de acordo com o nome da branch.

### Exemplo: 
Se o nome da branch é: **feature/login-social**, o evento de criação dessa branch deve fazer deploy dessa branch em um ambiente gerado exclusivamente com base nos dados dela (ainda com mock) e a url gerada seria algo como https://{{project-name}}.{{feature-name}}.internal (e pode executar apenas dentro da VPC)