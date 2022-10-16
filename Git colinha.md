#git 

Ver [[Git]]

# Criar
#### Clone um repositório existente
```bash
$ git clone ssh:user@domain.com.repo.git
```

#### Clone um repositório existente
```bash
$ git init
```

# Mudanças locais
#### Arquivos alterados em seu diretório atual
```bash
$ git status
```

#### Mudanças no arquivo rastreado
```bash
$ git diff
```

#### Adicione todas mudanças atuais ao próximo commit
```bash
$ git add .
```

#### Adicione algumas mudanças no `<arquivo>` para o próximo commit

```bash
$ git add -p <arquivo>
```

#### Commite todas as mudanças locais nos arquivos rastreados
```bash
$ git commit -a
```

#### Commite mudanças anteriormente colocadas em stage
```bash
$ git commit
```

#### Mude o último commit
###### *Não complemente commits publicados!*
```bash
$ git commit --amend
```

# História de commits
#### Mostrar todos commits, começando do mais novo
```bash
$ git log
```

#### Mostrar mudanças ao longo do tempo de um arquivo em específico
```bash
$ git log -p <arquivo>
```

#### Quem mudou o quê e quando no `<arquivo>`
```bash
$ git blame <arquivo>
```

# Galhos e tags
#### Liste todos os galhos existentes
```bash
$ git branch -av
```

#### Mudar o galho CABEÇA
```bash
$ git checkout <galho>
```

#### Crie um novo galho baseado na sua CABEÇA atual
```bash
$ git branch <novo-galho>
```

#### Crie um novo galho de rastreio baseado em um galho remoto 
```bash
$ git checkout --track <remoto/galho>
```

#### Delete um galho local
```bash
$ git branch -d <galho>
```

#### Marque o commit atual com uma bandeira
```bash
$ git tag <tag-name>
```

# Update and publicar
#### Liste todos os remotos presentemente configurados
```bash
$ git remote -v
```

#### Mostrar informação sobre remoto
```bash
$ git remote show <remoto>
```

#### Adicione novo repositório remoto, chamado `<remoto>
```bash
$ git remote add <nomecurto> <url>
```

#### Baixe as mudanças e diretamente fundir/integrar em CABEÇA
```bash
$ git pull <remoto> <galho>
```

#### Publique mudanças locais em um remoto
```bash
$ git push <remoto> <galho>
```

#### Delete um galho no remoto
```bash
$ git branch -dr <remote/galho>
```

#### Publique suas tags
```bash
$ git push --tags
```

# Merge & rebase
#### Funda `<galho>` em sua CABEÇA atual
```bash
$ git merge <galho>
```

#### Rebaseie sua atual CABEÇA no `<galho>`
###### *Nãp rebaseie commits publicados!*
```bash
$ git rebase <galho>
```

#### Aborte rebase
```bash
$ git rebase --abort
```

#### Continue uma rebase depois de resolver conflitos
```bash
$ git rebase --continue
```

#### Use sua ferramenta de fusão configurada para para resolver conflitos
```bash
$ git mergetool
```

#### Use seu editor para manualmente solucionar conflitos e (após resolver) marcar arquivo como resolvido
```bash
$ git add <resolved-arquivo>
$ git rm <resolved-arquivo>
```

# Refazer
#### Descartar todas as mudanças locais em seu diretório atual. 
```bash
$ git reset --hard HEAD
```
#### Descarte mudanças locais em um arquivo específico
```bash
$ git checkout HEAD <arquivo>
```

#### Reverta um commit (produzindo um novo commit com mudanças contrárias)
```bash
$ git revert <commit>
```

#### Resete o [[ponteiro]] de sua cabeça CABEÇA para um commit anterior
##### ...e descarte todas as mudanças desde então
```bash
$ git reset --hard <commit>
```
##### ...e preserve todas as mudanças como mudanças ainda não postas em stage
```bash
$ git reset <commit>
```
##### ...e preserve mudanças locais não commitadas
```bash
$ git reset --keep <commit>
```

