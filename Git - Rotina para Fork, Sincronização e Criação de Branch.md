---
title: Git - Rotina para Fork, Sincronização e Criação de Branch
created: 2023-06-29
aliases: 
tags: [git, github, fork, upstream]
note_status: working
publish: true
---
Ao trabalhar com o repositório de outra pessoa, geralmente realizamos um `fork`, sincronizamos com o repositório original (*upstream*) e criamos *branches* para realizar nossas mudanças. Aqui estão os comandos Git para executar essas operações.

# Glossário

## O que é um Upstream?

"Upstream" é um termo usado no Git para se referir ao repositório original a partir do qual um fork foi criado. Em outras palavras, se você fizer um fork de um repositório, o repositório de onde o fork foi feito é considerado o "upstream".

Na prática, quando você faz um fork de um repositório, você cria uma cópia do repositório que é exclusiva para você. Esta cópia é totalmente desconectada do repositório original, ou seja, mudanças no repositório original não aparecem automaticamente na sua cópia (o fork).

Ao adicionar o repositório original como um "upstream" remoto, você cria uma conexão entre o seu fork e o repositório original. Isso permite que você puxe (pull) as alterações do repositório original para o seu fork, mantendo-o sincronizado com as atualizações que acontecem no upstream.

Por exemplo, suponha que você tenha feito um fork de um repositório para contribuir com um projeto de código aberto. Enquanto você está trabalhando nas suas mudanças, outras pessoas podem estar fazendo suas próprias contribuições para o projeto. Adicionando o repositório original como um "upstream", você pode puxar essas alterações para o seu próprio fork e manter seu código atualizado com o projeto como um todo.

# Rotina

## Adicionando um fork + upstream

### Fork um repositório

O Fork de um repositório é realizado na interface do GitHub. Na página do repositório que deseja fazer o fork, clique no botão "Fork" (canto direito superior).

### Clone o repositório para o qual você fez fork

Depois de realizar o fork, você precisa clonar o repositório para a sua máquina local.

```bash
$ git clone ssh:seu_usuário@domain.com:seu_repo_fork.git
```

### Adicione o repositório original como "upstream"

```bash
$ cd seu_repo_fork # mude para a pasta do seu fork
$ git remote add upstream ssh:usuário_original@domain.com:repositório_original.git
```

Lembre-se de substituir `https://github.com/usuario_original/repo_original.git` pela URL do repositório original que você deseja adicionar.

### Verifique se o upstream foi adicionado corretamente

```bash
$ git remote -v
```

Você deve ver tanto o "origin" (que aponta para o seu fork) quanto o "upstream" (que aponta para o repositório original).

## Sincronize seu fork com o repositório upstream

Antes de iniciar seu trabalho, é uma boa ideia sincronizar seu fork com o repositório original (upstream) para obter as atualizações mais recentes.

```bash
$ git checkout main # ir para a branch main
$ git fetch upstream # pega a lista de mudanças que tem no remoto
$ git merge upstream/main # une as mudanças remotas com seu repositório local
$ git push origin main # manda a nova versão para seu fork no github
```

### Crie um novo branch para suas mudanças

Agora você está pronto para começar a trabalhar. Crie um novo branch para suas mudanças.

```bash
$ git checkout -b seu-novo-branch
```

Agora você pode fazer suas alterações, commitá-las e, em seguida, empurrar seu branch para o seu fork.

```bash
$ git push origin seu-novo-branch
```

### Se estiver contribuindo em um projeto open source

Quando suas alterações estiverem prontas para serem revisadas, você pode abrir um pull request no GitHub a partir do seu branch de trabalho para o branch principal do repositório original.