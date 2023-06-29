---
title: Git colinha
created: 2022-010-28
aliases: 
tags: [git, github]
note_status: finished
publish: true
---

# Configuração do Repositório

```bash
# Clone um repositório existente 
$ git clone ssh:user@domain.com.repo.git  

# Inicie um novo repositório 
$ git init
```

# Trabalhando com Mudanças Locais

```bash
# Verifique arquivos alterados em seu diretório atual 
$ git status  

# Veja as mudanças nos arquivos rastreados 
$ git diff  

# Adicione todas mudanças atuais para o próximo commit 
$ git add .  

# Adicione algumas mudanças no `<arquivo>` para o próximo commit 
$ git add -p <arquivo>  

# Faça o commit de todas as mudanças locais nos arquivos rastreados 
$ git commit -a  

# Faça o commit de mudanças anteriormente colocadas em stage 
$ git commit  

# Altere o último commit 
# Não altere commits publicados! 
$ git commit --amend
```

# Trabalhando com a História do Commit

```bash
# Mostra todos commits, começando pelo mais recente 
$ git log  

# Mostra as mudanças ao longo do tempo para um arquivo específico 

$ git log -p <arquivo>  

# Veja quem alterou o quê e quando no `<arquivo>` 
$ git blame <arquivo>
```

# Trabalhando com Branches e Tags

```bash
# Liste todos os branches existentes 
$ git branch -av 

# Mude o branch HEAD 
$ git checkout <branch>  

# Crie um novo branch baseado na sua HEAD atual 
$ git branch <novo-branch>  

# Crie um novo branch de rastreamento baseado em um branch remoto 
$ git checkout --track <remoto/branch>  

# Delete um branch local 
$ git branch -d <branch>  

# Marque o commit atual com uma tag 
$ git tag <tag-name>
```

# Atualizar e Publicar

```bash
# Liste todos os remotos atualmente configurados 
$ git remote -v  

# Mostre informações sobre o remoto 
$ git remote show <remoto>  

# Adicione um novo repositório remoto, chamado `<nomecurto>` 
$ git remote add <nomecurto> <url>  

# Baixe as mudanças e as funda/integre diretamente na HEAD 
$ git pull <remoto> <branch>  

# Publique mudanças locais em um remoto 
$ git push <remoto> <branch>  

# Delete um branch no remoto 
$ git branch -dr <remote/branch>  

# Publique suas tags 
$ git push --tags
```

# Merge e Rebase

```bash
# Funda `<branch>` na sua HEAD atual 
$ git merge <branch>  

# Faça rebase da sua atual HEAD no `<branch>` 
# Não faça rebase de commits publicados! 
$ git rebase <branch>  

# Aborta rebase $ git rebase --abort  
# Continue um rebase após resolver conflitos 
$ git rebase --continue  

# Use sua ferramenta de fusão configurada para resolver conflitos 
$ git mergetool  

# Use seu editor para resolver conflitos manualmente e (após resolver) marque o arquivo como resolvido 
$ git add <resolved-arquivo> 
$ git rm <resolved-arquivo>
```

# Refazer e Reverter Mudanças

```bash
# Descarte todas as mudanças locais em seu diretório atual
$ git reset --hard HEAD

# Descarte mudanças locais em um arquivo específico
$ git checkout HEAD <arquivo>

# Reverta um commit (produzindo um novo commit com mudanças contrárias)
$ git revert <commit>

# Resete a HEAD para um commit anterior
## Descarte todas as mudanças desde então
$ git reset --hard <commit>
## Preserve todas as mudanças como mudanças ainda não postas em stage
$ git reset <commit>
## Preserve mudanças locais não commitadas
$ git reset --keep <commit>
```

