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