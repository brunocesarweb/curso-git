
     ,-----.,--.                  ,--. ,---.   ,--.,------.  ,------.
    '  .--./|  | ,---. ,--.,--. ,-|  || o   \  |  ||  .-.  \ |  .---'
    |  |    |  || .-. ||  ||  |' .-. |`..'  |  |  ||  |  \  :|  `--, 
    '  '--'\|  |' '-' ''  ''  '\ `-' | .'  /   |  ||  '--'  /|  `---.
     `-----'`--' `---'  `----'  `---'  `--'    `--'`-------' `------'
    ----------------------------------------------------------------- 


Hi there! Welcome to Cloud9 IDE!

To get you started, create some files, play with the terminal,
or visit http://docs.c9.io for our documentation.
If you want, you can also go watch some training videos at
http://www.youtube.com/user/c9ide.

Happy coding!
The Cloud9 IDE team

--------------------------------------------
Anotações do curso:

2- aula:

Para que um repositório seja monitorado pelo git utiliza-se o comando:
git init

Assim o git monitora a pasta que recebeu esse comando e monitora também suas sub-pastas


Comando que verifica se tem arquivos controlados pelo git:
git ls-files

Comando git status mostra o status atual dos arquivos.

Comando git add para adicionar as mudanças para comitar

Comitar use o comando
git commit -m "Mensagem para comitar"

Configurar o usuário
git config --global user.name "Meu nome"
git config --global user.email "meuemail@email.com.br"

O parametro --global configura o usuario globalmente no pc, se tirar esse parametro ele configura somente no projeto.

3 - aula:

Comando:
git log
Mostra um histórico com os commits feitos até o momento

git whatchanged
Ver com mais detalhes dos arquivos incuidos/alterados

se adicionar mos o parametro -p consguimos ver com mais detalhes as alterações
git whatchanged -p

Comando git remote
Mostra quais repositorios remotos o atual repositorio tem

Adicionar um repositorio origin( que será o apelido do repositorio ele pode ser escolhido por quem desenvolve):
git remote add origin URL_DO_REPOSITORIO_REMOTO
Executar o comando git remote, aparecerá o repositorio remoto.
Com isso, você está indicando que o repositório Git local se conecta com um repositório remoto através do alias ou atalho origin cujo endereço real é https://github.com/[seu_usuario_no_github]/curso-git.git.
Lembre-se de substituir [seu_usuario_no_github] por seu nome de usuário. Se quiser conferir o resultado, utilize o comando git remote -v

Comando git push
Ele funciona para enviar as alterações para o repositorio remoto no caso o repositório origin e qual a branch que vai ser enviada(master)
git push origin master
Vai solicitar usuario e senha.
Outra alternativa é utilizar, no primeiro push, a opção -u ou --set-upstream.
Ela atrela a branch remota à local, fazendo com que não seja mais necessário passar como parâmetros a origem e a branch no comando push, que fica então assim: git push.


Comando git clone
Clona um repositorio para a máquina


4- aula:

Criar uma branch usa o comando
$ git branch nome_da_branch

acrescentando o -b você cria e muda para a branch
$ git branch -b nome_da_branch

Para mudar de branch comando:
$ git checkout nome_da_branch

O comando
$ git branch -a nome_da_branch
São listadas as branch locais e remotas, sem o -a são listadas somente as locais


Depois de fazer o push da branch e for fazer o pull é preciso sincronizar a branch local com a remoto
Usando o comando abaixo para subir a branch local para a remoto:
$ git push -u origin design

Outro usuário usando os arquivos
O comando:
$ git branch -r 
Mostra somente as branchs remotas

O comando:
$ git branch -t origin/design
O outro usuário cria uma branch design jã traqueada com a branch remoto

Comandos para apagar branch remotas:
$ git push -d origin design
e
$ git push origin :design


Comando
$ git fetch origin
É possível verificar as atualizações que foram realizadas no repositório referente ao origin


5 - aula:

Resolução de conflitos:

Quando dois usuários diferentes mexem no mesmo arquivo, o primeiro altera o arquivo remoto faz o commit e o push,
o segundo ao fazer o push recebe a mensagem que o seu commit foi rejeitado.
É necessário atualizar o repositório local, usando o comando git pull, ao fazer isso o git jã tenta fazer o merge automático dos arquivos.
O merge é feito automaticamente, pode ser verificado com o comando git log que mostra o merge feito.

Outro tipo de conflito, se caso dois usuários mexerem na mesma informação, como por exemplo na mesma linha.

O segundo usuário ao tentar fazer o push acontecerá o conflito, será necessário fazer o pull, e uma mensagem de conflito aparecerá pois ele não conseguiu fazer o merge das alterações.

Ao verificar o arquivo temos a informação:

<<<<<<<<< HEAD
        Isso  aqui é o conteúdo do site
    </main>>
=========
        Isso aqui é o conteúdo da página
    </main>
>>>>>>>>> 548efa50f5...

Onde o que está entre o HEAD e o === é o conteúdo que estava antes de fazer o git pull com os commits para subir, 
e entre o ==== e o >>>>> eo hash do commit é o que veio do repositório remoto.

Para resolver é preciso ir apagando o que não for ficar no arquivo e salvar o arquivo, e adicionar no git usando o comando add
$ git add nome_do_arquivo_que_estava_com_conflito

Depois é necessário fazer o commit:
$ git commit -m "Merge dos conflitos"

Feito isso é possível fazer o git push:
$ git push

O outro usuário não fez o push de suas alterações também, ele fará agora:
$ git push
Será rejeitado, e será feito o git pull, e aparecerá uma mensagem de conflito.
Teremos que resolver o conflito:

<<<<<<<<< HEAD
        Aqui está o conteúdo da página
=========
        Isso aqui é o conteúdo do site
>>>>>>>>> dba81c7f220...

No HEAD temos o conteúdo local e depois do ===== temos o conteúdo remoto.

*Ferramentas visuais de merge:
O comando git mergetool mostra no console uma lista de programas possíveis de ser utilizados. Dessa lista, pode-se escolher um, instalar no seu computador e utilizar através do comando git mergetool -t nome_do_programa.

Para saber mais, execute o comando git mergetool --help no terminal e veja as opções possíveis.

Algumas das ferramentas gratuitas mais comuns são o kdiff3, Meld ou P4Merge. Em MacOSX também existe o semi-nativo FileMerge, que vem junto com o XCode.


6 - aula:

Boas pŕaticas do uso do git, resoluão de conflitos, criação de branchs desenvolvimento.
Comandos: branch, merge, pull, push, add, etc...

1-Da branch master, utilize o comando git checkout -b testeRebase para criar e se mover para uma nova branch
2-Altere alguns arquivos, crie um ou dois commits nesta branch
3-Volte para a master e faça a mesma coisa, se possível evitando conflitos. Crie arquivos com nomes diferentes, por exemplo, e faça um ou dois commits novos
4-Volte para a testeRebase e crie mais um ou dois commits
5-Dê uma olhada na saída do comando git log e repare que os commits que criou na master não estão listados
6-Execute o comando git rebase master para aplicar os commits de lá que faltam na branch testeRebase
7-Dê uma olhada na saída do comando git log e repare que os commits que criou na master estão listados, mas não estão por último
Explicação:
O objetivo do comando git rebase é fazer com que a branch em que se está tenha um novo HEAD, "copiado" de outra branch. 
Ou seja, a base da branch, a partir da qual você vai realizar seus commits, deverá ser modificada. 
Para isso, caso haja commits novos na branch que terá a base trocada, o Git os coloca em um local temporário e em seguida começa a aplicar a nova base. 
Após a atualização do HEAD, o Git começa a aplicar seus commits sobre a nova base.
Vale ressaltar que se você criou dois commits na branch testeRebase, depois um na master e então mais um na testeRebase, a ordem em que eles aparecerão no git log é exatamente esta, pois os commits são reaplicados na ordem em que foram criados, baseado no horário do commit.


7 - aula:
Removendo alterações que foram para o repositório:

-Criar uma branch de desenvolvimento, para fazer as alterações.

Para que seja desfeita as alterações nos arquivos que ainda não foram adicionados ao git usamos o comando:
$ git checkout nome-do-arquivo.html

Depois de ter feito o git add e quiser desfazer a alteração o git checkout com o nome do arquivo não vai funcionar, é preciso fazer o comando abaixo:
$ git reset HEAD nome-do-arquivo.html
Isso faz com que a alteração que foi adicionada retorne ao seu estado anterior e pode ser retirado com o git checkout.

Depois de ter adicionado e ter comitado a mudança como fazer para remover as alterações:
Usar o comando:
$ git log
Copiar o identificador do commit que é um número serial, e usar o comando reset
$ git reset df18e05997ffa9642e63ede51b19a02e3d599062
Assim o commit é desfeito e a branch volta ao estado anterior.

Desfazer alterações do commit, para isso é necessário usar o comando revert e o identificador(hash) do commit:
$ git revert df18e05997ffa9642e63ede51b19a02e3d599062

Comando git stash, guarda as alterações que ainda não foram comitadas e precisariam ficar guardadas temporariamente.
$ git stash

Pode seguir o fluxo de commit, para verificar se tem alguma alteração no stash usar o comando:
$ git stash list

Para retomar usar pop
$ git stash pop

Ou de maneira mais específica:
$ git stash apply stash@{0}
Onde stash@{0} é a identificação da alteração

A alteração não é removida do stash list, para isso tem que usar o comando:
$ git stash drop

Procurar commits para desfazer:
Ferramenta bisect

Comandos: $ git bisect
(good, bad, etc.)

--Explicação

Como vimos, o comando git checkout serve tanto para trocar de branch quanto descartar alterações de um arquivo do working directory. Mas se possuímos um arquivo e uma branch com o mesmo nome, o Git trata como padrão considerar que o usuário quer mudar de branch. Precisamos então de uma alternativa para diferenciar a branch do arquivo.
Para isso existe uma notação no comando git checkout, que indica que daqui pra frente só serão listados arquivos. Digamos que temos as branches design e master (e estamos na master) e o arquivo design que na master contém alterações. Para garantir que vamos restaurar o arquivo, precisamos usar o seguinte comando:
git checkout -- design
Essa notação de dois hífens -- indica que os parâmetros seguintes serão todos nomes de arquivos, permitindo que restauremos o arquivo design ao estado original.

A notação -- permite que passemos quantos nomes de arquivos quisermos. Repare que é diferente, por exemplo, das opções do comando git rebase:
git checkout -- design
git rebase --continue
A opção do rebase tem os hífens colados no texto. Já o separador do checkout dá um espaço, permitindo a diferenciação.
--Explicação


8 - aula

Ao iniciar criar uma branch de desenvolvimento para continuar:
$ git checkout -b desenvolvimento

Fazer todo o processo de subir.

Criar os aliases ou traduzindo os apelidos, para poder criar vamos ter que alterar o arquivo gitconfig
$ vim ~/.gitconfig

Para criar os apelidos configurar o gitconfig:
[alias]
    st = status
    
Ao salvar o arquivo você pode usar o comando:
$ git st 
Para exibir o status a partir de agora

Para criar um atalho para enviar dados para master
[alias]
    st = status
    envia = !git checkout master && git pull && git checkout desenvolvimento && git rebase master && git checkout master && git merge desenvolvimento && git push

Agora usando o comando $ git envia ele faz todo o processo descrito no alias

Exibindo informações:
$ git log --pretty='%an realizou commit em %ad: %s' --graph

Fork do projeto

9 - aula

Passando um commit específico para a master, ao desenvolver faça os commits e estando na master use o comando:
$ git cherry-pick a0e5b6c
é o comando cherry-pick passando o hash do commit

É preciso que tenha cuidado para não trazer um commit que dependa de outro para a branch principal.

10 - aula
Uso de interfaces












