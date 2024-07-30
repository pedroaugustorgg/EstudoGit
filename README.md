# <img src="https://img.icons8.com/?size=100&id=20906&format=png&color=000000" alt="branches" width="30px">🖥️ Principais comandos para seu versionamento de código via terminal com git

📗**Repositório de apoio/inspiração:** [leocomelli/git.md](https://gist.github.com/leocomelli/2545add34e4fec21ec16)

## ÍNDICE
 <a href="#section1">**1.**<img src="https://img.icons8.com/?size=100&id=4VuUVaM5Sn5D&format=png&color=000000" alt="clone" width="22px"> Clonando um repositório do GitHub para sua pasta local</a>

 <a href="#section2">**2.** ⚙️ Como setar seu usuário e e-mail do GitHub localmente para trabalhar com repositórios remotos (só precisa fazer uma vez)</a>

 <a href="#section3">**3.** 🌐 → 🖥️ Sincronizando repositório LOCAL com conteúdo do repositório REMOTO do GitHub (*pull*)</a>

 <a href="#section4">**4.** 🛠️ Gestão de repositório (add, *branches* e *commits*)</a>

 <a href="#section5">**5.** 🖥️ → 🌐 Sincronizando repositório REMOTO do GitHub com conteúdo do repositório LOCAL (*push*)</a>

 <a href="#section6">**6.** 🆘 Resolução de conflitos (erros comuns)</a>

 <a href="#section7">**7.** <img src="https://img.icons8.com/?size=100&id=K7ebDTcbruY8&format=png&color=000000" alt="teamgroup" width="25px"> Autores</a>

 <hr><br>

## <p id="section1"> <img src="https://img.icons8.com/?size=100&id=4VuUVaM5Sn5D&format=png&color=000000" alt="clone" width="25px"> Clonando um repositório do GitHub para sua pasta local:
- O comando "git clone" serve para clonar todo o repositório remoto diretamente na sua máquina, isso fará com que seja criado um arquivo oculto ".git" na pasta local onde vc irá clonar o repositório e você poderá começar a gerenciar o repositório localmente. É bem simples a execução do comando e ocorre da seguinte forma:
        
        git clone <URLdoRepositório>
    
    - **Exemplo prático:** 

            git clone https://github.com/pedroaugustorgg/EstudoGit

<br/> 

## <p id="section2"> ⚙️ Como setar seu usuário e e-mail do GitHub localmente para trabalhar com repositórios remotos (só precisa fazer uma vez):
- ### Setando usuário:

        git config --global user.name <NomeDoUsuário>

    - **Exemplo prático:**

            git config --global user.name "Pedro Guedes"

- ### Setando e-mail:

        git config --global user.email <E-mailDoUsuário>

    -  **Exemplo prático:**

            git config --global user.email pedroaugustorgg@gmail.com

- ### Conferindo usuário e email setados:

        git config user.name && git config user.email

  -  ⚠️ **Observação:** Caso você tenha setado o usuário e/ou e-mail errado, basta ir na pasta oculta ".git" do seu repositório e alterar o arquivo "config", lá estará o seu usuário e senha setados anteriormente.

<br/>

## <p id="section3"> 🌐 → 🖥️ Sincronizando repositório LOCAL com conteúdo do repositório REMOTO do GitHub (*pull*):
- Caso seu usuário e e-mail já esteja setado no repositório local, para importar o conteúdo do GitHub para sua máquina, basta utilizar o seguinte comando:
        
        git pull

- Caso o repositório local ainda não esteja sincronizado, você precisará informar a URL do repositório que deseja:

        git pull <remoteURL>

    -  **Exemplo prático:**
    
            git pull https://github.com/pedroaugustorgg/EstudoGit

<br/>

## <p id="section4"> 🛠️ Gestão de repositório (add, *branches* e *commits*)
- ### ➕ ADD
    O comando "git add" serve para adicionar os arquivos com alterações realizadas no repositório dentro do *commit* a ser realizado posteriormente. Segue um exemplo prático:

            git add index.html

    - 💡 **Dica valiosa:** Para que não haja a necessidade de ir adicionando os arquivos tratados um a um, você pode utilizar o seguinte comando que irá adicionar todas as alterações realizadas:

            git add .

<br/>

- ### <img src="https://img.icons8.com/?size=100&id=n7YnpFzywxHh&format=png&color=000000" alt="branches" width="25px"> BRANCHES
    As *branches* são basicamente os "setores" dentro do mesmo repositório que podem ser utilizadas de forma simultânea e paralela ao setor/branch principal, que geramente é chamada de ***main*** ou ***master*** por padrão, porém pode ser qualquer nome que o dono do respositório queira chamar. Para visualizar as branches continas no repositório local, você pode utilizar o seguinte comando:
            
            git branch

    - Para **CRIAR** uma branch, o seguinte comando deve ser executado:

            git branch <NomeDaBranch>
        - 💡 **Dica valiosa:** Para criar uma nova branch e já trocar para ela, basta utilizar o comando -b, ficando da seguinte forma:

                git branch -b <NomeDaBranch>

    - Para **REMOVER** uma branch, o seguinte comando deve ser executado:

            git branch -d <NomeDaBranch>

    - Para **TROCAR** de branch no respositório, o seguinte comando deve ser executado:

            git checkout <NomeDaBranch>

        - 💡 Baixando uma *branch* remota para edição localmente:

                git checkout -b DevPedro origin/DevPedro

    - Para **MERGEAR (mesclar)** uma branch com a outra, o seguinte comando deve ser executado:
            
            git checkout main
            git merge DevPedro
        - ⚠️ **Observação.:** Para realizar o merge, é necessário estar no branch que deverá receber as alterações. O merge pode ser automático ou manual. 

                Automerging meu_arquivo.txt
                CONFLICT (content): Merge conflict in meu_arquivo.txt
                Automatic merge failed; fix conflicts and then commit the result.

    ### 💡 BONUS
    - ***REBASE*** entre *branches*
        - O "rebase" serve basicamente para sincronizar uma branch com outra ([mais detalhes clicando aqui](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)). Imaginando um cenário real, o rebase poderia ser utilizado para sincronizar uma branch de desenvolvimento com uma branch em produção. Segue um exemplo prático de uma sincronia da branch "developer" com a branch "main":

                git checkout developer
                git rebase main

<br/>

- ### <img src="https://img.icons8.com/?size=100&id=Cz0Q4xlXhAVM&format=png&color=000000" alt="commits" width="25px"> COMMITS
    O *commit* serve para como um "registro" de todas as tratativas realizadas no repositório em questão (seja ajuste em linhas de código ou até mesmo adição/exclusão de arquivos) desde a última sincronia realizada.

        git commit -m "Título do commit" -m "descrição do commit"

  - 💡 **Dica valiosa:** A sequencia de comandos mais comum para verificar os arquivos editados, salvar todas as suas alterações locais em um commit e mesclar com a branch principal do repositório (main ou master) é a seguinte:

        git status
        git add .
        git commit -m "Título do commit" -m "descrição do commit"
        git checkout main
        git merge <branch_com_alteracoes>

<br/>

## <p id="section5"> 🖥️ → 🌐 Sincronizando repositório REMOTO do GitHub com conteúdo do repositório LOCAL (*push*):
- Com todos os commits devidamente realizados, você pode enviar tudo o que você fez localmente para atualizar o repositório remoto com o seguinte comando:
    
        git push <remoteURL> <NomeDaBranch>

    -  **Exemplo prático:** Sincronizando todo o trabalho local com a branch "DevPedro" do repositório remoto.
    
            git push https://github.com/pedroaugustorgg/EstudoGit DevPedro

- 💡 **Dica valiosa¹:** Para sincronizar todas as branches locais com as branches remotas, basta utilizar o seguinte comando:
        
        git push --all origin

- 💡 **Dica valiosa²:** Para sincronizar uma branch específica diretamente na branch remota (sem a necessidade de validar pull request lá no GitHub), deve-se utilizar o seguinte comando:
        
        git push --set-upstream origin <NomeBranchRemota>
  - ⚠️ **Observação.:** NÃO irá funcionar caso seja o primeiro push da máquina local para o repositório remoto.

<br/>

## <p id="section6"> 🆘 Resolução de conflitos (erros comuns):

- ### ❌ Erro: *non-fast-forward*
  - **Problema:** Repositório local não sincronizado com repositório online e pode ocorrer durante um push
  - [Link com solução](https://docs.github.com/pt/enterprise-cloud@latest/get-started/using-git/dealing-with-non-fast-forward-errors) ✅ A dica é realizar uma sincronia do repositório remoto com o seurepositório local através do comando "git pull origin <nome_da_branch>"
  - Exemplo prático do erro:

                $ git push 
                ! [rejected]        main -> main (non-fast-forward)

- ### ❌ Erro: *main does not match any*
  - **Problema:** Divergência de match entre as branches, pode ocorrer ao fazer um push do repositório local para o remoto.
  - [Link com solução](https://stackoverflow.com/questions/4181861/message-src-refspec-master-does-not-match-any-when-pushing-commits-in-git) ✅ Também pode ocorrer durante um push, a dica é verificar se os nomes da(s) branch(es) local (comando "git branch") estão iguais aos nomes das branches remotas, após isso, realizar um push específico da branch desejada com o comando "git push origin <nome_da_branch>".
  - Exemplo prático do erro:
        
                $ git push
                error: src refspec main does not match any
                error: failed to push some refs to <URLdaBranch>

- ### ❌ Erro: *Merge conflict*
  - **Problema:** Ocorre durante um merge entre branches.Como o merge automático é feito em arquivos textos que não sofreram alterações nas mesmas linhas, o merge manual precisa ser feito em arquivos textos que sofreram alterações nas mesmas linhas. Caso não seja feito, isso resultará em um conflito.
  - [Link com solução](https://www.dio.me/articles/corrigindo-conflitos-em-merges-no-git) ✅ A dica é adicionar os arquivos com o comando "git add <nome_do_arquivo>" ou "git add .", commitar as alterações já adicionadas e realizar o merge posteriormente.
  - Exemplo prático do erro:

                $ git checkout main
                $ git merge DevPedro
                Automerging <NomeDoArquivo.txt>
                CONFLICT (content): Merge conflict in meu_arquivo.txt
                Automatic merge failed; fix conflicts and then commit the result.

<br/>

- ### ❌ Erro: *Pulling is not possible*
  - **Problema:** Normalmente ocorre quando você tenta realizar um pull (puxar conteúdo do repositório remoto para o local) e existe alguma alteração no seu repositório local que precisa ser desfeita ou commitada para ser possível seguir com o pull.
  - [Link com solução](https://pt.stackoverflow.com/questions/455932/não-consigo-fazer-git-pull-no-servidor) ✅ A dica pra solucionar esta intercorrência é conferir alterações ainda não commitadas com o comando "git status" e realizar o commit ou desfazer alguma alteração com o comando "git checkout <arquivo.txt>".
  
    - 💡 **Dica valiosa:** Para desfazer TODAS as alterações locais NÃO COMITADAS você pode usar o comando "git reset --hard HEAD".
  - Exemplo prático do erro:

                $ git pull
                error: Pulling is not possible because you have unmerged files.
                hint: Fix them up in the work tree, and then use 'git add/rm <file>'
                hint: as appropriate to mark resolution and make a commit.
                fatal: Exiting because of an unresolved conflict.

<br/>

## <p id="section7"> <img src="https://img.icons8.com/?size=100&id=K7ebDTcbruY8&format=png&color=000000" alt="teamgroup" width="30px"> Autores

| [<img loading="lazy" src="https://avatars.githubusercontent.com/u/165854883?v=4" width=115><br><sub>Gabriel Campos</sub>](https://github.com/Super-Link) |  [<img loading="lazy" src="https://avatars.githubusercontent.com/u/80770771? v=4" width=115><br><sub>Pedro Guedes</sub>](https://github.com/pedroaugustorgg) |  [<img loading="lazy" src="https://avatars.githubusercontent.com/u/93458723?v=4" width=115><br><sub>Sergio Campos</sub>](https://github.com/camposcomunicacao) |
| :---: | :---: | :---: |