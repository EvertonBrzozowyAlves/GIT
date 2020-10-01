# GIT
O GIT é um sistema de versionamento de arquivos, usado principalmente para controlar versões de arquivos utilizados por várias pessoas.  
Quando temos um projeto em que várias pessoas acessam e modificam os mesmos arquivos, é interessante utilizar o GIT como ferramenta de controle de código fonte.    

## Configuração inicial
O mínimo para iniciar os trabalhos com GIT e associar um usuário as ações que serão tomadas.  
Para configurar nome de usuário e email:
```
git config --local user.name "Seu nome aqui"
git config --local user.email "seu@email.aqui"
```

>Nota sobre os níveis de configurações no GIT:  
>1. --system (para todos os usuários e projetos na máquina atual)
>2. --global (seu usuário na máquina atual)
>3. --local (somente projeto atual)

## Configurações gerais
Para alterar uma propriedade das configurações, podemos usar o seguinte comando:
```
git config --<nível> <nomeConfiguracao> "<valorDesejado>"
git config --local user.name "John Doe"
```

Para visualizar a configuraçao para uma propriedade:
```
git config <nomeConfiguracao>
git config <user.name>
```

Alterar o editor de texto das configurações para vscode:
```
git config --global core.editor code    
```

Editar as configurações em modo global: 
```
git config --global --edit              
```

## Comandos

Inicializa um novo repositório Git  
```
git init
```

Exibe o status dos arquivos em relação ao repositório:
```
git status
```
Para salvar um estado dos arquivos no GIT, fazemos um commit:
```
git commit -m 'primeiro commit'
```

## Log
O log permite visualizar o histórico e os detalhes dos commits efetuados no repositório GIT.  
Para visualizar o log de maneira padrão: 
```
git log
```

Um log resumido:
```
git log --oneline
```

Um log mais detalhado:
```
git log -p
```

A saída do log pode ser configurada de diversas formas, usando o comando **--pretty**.

Formatando o log:
>%C(cor)  
%h: hash do commit reduzido  
%d: branch  
%s: mensagem  
%cn: quem fez o commit  
%cr: data commit  

Exemplo de configuração (adicionar ao arquivo .gitconfig):

```
git log --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr' 
```

Exemplo no .gitconfig, para não ter que repetir o comando todas as vezes:

```
[core]
	editor = code --wait //para que o git tenha tempo de carregar os dados no arquivo antes de abrir

[alias]
    s = !git status -s //associa o comando git status -s (status resumido) ao alias s
    c = !git add --all && git commit -m // para usar: 'git c "mensagem"'
    l = !git log --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
```

## .gitignore
O .gitignore é um arquivo que criamos para que o GIT não monitore determinados arquivos/pastas.  
Para isso, criar o arquivo com esse nome e depois adicionar os nomes de arquivos ou pastas a serem ignorados.
>Para funcionar corretamente, o ideal é que os arquivos a serem ignorados já não tenham sido adicionados ao versionamento e commitados.  
Se esse for o caso, será necessário remover o arquivo do versionamento e adicionar ao .gitigore.

Exemplo de .gitignore:
```
ignoreme/            //Ignora a o diretorio 'ignoreme' e o seu conteúdo
ignoreme.txt         //Ignora qualquer arquivo com nome 'ignoreme.txt'
ignoreme/*/*.txt     //Ignora qualquer arquivo com extensão .txt, dentro de qualquer diretório, dentro de um diretório chamado ignoreme
```

O **#** adiciona uma comentário no arquivo, desconsiderando aquela linha.
