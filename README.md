# Estudo de Git/GitHub
## Autores

| [<img loading="lazy" src="https://avatars.githubusercontent.com/u/165854883?v=4" width=115><br><sub>Gabriel Campos</sub>](https://github.com/Super-Link) |  [<img loading="lazy" src="https://avatars.githubusercontent.com/u/80770771? v=4" width=115><br><sub>Pedro Guedes</sub>](https://github.com/pedroaugustorgg) |  [<img loading="lazy" src="https://avatars.githubusercontent.com/u/93458723?v=4" width=115><br><sub>Sergio Campos</sub>](https://github.com/camposcomunicacao) |
| :---: | :---: | :---: |

📗**Repositório de apoio/inspiração:** [leocomelli/git.md](https://gist.github.com/leocomelli/2545add34e4fec21ec16)

# 🖥️ Principais comandos para seu versionamento de código via terminal com git:

## Clonando um repositório já existente para sua pasta local:
- O comando "git clone" serve para clonar todo o repositório remoto diretamente para um repositório local, é bem simples e ocorre da seguinte forma:
        
        git clone <URLdoRepositório>
    
    - **Exemplo prático:** 

            git clone https://github.com/pedroaugustorgg/EstudoGit

<br/> 

## ⚙️ Como setar seu usuário e e-mail do GitHub localmente para trabalhar com repositórios remotos (só precisa fazer uma vez):
- ### Setando usuário:

        git config --global user.name <NomeDoUsuário>

    - **Exemplo prático:**

            git config --global user.name "Pedro Guedes"

- ### Setando e-mail:

        git config --global user.email <E-mailDoUsuário>

    -  **Exemplo prático:**

            git config --global user.email pedroaugustorgg@gmail.com

<br/>

## 🌐 → 🖥️ Sincronizando repositório LOCAL com conteúdo do repositório REMOTO do GitHub:
- Caso seu usuário e e-mail já esteja sincronizado com o repositório:
        
        git pull

- Caso o repositório local ainda não esteja sincronizado, você precisará informar a URL do repositório que deseja:

        git pull <remoteURL>

    -  **Exemplo prático:**
    
            git pull https://github.com/pedroaugustorgg/EstudoGit

<br/>

## 🛠️ Gestão de repositório (add, *commits* e *branches*)
- ### ADD ➕
    O comando "git add" serve para adicionar os arquivos com alterações realizadas no repositório dentro do *commit* a ser realizado posteriormente. Segue um exemplo prático:

            git add index.html

    - 💡 **Dica valiosa:** Para que não haja a necessidade de ir adicionando os arquivos tratados um a um, você pode utilizar o seguinte comando que irá adicionar todas as alterações realizadas:

            git add .

<br/>

- ### BRANCHES 🧑‍🧒‍🧒
    As *branches* são basicamente os "setores" dentro do mesmo repositório que podem ser utilizadas de forma simultânea e paralela ao setor/branche principal, que geramente é chamada de ***main*** ou ***master*** por padrão, porém pode ser qualquer nome que o dono do respositório queira chamar. Para visualizar as branches continas no repositório local, você pode utilizar o seguinte comando:
            
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
        - **⚠️ Observação.:** Para realizar o merge, é necessário estar no branch que deverá receber as alterações. O merge pode automático ou manual. O merge automático será feito em arquivos textos que não sofreram alterações nas mesmas linhas, já o merge manual será feito em arquivos textos que sofreram alterações nas mesmas linhas. A mensagem indicando um merge manual será:

                Automerging meu_arquivo.txt
                CONFLICT (content): Merge conflict in meu_arquivo.txt
                Automatic merge failed; fix conflicts and then commit the result.

    ### 💡 BONUS
    - ***REBASE*** entre *branches*
        - O "rebase" serve basicamente para sincronizar uma branch com outra ([mais detalhes clicando aqui](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)). Imaginando um cenário real, o rebase poderia ser utilizado para sincronizar uma branch de desenvolvimento com uma branch em produção. Segue um exemplo prático de uma sincronia da branch "developer" com a branch "main":

                git checkout developer
                git rebase main

<br/>

- ### COMMITS ✅
    O *commit* serve para como um "registro" de todas as tratativas realizadas no repositório em questão (seja ajuste em linhas de código ou até mesmo adição/exclusão de arquivos) desde a última sincronia realizada.

        git commit -m "Título do commit" -m "descrição do commit"

<br/>

### 🖥️ → 🌐 Sincronizando repositório REMOTO do GitHub com repositório LOCAL:
- Com todos os commits devidamente realizados, você pode enviar tudo o que você fez localmente para atualizar o repositório remoto com o seguinte comando:
    
        git push <remoteURL> <NomeDaBranch>

    -  **Exemplo prático:** Sincronizando todo o trabalho local com a branch "DevPedro" do repositório remoto.
    
            git push https://github.com/pedroaugustorgg/EstudoGit DevPedro

- 💡 **Dica valiosa:** Para sincronizar diretamente na branch remota sem a necessidade de validar pull request lá no GitHub, deve-se utilizar o seguinte comando:
        
        git push --set-upstream origin <NomeBranchRemota>

<br/>

### 🆘 Resolução de conflitos (erros comuns):

- ✅ [Lidar com erros non-fast-forward](https://docs.github.com/pt/enterprise-cloud@latest/get-started/using-git/dealing-with-non-fast-forward-errors)
  - Exemplo prático:

        ❌! [rejected]        main -> main (non-fast-forward)❌