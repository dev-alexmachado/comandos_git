# Comandos Git para iniciantes

Segue abaixo a lista de comandos git e a ordem necessária para executar determinadas ações.

## Sumário

1. [Novo repositório local](#novo-repositório-local)
1.1 [Caso as credenciais setadas do usuário sejam diferentes do desenvolvedor](#caso-as-credenciais-setadas-do-usuário-sejam-diferentes-do-desenvolvedor)
1.2 [Caso as credenciais não estejam setadas](#caso-as-credenciais-não-estejam-setadas)
1.3 [Quando as credenciais estiverem setadas](#quando-as-credenciais-estiverem-setadas)
2. [Passando o repositório local para o remoto (GitHub)](#passando-o-repositório-local-para-o-remoto-github)
3. [Como atualizar o repositório remoto](#como-atualizar-o-repositório-remoto)
4. [Como mudar repositório local de máquina](#como-mudar-repositório-local-de-máquina)
5. [Como atualizar um repositório já existente com a versão remota](#como-atualizar-um-repositório-já-existente-com-a-versão-remota)

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

> [!WARNING]
> Ao retornar para um repositório em que o *push* já foi feito anteriorente, existe a possibilidade dele ter sido modificado em outra máquina ou mesmo diretamente no repositório remoto. Caso isso tenha acontecido, vão existir duas versões diferentes do mesmo repositório, o que pode ocasionar em conflitos na hora de efetuar o *push*.
> Para evitar isso, é interessante executar o comando `git pull` antes de qualquer alteração no repositório local. Isso fará com que o repositório local seja atualizado com a versão do repositório remoto, e evitará este problema.

Após enviar o seu repositório local para o repositório remoto, obviamente você retornará mais cedo ou mais tarde para o seu projeto, a fim de dar manutenção ou de corrigir possíveis erros encontrados após o *push*, ou até mesmo após a implementação da sua aplicação. Ao alterar qualquer coisa do seu projeto, seja no código-fonte, imagens estáticas ou mesmo na estrutura de pastas, o seu projeto terá atualizações não incluídas na versão que foi *commitada*.

Isso significa que, ao terminar as novas alterações, você deverá *commitar* novamente o seu projeto, a fim de criar uma nova versão dele. O procedimento para fazer isso não necessariamente será identico ao da primeira vez, já que desta vez você não precisará inicializar um repositório local, já que ele já existe, nem precisará vinculá-lo ao GitHub: ele já está vinculado. As únicas coisas que precisará fazer é adicionar as alterações ao *stage*, *commitar* e fazer o *push*, que é o reenvio do seu repositório local ao remoto, atualizando a versão que está no GitHub com a versão que está no seu computador.

Para fazer isso, execute no terminal os comandos a seguir:
- `git add <nome-do-novo-arquivo>` - adiciona novo arquivo ao *stage; ou `git add <nome-do-arquivo-alterado>` - adiciona o arquivo modificado ao *stage*; ou `git add .` - adiciona todos os arquivos novos e alterados ao *stage*
- `git commit -m "Mensagem do commit."` - *commita*, ou seja, cria uma nova versão do projeto, diferente da versão anterior
- `git push` - envia a nova versão do projeto para o GitHub

> [!TIP]
> Caso tenha dúvidas, se tiver seguido o passo a passo para o primeiro *commit*, e/ou se tiver as credenciais já setadas, pode simplesmente executar os comandos a seguir na seguinte ordem:<br>
> `git add .`<br>
> `git commit -m "Mensagem do commit."`<br>
> `git push`<br>

## Como mudar repositório local de máquina

Caso esteja trabalhando em um projeto, e por algum motivo, queira trabalhar no mesmo projeto em outra máquina, é necessário clonar o seu repositório para esta nova máquina, desde que ela tenha o programa Git instalado.

- Acesse o GitHub, e dentro do repositório, clique no botão verde **Code** no canto direito da tela da página do repositório
- Copie a URL do endereço do repositório que se encontra nesse botão
- Veja na imagem abaixo
![alt text](image.png)
- Volte ao diretório do seu repositório local e execute o comando a seguir
- `git clone <endereco-do-repositorio-remoto>` - baixa o repositório remoto para a máquina que não possui uma versão desse repositório

> [!NOTE]
> Este procedimento fará com que um repositório que antes estava em outra máquina agora passe para sua nova máquina, mas isso deve ser feito somente caso esta nova máquina não tenha uma versão anterior desse mesmo repositório. Caso o PC em questão já tenha uma versão anterior deste repositório, o procedimento a ser feito é outro, que veremos a seguir.

## Como atualizar um repositório já existente com a versão remota

Caso a máquina que você esteja mexendo já tenha uma versão anterior do repositório, então o procedimento a ser feito não é um clone, mas sim um ***pull***, que atualiza o repositório local com a versão do repositório remoto. Basta executar o comando a seguir:

- `git pull` - atualiza o repositório local com a versão mais recente do repositório remoto.

> [!IMPORTANT]
> Ao retornar para um repositório já existente, é uma boa prática começar executando `git pull` antes de começar a trabalhar, para não esquecer e acabar gerando duas versões atualizadas diferentes do mesmo repositório, o que pode ocasionar conflitos entre as versões, e consequentemente a perda de progresso do seu projeto.

