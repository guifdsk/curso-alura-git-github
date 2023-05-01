# Módulo Git e GitHub

## Índice <a id='0'></a>
- [Comandos Básicos](#1)
  - [Iniciando um repositório e versionamento pelo Git](#1.1)
  - [Atualizando modificações de um arquivo](#1.2)
  - [Criando um servidor local para compartilhar dados](#1.3)
  - [Branchs](#1.4)
  - [Sincronizando dados e repositórios](#1.5)
  - [Guia de Rebase](#1.6)
  - [Versões de repositórios e de arquivos](#1.7)
  - [Vizualizando alterações](#1.8)
- [Informações Adicionais](#2)
  - [Estágios de modificação dos arquivos no repositório](#2.1)
  - [Ignorando arquivos com .gitignore](#2.2)
  - [Git Checkout - Switch - Restore](#2.2)
  


## [Comandos Básicos](#0) <a id='1'></a>

### [Iniciando um repositório e versionamento pelo Git](#0) <a id='1.1'></a>
```
mkdir <nome_do_diretorio>
cd <nome_do_diretorio>
git init
```
`mkdir` - Cria um novo diretório no local atual.

`cd <nome_do_diretorio>` - Navega entre os diretórios.

`git init` - Transforma o diretório atual em um repositório do Git. 

### [Atualizando modificações de um arquivo](#0) <a id='1.2'></a>
```
touch <nome_do_arquivo>
git status
git restore .
git restore <nome_do_arquivo>
git clean -df
git add <nome_do_arquivo>
git add .
git restore --staged .
git restore --staged <nome_do_arquivo>
git commit -m "mensagem"
git commit -am "mensagem"
git commit -m "mensagem" -m "mensagem adicional"
```
`touch <nome_do_arquivo>` - É usado para criar um arquivo vazio.

`git status` - Lista os arquivos e seus respectivos estágios no diretório, sendo eles: preparados(_Staged_), despreparados(_Modified_/_Deleted_) e não foram monitorados(_Untracked_).

`git restore .` - Remove as alterações realizadas nos arquivos que estão visíveis (working tree) e não foram adicionados à área _staged_, retornando ao estado do _commit_ atual (_HEAD_).

`git restore <nome_do_arquivo>` - Remove as alterações realizadas no arquivo especificado que não foi adicionado à área _staged_.

`git clean -df` - Remove um arquivo criado que não foi adicionado à área _staged_.

`git add .` - Adiciona as modificações de arquivos, arquivos criados ou removidos no diretório ativo à área de _staged_. No entanto, as modificações são gravadas de fato quando for realizado um _commit_.

`git add <nome_do_arquivo>` - Adiciona as modificações do arquivo especificado no diretório ativo à área de _staged_.

`git restore --staged .` - Retira todos arquivos que foram adicionados à área de _staged_.

`git restore --staged <nome_do_arquivo>` - Retira o arquivo especificado que foi adicionado à área de _staged_.

`git commit -m "mensagem"` - Grava o estado do seu repositório atual, associado com uma mensagem referente às mudanças. Somente as mudanças com estado _staged_ farão parte do _commit_. 

`git commit -am "mensagem"` - Associa o comando "git add ." ao comando de _commit_, adicionado todos arquivos à área de _staged_ antes de realizar o _commit_.

`git commit -m "mensagem" -m "mensagem adicional"` - Grava o estado do seu repositório atual, associado com duas mensagens referente às mudanças, sendo a segunda uma descrição mais detalhada.

### [Trabalhando com servidor local e repositórios remotos](#0) <a id='1.3'></a>
```
git init --bare - Funcionam como um servidor e são considerados repositórios apenas para armazenamento de alterações dos arquivos, e não uma cópia física de cada um dos arquivos.
git remote - Lista todos repositórios remotos que são reconhecidos localmente.
git remote add <nome_repositorio_remoto> <caminho> - Adiciona um repositório remoto localmente, sendo que podemos dar um nome para esse repositório e em seguida colar a rota no qual ele se encontra, podendo ser uma rota de rede ou url.
git remote -v - Além de listar os repositórios remotos, também informa a rota em que ele está localizado.
git remote remove <nome_repositorio_remoto> - Remove um repositório remoto.
git clone <caminho_repositorio_remoto> - Copia localmente os dados de um repositório remoto.
```

### [Branchs](#0) <a id='1.4'></a>
```
git branch
git branch -a
git branch <nome_nova_branch>
git switch <nome_branch>
git switch -c <nome_nova_branch>
git switch -
git branch -d <nome_branch>
git branch -D <nome_branch>
git push <nome_repositorio_remoto> --delete <nome_branch>
git branch -m <novo_nome_branch>
git branch -m <nome_branch> <novo_nome_branch>
```
`git branch` - Lista as branchs de trabalho.

`git branch -a` - Lista as branchs remotas.

`git branch <nome_nova_branch>` - Cria uma nova branch a partir da branch atual.

`git switch <nome_branch>` - Navega entre as branch.

`git switch -c <nome_nova_branch>` - Cria uma nova branch e navega até ela em sequência.

`git switch -` - Retorna para branch main/master.

`git branch -d <nome_branch>` - Exclui uma branch de forma segura, caso não tenha realizado um push dos dados commitados não será possivel realizar a exclusão. É necessário realizar a exclusão a partir de outra branch.

`git branch -D <nome_branch>` - Força a exclusão da branch, idependentemente do seu estado. É necessário realizar a exclusão a partir de outra branch.

`git push <nome_repositorio_remoto> --delete <nome_branch>` - Exclui uma branch remota.

`git branch -m <novo_nome_branch>` - Renomeia a branch atual de trabalho.

`git branch -m <nome_branch> <novo_nome_branch>` - Renomeia outra branch.

### [Sincronizando dados e repositórios](#0) <a id='1.5'></a>
```
git fetch <nome_repositorio_remoto> <nome_branch>
git pull <nome_repositorio_remoto> <nome_branch>
git push <nome_repositorio_remoto> <nome_branch>
git merge <branch_origem>
git rebase <branch_origem>

git revert
```
`git fetch <nome_repositorio_remoto> <nome_branch >` - Traz referências do repositório remoto localmente a fim de verificar diferenças que possam ter ocorrido mas não gera nenhum tipo de mudança localmente.

`git pull <nome_repositorio_remoto> <nome_branch >` - Traz referências do repositório remoto incorporando-as localmente. 

`git push <nome_repositorio_remoto> <nome_branch >` - Envia para o repositório remoto as modificações locais.

`git merge <branch_origem>` - Atualiza a branch atual com os dados da branch origem e gera um commit.

`git rebase <branch_origem>` - Atualiza a branch atual com os dados da branch origem, porém, não gera um commit dessa ação.

### [Guia de Rebase](#0) <a id='1.6'></a>
```
git switch <branch_origem>
git pull
git switch <branch_de_trabalho>
git rebase <branch_origem>
git push --force-with-tease - Esta opção permite forçar o push sem o risco de sobrescrever acidentalmente o trabalho de outra pessoa.
git switch <branch_origem>
git merge <branch_de_trabalho>
```

### [Versões de repositórios e de arquivos](#0) <a id='1.7'></a>
```
git restore --source <hash_commit> <nome_arquivo>
git restore --source <hash_commit> .
git tag -a <nome_versao> -m "mensagem"
git tag
git checkout <tag_versao>
git stash
git stash -u
git stash -a
git stash save "mensagem"
git stash pop
git stash list
git stash pop <hash_do_stash>
git stash clear
```
`git restore --source <hash_commit> <nome_arquivo>` - Restaura o estado de um determinado arquivo do hash parametrizado para sua branch de trabalho.

`git restore --source <hash_commit> .` - Restaura o estado de todos os arquivos do hash parametrizado para sua branch de trabalho.

`git tag -a <nome_versao> -m "mensagem"` - adiciona uma tag de versao no git, assim podemos ter um controle de atualizações relevantes no repositório.

`git tag` - Lista as tags encontradas no repositório.

`git checkout <versao>` - Restaura o estado de um determinado arquivo da verão parametrizada para sua branch de trabalho desanexado (detached) do controle de versão.

`git stash` - Salva as alterações de arquivos que ainda não passaram por um commit em uma lista de stash e volta sua branch para ao estado do último commit.

`git stash -u` - Inclui no stash arquivos não rastreados e modificados.

`git stash -a` - Inclui no stash mudanças em arquivos ignorados, não rastreados e modificados.

`git stash save "mensagem"` - Adiciona uma mensagem ao stash salvo, caso contrário a mensagem será salva com a hash e mensagem do ultimo commit.

`git stash pop` - Busca o primeiro stash salvo na lista e trás as informações contidas nele, logo após ele apaga essa informação da lista de stash.

`git stash list` - Exibe uma lista de stashs criados.

`git stash pop <hash_do_stash>` - Adiciona alterações contidas no stash e o exclui da lista.

`git stash clear` - Limpa a lista de stash.

### [Vizualizando alterações](#0) <a id='1.8'></a>
```
git log
git log -n
git log -p
git log --oneline
git log --author="user_name"
git log --graph
```
`git log` - Exibe os informações sobre os commits realizados.

`git log -n` - Exibe a quantidade "n" (ex.: 1, 2, 3) de logs dos commits realizados.

`git log -p` - Exibe as mudanças realizadas em cada commit.

`git log --oneline` - Exibe os commits realiziados de forma reduzida.

`git log --author="user_name"` - Exibe commits realizado por um determinado autor.

`git log --graph` - Exibe graficamente as mudanças realizadas pela branch atual e possíveis branchs.

## [Informações Adicionais](#0) <a id='2'></a>

### [Estágios de modificação dos arquivos no repositório](#0) <a id='2.1'></a>
__Unmodified (não modificado)__
>Estado em que o repositório não possuí nenhum tipo de alteração.

__Untracked (não rastreado)__
>O arquivo ainda não está sob monitoramento do Git. Quando criamos um novo arquivo em nosso repositório precisamos fazer com o que o Git entenda que ele precisa ser monitorado para verificar possíveis alterações e realizar o controle de versões.

__Modified (modificado)__
>Significa que o arquivo monitorado pelo Git sofreu alterações em seu conteúdo, sendo diferente da última versão disponível.

__Deleted (excluido)__
>O arquivo monitorado pelo Git não está mais presente no repositório.

__Staged ou Stage (preparado)__
>Após realizar alterações ou criação de arquivos, precisamos informar ao Git quais deles serão adicionados à nova versão, o Git precisa saber que o arquivo foi modificado e agora está na área de preparação para ser consolidado.

### [Ignorando arquivos com .gitignore](#0) <a id='2.2'></a>

>Nele podemos anotar arquivos e diretórios que podem ser ignorados e ficam fora da visão do Git para o controle de versionamento, geralmente podem ser arquivos de configuração de ambiente ou qualquer outro que não queremos que faça parte do nosso diretório monitorado pelo Git.

### [Git Checkout - Switch - Restore](#0)<a id='2.3'></a>
> A partir da versão 2.23.0 foram implementados novos comandos e ambos vêm com o intuito de dividir responsabilidades do comando "checkout", e serem mais específicos para as funções que se propõem realizar. Os novos comandos são o git restore e o git switch e ambos foram citados nos modulos acima, substituindo os comandos abaixo, por exemplo:
```
Switch
git checkout <nome_branch>
git checkout -b <nome_nova_branch>

Restore
git checkout -- .
git checkout -- <nome_do_arquivo>
git checkout <hash_commit>
```