# Trabalhando com Git e GitHub


=> Baseado nos cursos: Introdução ao Git e ao GitHub(digitalinnovation); Git e GitHub [20 Horas](Curso em video); Git e Github para iniciantes(Udemy)



**git  init ** => iniciar git, estamos criando um repositório dentro do diretório(pasta)

**git add** => mover arquivos e iniciar de fato o versionamento

**git commit** => Comitar 



obs: todo comando do Git leva a palavra Git na frente e o comando especifico logo após



## **Visualizando logs**

Buscando pelo log informações

Essas informações são importantes para poder decidir se volto, avanço etc.

**vim Readme.md** => editar arquivo 

**git log --oneline** => histórico de commites

**git checkout -b main** => trocando **main** para o lugar do **master** no diretório local

**git log --author="Will" ** => listar todos os commits de um autor

**git  shortlog**  => lista em ordem alfabetica os autores e quantos commites fizeram

**git shortlog -sn** => quantidade de commites e a pessoa

**git log --graph**=> mostra em forma gráfica o que está acontecendo com meus branchs e versões

**git log**

hache = códigos únicos gerados em cada commit , pela hache consigo ver o que foi adicionado ou não no commit

**git show**	=> consigo ver mais partes adicionadas ex: link



### **Visualizando o diff**

**git status**

**vim Readme.md** => editar arquivo e inserir um texto na linha

**git  diff** => vai mostrar a minha modificação, o sinal de mais "+" sinaliza que eu acrescentei

cada mudança que eu fizer consigo olhar o git diff antes de commitar

obs: sempre utilize o git diff antes de commitar, assim você sempre da uma lida e uma revisada 

**git diff --name-only**  => dizer o nome do arquivo modificado, ótimo quando tem uma grande lista

**git commit -am "Edit Readme"**=> commitar arquivo que já existiu

**git log** => verificar meu commit

**git show** => 



### Desfazendo Coisas

**git checkout arquivo.md** => retornar arquivos e modificações quando ainda em **estado de edição**

**git reset --** => retornar arquivos e commits que estão no **staged**

Ex: digitei alguma coisa errado, mas não quero ficar apagando o arquivo todo, só quero tirar o que ele tinha feito da ultima vez


**git log** => vejo ultimos commits

**git status** => verificar se tem modificação

**Vim Readme.md** => editar arquivo

**git status** => **modified**

**git diff** => mostra a mudança

obs: vamos supor que eu vi que fiz a alteração no arquivo errada

**git checkout Readme.md** => vai retornar o arquivo para antes da edição

**git diff** => nenhuma diferença

**vim Readme.md** => abrir o arquivo e ver que não tem mais a alteração

agora altera o arquivo novamente 

**git add Readme.md** => dessa vez adiciona na área de **stage**

**git status** => **modified**, dessa vez mudanças pronta pra ele 

**git diff**=> agora não mostra nenhuma diferença pra ele o estado já está consolidado, não tem diferença só falta commitar

 obs: mas eu quero voltar porque faltou um detalhe para eu editar

**git reset HEAD Readme.md** => quero voltar para o meu ponteiro que eu já estou, quero remover arquivo do estage 

**git diff** => mostra que voltou com a modificação

**git checkout Redme.md** => vou tirar novamente minha mudança 

**git status** => nada para fazer 

**git status** 

**git commit -am "Alterei"**=> commitar direto **am** adiciona todos os arquivos modificados

**git reset** **--soft**=> o **git reset** tem o **--soft**(mata as modificações mas o arquivo já vai estar em **staged** com a modificação prontinho para ser commitado novamente), **--mixed**(mata o commit mas voltar arquivos para antes de **staged** ou seja **modified**), **--hard**(simplesmente ignora a existência do commit e tudo o que foi feito nele, mata o commit) deve ser usado com cuidado, ex: só se não tiver jogado no repositório remotoem que outras pessoas estão mexendo 

**git reset --soft b4f2245546b565çlkjbhh4456** =>a partir de qual para cima quero mudar? ex: se quero o ultimo na verdade escolho o penúltimo(**hach** b4f2245546b565çlkjbhh4456)

**git status** 

**git commit -m "ljklkjljklkjkl"** => o outro commit sumiu e agora tem esse


### Criando e Adicionando uma chave SSH

Problemas ao enviando código para o Remoto

**SSH** =>  protocolo que serve para autenticar usuário remoto ao servidor, é baseado em chaves aonde existe uma publica e uma privada, onde a chave privada consegue abrir a publica somente essa chave, ou seja agente envia essa chave publica para o servidor (GitHub) , com a chave privada dentro da nossa máquina a gente consegue abrir a chave publica do servidor e é capaz de subir nosso código

https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh



**Gerar chave SSH**

clicar => **Generating a new SSH key**

no terminal => colocar linhas de código

```shell
ssh-keygen -t ed25519 -C "your_email@example.com"
```

no terminal => Enter

no terminal => Enter

**cd ~/.ssh/** => Diretório aonde fica as chavez  **SSH** (~ = home)

**ls** => colocar no git hub a chave **id_rsa.pub**

**cat  id_rsa.pub**=> pegar a chave, depois do comando mostra a chave

 **more id_rsa.pub** => tem a mesma chave

**vi id_rsa.pub**=> ou posso abrir a chave no editor de texto



**Adicionar chave SSH no GitHub**

agora copia a chave e vai para o **GitHub > Settings > SSH and GPG Keys > New SSH > inserir a chave em Keys > inseri titulo de acordo com a chave** ex: nome da máquina "Windows Pro" ou home e work para diferenciar trabalho ou pessoal **> ADD SSH Key**

agora vou poder utilizar o git hub e poder fazer **PUSH** sem dar erro de permissão



### Ligando um repositório local a um remoto

**git remote add origin https://github.com/Teste/testar-api.git** => vai adicionar um repositório remoto com o nome origin(nome default para determinar que é a origem do remoto mas pode ser outro nome)

**git remote** => mostra que já tem um repositório origin

**git remote -v** => mais informações

**git push -u origin master** =>envia os arquivos, logs e modificações para o repositório que eu estou determinando (**-u** serve para não precisar ficar digitando a linha inteira novamente, no próximo só digito **git push**)



### Enviando mudanças para um repositório remoto

**Vim Readme.md** => editar arquivo 

**git status** 

**git commit -am "alterei"**(**-a** = mandar direto **m**=mandar a mensagem)

**git log** => ver os commits

**git push origin master**



### Clonando repositórios remotos

**git clone   https://github.com/Teste/testar-api.git github-course-clone** => clonei com outro nome



### Fazendo fork de um projeto

fork pega um projeto que não é meu, faz uma copia para mim, digamos que tem um repositório que eu quero ajudar a e contribuir, eu vi um erro nele, ou faltando alguma documentação, ou algum código.

1.  faço **fork**
2.  faço as **mudanças**
3.  envio um **pull request** para a pessoa informando as mudanças que eu fiz



Ele é diferente do clone, **clone** só consigo fazer para os repositórios que são meus de fato que depois quero mandar essas modificações para o GitHub. Se eu não for dono posso até clonar mas se fazer modificação não consigo enviar porque o repositório não é meu e eu não tenho permissão 



### Ramificação(Branch)

Ponteiro móvel que leva a um commit

**Vantagens**

- Poder modificar sem alterar o local principal
- Facilmente "desligável"
- Múltiplas pessoas trabalhando
- Evita conflitos



Criar um novo branch

**git checkout -b testing** => **-b** = criar um branch e passar o nome do branch

**git branch** =>  mostra as brachs existentes e o "*****" dizendo o branch que eu estou



Movendo e deletando branches

**git checkout** **testing** => ir para um branch que eu queira

**git checkout master** => voltei para a master

**git branch -D testing** => apagar um branch que eu não quero mais utilizar

**git branch** => confirmar quantas tenho agora


Merge e Rebase

indicado:Merge(estou no master)
Casos de Pull Request, repositórios que de fato foi unido, juntou a feature

mkdir rebase-merge => criei pasta
cd rebase-merge/ => acessei pasta
git init => inicializar o repositorio
vim foo=> criar arquivo chamado foo
git status
git add foo
git commit -m "Add foo"
git checkout -b test => criar novo branch
vim bar => criar arquivo chamado bar
git status
git add bar
git commit -m "Add bar"
git log 
git checkout master=> voltar para o master só para ver quais arquivos tem
git log
vim fizz=> novo arquivo
git add fizz
git commit "Add fiz"
git log
git merge test
git log 
git log --graph


Rebase(estou no master)
indicado: trabalhando e adicionando  commits e sempre atualizando os outros brabchs

vim buzz => criei arquivo
git add.
git commit
git checkout -b rebase-branch=> criar um novo bramch
vim bla => criei novo arquivo
git add.
git commit -m"Add bla"
git log graf 
git checkout master
git log
vim seila
git add.
git commit -m "Add sei la"
git log
git rebase rebase-branch
git log -- graph

Criando git ignore =>

-----------------------------------------------

### 1- Criar um repositório (pasta ex: **workspace**)

obs: abrir GitBash direto da pasta, elimina a necessidade de eu ficar navegando entre as pastas, todos os passos fazer direto na (MASTER)



**Git Bash** => botão direito em cima do arquivo, abri com Git Bash

**ls** => listar

**cd** **workspace**  => acessei a pasta

**mkdir** **livro-receitas** => criar uma pasta dentro da pasta

**LS** => listar para confirmar  criação da pasta



### 2- Iniciar Git

 **git  init**

**ls** => a pasta  **.git** fica oculta, é uma pasta gerencial aonde fica todo o código do git , aonde versiona os objetos que manipulamos

**ls -a** => a fleg **-a**  mostra as pastas ocultas 

**cd .git/** => entrei na pasta oculta

**ls** => listei para visualizar a pasta com sua estrutura, obs: para a pasta **objects**(arquivos e objetos ficam nessa pasta, o  objeto commit é criado com um autor atrelado)

**cd...** => voltei um nivel na pasta

---------------------------------------

 _**configuração inicial**_

se for a primeira vez que estou usando o git ele vai pedir as configurações: username, email



**git config --global ** user.email "teste@teste.com"  => posso setar de forma global ou apenas para o repositorio

**git config --global ** user.name Teste

-------------------------------------------------

_**adicionando arquivo markdown** "**.MD**_ "

dentro do repositorio(pasta), crie um arquivo com a extensão markdown => botão direito > novo > Documento de texto > muda extensão para **.md **> escreva alguma receita no arquivo

------------------------------------------

### 3- Gerar primeiro COMMIT

**git add *** ==> vou COMMITAR o arquivo criado(receita)

**git commit -m** "commit inicial"=> passei uma string, um texto



---------------------------------------------------

### 4- Ciclo de Vida

**Conceitos** 

​                                     ===============Tracked====================

Untracked                   Unmodified                      Modified                     Staged

​       **==============**adiciona o arquivo=**=======================>**

​                                                **==**Edita o arquivo**====>**

​                                                                                       **==**"Stage" o arquivo**=>**

​        **<===**Remove o arquivo**==**

​                                                  **<==================**Commit**=========**



**git -add *** => move para **Staged**

**git -commit -m** => move os arquivos que estavam na area de **Staged** e volto eles para **Unmodified** , criou um snap shot ou uma foto do estado dos arquivos e coloco eles para não modificados para que ele retorne para o ciclo, eu populo o repositório local, o repositorio local será composto por commits(sem commitar não consigo enviar para o repositório remoto)

-------------------------------

Git é um sistema distribuido, ele tem a versão dele no servidor, e a minha  versão  na máquina



**Servidor**  

 REMOTE REPOSITORY  

**Ambiente de desenvolvimento**

WORKING DIRECTORY           STAGING AREA          LOCAL REPOSITORY



obs: Quando faço um commit  passa a fazer parte do meu repository local

----------------------------------------------------

**ls** => listar os arquivos

**git status**  => retorna se houve alteração, estado de trabalho etc. (vou usar com frequencia)

**mkdir**  receitas => criei pasta receitas

**ls**  => listar

**mv strogonoff.md** **./receitas/** => mover;  do repositório que estou quero buscar outro repositorio 

**ls** => listar 

**cd receitas/** => entrei dentro da pasta que listou

**ls** => para verificar arquivo strogonof

**cd..** => voltar voltar um nivel

**git status**=> vai trazer mais mudanças e algumas em **not staged** que precisam de commit

**git add strogonoff.md receitas/** => duas modificações, arquivo e pasta nova

**git status** => mudaram para **stage** e estão prontos para serem **commitados**

git commit -m "criando pasta receitas, move arquivo para receitas"=> fiz commit e criei uma mensagem 

**git status**=>  não tem nenhum arquivo para commitar, nenhum **Untracked**  e **Modified**    

**echo > README.md** => adicionar **arquivo** **index**

**git status** => git vai falar que não tem **Untracked** ou não rastreados

obs: abrir arquivo e colocar titulo ex: Livro de receitas e listar receitas

**git status** => git vai falar que tem **Untracked**

**git add*** => mover para **Staged**, "*"  pega tudo que foi modificado do diretorio de trabalho

**git status** => mudanças para serem commitadas, ou seja estão em **Staged**

**git commit -m "adiciona index"** => agora tenho o arquivo README.md ou a capa do livro



### 5- Git Hub

Ideal é que as configurações da plataforma e máquina local estejam iguais(credenciais)

**git config --list** => tras a lista de todas as configurações que estão no git

reescrever configurações

**git config --global --unset  user.email**

 **git config --global --unset  user.nickname**

**git config --global --unset  user.email "teste@teste.com"** =>passar email novamente(mesmo do github)

 **git config --global --unset  user.nickname  "teste"** =>  passar nickname novamente(mesmo do github)



empurrar a versão do repositório local para uma origem remota

1. crio um repositório no gihub
2. copio a url do repositório criado

3. empurrar **(pelo "git bash")** a versão para repositório ou origem remoto, vou passar o link do repositório criado no git hub

**git remote add origin https://github.com/Teste/testar-api.git**

**git remote -v** => trás a lista de repositórios remotos que estou cadastrado(**pasta .git**)

**git status**=> me certificar que não tem nenhuma pendência no repositório

**git push origin master** => empurrar do local para remoto(obs: master ou main)



### **6- Conflitos de merge, Git Hub**  

1. Alteração na mesma linha de código em branch diferentes
2. Tento fazer merge na master mas o git identifica que existe um conflito, ou seja a minha branch está diferente de outra branch no mesmo local(pode ser virgula, pontos etc). O GitHub não vai fazer nada ele vai indicar para eu ir e alterar o correto. 

exemplo de correção:

obs: O **README** sofreu alteração

**git status**  => changes not **staged** for commit (verificar se o arquivo está com **status modified**) 

**git add *** => adicionar tudo

**git status** => agora tenho mudanças para serem comitadas, changes to be commited(unstage)

**git commit -m "Adiciona alteração"** 

**git push origin master** => vai apresentar falha ao empurrar, ele tentou integrar as branchs mas tem algum trabalho/alteração/commit/data diferente do local

**git pull origin master** => puxar as alterações do remoto para a minha máquina, 

erro: 

CONFLICT(content): Merge conflict in README.md

Automatic merge failed; fix conflicts and then commit the result



nesse caso o conflito pode ser solucionado fazendo a alteração manual do arquivo **README**

**git status** =>  alerta para fazer commit

**git add *** =>  adicionar arquivo na área de **staged** 

**git commit -m "Resolve conflitos"** 

**git pull origin master** => olhar no github e confirmar



### **7- Baixar/clonar repositório**

1. No terminal preciso estar no local de trabalho ex: workspace
2. copiar a url(.git) de um repositório no git hub

3. clonar

**git clone "https://github.com/Teste/testar-api.git"  **=> vai fazer download

**ls** => verificar se está no repositório

**cd Teste/**

**ls -a** => se tiver **.git** , não é uma pasta comum mas um **repositório**

**git remote -v**








