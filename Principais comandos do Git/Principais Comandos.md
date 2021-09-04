### Setup Inicial

Define o nome do usuário, ou seja, é este nome que aparece quando você vê o autor de um commit por exemplo.

```
git config --global user.name "Marcelo Costa"
```

Define o e-mail do usuário padrão:

```
git config --global user.email "seu@email.com.br"
```

Juntamente você pode escolher qual o editor de código o GIT utiliza por padrão, ele é usado por exemplo para editar arquivos de configuração do próprio GIT ou para exibir reports, bem como quando um auto merge falha e necessita da sua analise.

```
git config --global core.editor subl
```

No lugar “subl”, digitar o seu editor, exemplos:

Sublime Text => subl
Visual Code => code

Se adicionar a opção “–wait” (ex. “code –wait”) mantém o Terminal aberto até o editor ser fechado.

**Dica:** [neste outro post](https://marcelocosta.com.br/como-criar-um-arquivo-global-de-configuracao-do-git/) ensino como alterar essas configurações básicas e outras direto no editor de texto, alterando e adicionando configurações globais do GIT.

Visualizar o nome do usuário:

```
git config user.name
```

Listar todas as configurações:

```
git config --list
```

### Projeto novo (local)

Para iniciar um novo projeto com versionamento pelo GIT, basta abrir o terminal / bash e digitar:

```
git init
```

### Servidor remoto

Para trabalhar com um servidor remoto, antes de tudo é preciso adicionar a referência dele ao GIT, ou se você clonar um projeto diretamente do GitHub essa configuração torna-se desnecessária.

```
git remote add nome_do_remote ssh://usuario@caminho_e_nome_completo_do_repositorio.git 
```

Para verificar quais os remotes já cadastrados:

```
git remote -v
```

Enviar commits para o “servidor”:

```
git push web master
```

Onde “web” é o nome do repositório adicionado com o ‘git remote’ e “master” é o branch.

Receber commits do “servidor”:

```
git pull web master
```

Onde “web” é o nome do repositório adicionado com o ‘git remote’ e “master” é o branch.

### Gerenciamento

Mostrar o status do git:

```
git status
```

Mostra o Log de alterações do projeto:

```
git log
```

Além dos dados do comando acima, exibe também o diff de cada arquivo:

```
git log -p
```

Exibe versão curta do Log de alterações do projeto:

```
git shortlog
```

Você pode utilizar comandos GIT customizados, como por exemplo para para exibir um log formatado e resumido. Dica: Se a listagem for grande apertar “q” para encerrar.

```
git log --pretty=format:'%C(blue)%h %C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
```

![Exemplo de Comando GIT customizado](https://marcelocosta.com.br/wp-content/uploads/2018/01/gitlog-exemplo.png)Captura de tela exemplificando o uso de GIT log log personalizado.

Alterações feitas nos arquivos que ainda não foram adicionadas na “staged area”:

```
git diff
```

Alterações feitas nos arquivos da “staged area”:

```
git diff --staged
```

### Commits

Adiciona todos os arquivos da pasta:

```
git add -A
```

Ao contrário do comando acima, adiciona somente mudanças em arquivos já monitorados:

```
git add -U
```

Este é o mais utilizado por mim, ele adiciona todos os arquivos da árvore, sejam edições ou novos arquivos desde que não estejam na lista de arquivos a serem ignorados:

```
git add.
```

Gera uma versão “estável” com comentário:

```
git commit -m "mensagem de commit"
```

Gera uma versão “estável” e torna desnecessário o GIT ADD com comentário:

```
git commit -a -m "mensagem de commit"
```

Remove arquivos que já estão sendo monitorados pelo GIT:

```
git rm --cached pasta_ou_arquivo -r
```

A flag -r é de recursivo, usar quando for uma pasta e quiser remover todo o conteúdo dela.

### Branchs

Ver lista dos branchs (o atual estará com * e em verde):

```
git branch
```

Ver o ultimo commit em cada branch:

```
git branch -v
```

Cria um novo branch e muda para ele ao mesmo tempo:

```
git checkout -b nomeBranchNovo
```

O comando acima é o equivalente ao 2 comandos abaixo:

```
// cria um branch
git branch nomeBranchNovo

// muda para o branch
git checkout nomeBranchNovo
```

Trazer mudanças do branch X para o master:

```
git checkout master
```

Merge das alterações no branch master (já estando nele, comando acima):

```
git merge nomeBranchNovo
```

Exclui o branch:

```
git branch -d nomeBranchDeletar
```

