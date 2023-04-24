# Git e Github: controle e compartilhe seu código

## Comandos Básicos
### Iniciando um repositório e versionamento pelo Git
```
mkdir - Cria um novo repositório.
cd - Navega entre os repositórios.
git init - Inicializa o monitoramento do git sobre o repositória atual.
```

### Atualizando modificações de um arquivo
```
touch - Cria um arquivo.
git status- Mostra estágio dos arquivos no repositório.
git add <nome_do_arquivo> - Adiciona o arquivo especificado na area de stage.
git add . - Adiciona todos arquivos que contenham modificações ou foram criados na area de stage.
git commit -m - Guardar o estado do seu repositório atual + mensagem das alterações realizadas.
git commit -am - adiciona todos os arquivos modificados na área de stage e, em seguida, guardar o estado do seu repositório atual + mensagem das alterações realizadas.
git log - Exibe os informações sobre os commits realizados.
git log -n - Exibe a quantidade "n" (ex.: 1, 2, 3) de logs dos commits realizados.
git log -p - Exibe as mudanças realizadas em cada commit.
git log --graph - Exibe graficamente as mudanças realizadas pela branch atual e possíveis ramificações.
```


### Criando um servidor local para compartilhar dados
```
git init --bare - Funcionam como um servidor e são considerados repositórios apenas para armazenamento que contém apenas as alterações dos arquivos, e não uma cópia física de cada um dos arquivos.
git remote - Lista todos repositórios remotos que são reconhecidos localmente.
git remote add <nome_servidor_remoto> <caminho> - adiciona um servidor remoto localmente, sendo que podemos dar um nome para esse servidor e em seguida colar a rota no qual ele se encontra, podendo ser uma rota de rede ou url.
git remote -v - Além de listar os repositórios remotos, também informa a rota em que ele está localizado.
git clone <caminho_servidor_remoto> - Copia localmente os dados de um repositório remoto.
```

### Sincronizando dados e repositórios
```
git fetch <nome_servidor_remoto> <nome_branch > - Traz referências do repositório remoto localmente a fim de verificar diferenças que possam ter ocorrido mas não gera nenhum tipo de mudança localmente.
git pull <nome_servidor_remoto> <nome_branch > - Traz referências do repositório remoto incorporando-as localmente. 
git push <nome_servidor_remoto> <nome_branch > - Envia para o repositório remoto as modificações locais.
```

### Ramificações
```
git branch - lista as ramifições de trabalho
git branch <nome_branch> - Cria uma nova ramificação a partir da ramificação atual.
git checkout <nome_branch> - Navega entre as ramificações.
git checkout -b <nome_branch> - Cria uma nova ramificação e navega até ela em sequência.
git branch -d <nome_branch> - Exclui uma ramificação. É necessário realizar a exclusão a partir de outra ramificação.
git push <nome_servidor_remoto> --delete <nome_branch> - Exclui uma ramificação remota.
```

### Atualizando Branchs
```
git merge <branch_origem> - Atualiza a branch atual com os dados da branch origem e gera um commit
git rebase <branch_origem> - Atualiza a branch atual com os dados da branch origem, porém, não gera um commit dessa ação.
```

### Guia de Rebase
```
git checkout <branch_origem>
git pull
git checkout <branch_de_trabalho>
git rebase <branch_origem>
git push --force-with-tease - Esta opção permite forçar o push sem o risco de sobrescrever acidentalmente o trabalho de outra pessoa.
git checkout <branch_origem>
git merge <branch_de_trabalho>
```


## Informações Adicionais
### Estágios de modificação dos arquivos no repositório
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

### Ignorando arquivos
__.gitignore__
>Neste arquivo podemos anotar arquivos e diretórios que podem ser ignorados pelos Git e não são necessários ter um controle sobre eles, geralmente podem ser arquivos de configuração de ambiente ou qualquer outro que não queremos que faça parte do nosso diretório monitorado pelo Git.