# Comandos Git para iniciantes

Segue abaixo a lista de comandos git e a ordem necessária para executar determinadas ações.

## Novo repositório local

- `git init` - cria novo repositório local.
- `git config --list` - lista as configurações ativas do Git. Pode ser usado para verificar as credenciais (user name e e-mail) usadas no repositório ou na máquina, por exemplo. As configurações podem vir em 3 níveis diferentes:
    - **local**: vale só para um repositório específico
    - **global**: vale para o usuário do computador
    - **system**: vale para todos os usuários do sistema

### Caso as credenciais setadas do usuário sejam diferentes do desenvolvedor

Se as credenciais forem apenas no repositório:
- `git config --unset user.name` - retira as credenciais do nome de usuário do repositório
- `git config --unset user.email` - retira as credenciais do e-mail do usuário do repositório

Se as credenciais forem globais:
- `git config --global --unset user.name` - retira as credenciais do nome de usuário de todos os repositórios
- `git config --global --unset user.email` - retira as credenciais do e-mail do usuário de todos os repositórios

### Caso as credenciais não estejam setadas

- `git config user.name "Nome do Usuário"` - seta o nome do usuário no repositório; ou `git config --global user.name "Nome do Usuário"` - seta o nome do usuário em todos os repositórios
- `git config user.email "email@servidor.com"` - seta o e-mail do usuário no repositório; ou `git config --global user.email "email@servidor.com"` - seta o e-mail do usuário em todos os repositórios

### Quando as credenciais estiverem setadas

- `git add <nome-do-arquivo>` - envia para o *stage* o arquivo que deseja fazer o *commit*; ou `git add .` - envia todos os arquivos alterados para o *stage*
- `git commit -m "Mensagem do commit"` - cria um novo *commit* no repositório local, ou seja, uma nova versão do seu projeto, e um ponto seguro de onde você pode prosseguir com o seu projeto

> [!TIP]
> Para facilitar, caso tenha dúvidas sobre qual ordem executar os comandos, faça a seguinte ordem:<br>
> `git init`<br>
> `git config --global --unset user.name`<br>
> `git config --global --unset user.email`<br>
> `git config user.name "Seu Nome de Usuário do GitHub"`<br>
> `git config user.email "seu_email_do_github@servidor.com"`<br>
> `git add .`<br>
> `git commit -m "Mensagem do seu commit"`<br>

## Passando o repositório local para o remoto (GitHub)

> [!IMPORTANT]
> A partir desse ponto, há a necessidade de uma conta no **GitHub**, e de um repositório criado lá, pois a seguir iremos vincular o repositório local ao repositório remoto do GitHub.

- Crie uma conta no **GitHub**, caso já não tenha
- Crie um repositório novo no **GitHub** (botão verde ***New*** no canto superior da tela)

> [!WARNING]
> Ao criar um repositório no GitHub, você pode definir como ***public*** ou ***private***. Se quiser criar um repositório para fins de portifólio, defina-o o como ***public***. Caso estej desenvolvendo um projeto comercial, defina-o como ***private***.

- Após criar o repositório remoto no GitHub, volte para o repositório local e execute os comandos a seguir no terminal do diretório do repositório
- `git remote add origin <endereco-do-repositorio-remoto>` - vincula o seu repositório local ao repositório remoto
- `git branch -M main` - cria uma branch principal ao seu repositório para o envio ao GitHub
- `git push -u origin main` - efetua o ***push***, ou seja, envia seu repositório local para a *branch* principal do seu repositório remoto

Após isso, o seu repositório está atualizado e ***commitado***.

> [!NOTE]
> Este procedimento visa evitar que você perca seu projeto por qualquer motivo, seja porque a máquina foi formatada, seja porque você fez alterações no seu código-fonte que não devia, seja porque alguém apagou o seu projeto da máquina. Caso isso aconteça, é possível retornar seu projeto para o último estado em que se encontrava quando foi feito o último *commit*.

> [!IMPORTANT]
> Este procedimento serve para criar o repositório local e remoto, e deve ser feito somente da primeira vez. Caso queira atualizar um repositório já existente, o procedimento é outro. Continue com a leitura para saber como atualizar tanto o repositório local quanto o remoto.

## Como atualizar o repositório remoto

> [!NOTE]
> Este procedimento deve ser executado toda vez que o usuário realizar alguma alteração no seu projeto, desde que deseje que tal alteração permaneça no seu projeto.