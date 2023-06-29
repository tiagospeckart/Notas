
---
título: Boas Práticas para Commits 
criado: 2023-05-07 
tags: [git, github, guia] 
status_nota: done 
publicar: true
---

# Diretrizes para mensagens de commit

```
Resumo curto (72 caracteres ou menos)  

Texto explicativo mais detalhado. Limite-o a 72 caracteres. A linha em branco separando o resumo do corpo é essencial (a menos que você omita completamente o corpo).  Escreva sua mensagem de commit no imperativo: "Corrigir bug" e não "Bug corrigido" ou "Corrige bug". Esta convenção é consistente com as mensagens de commit geradas por comandos como git merge e git revert.  Outros parágrafos vêm após linhas em branco.  
- Bullet points são aceitáveis, também. 
- Geralmente, um hífen ou asterisco é usado para o bullet, seguido por um   espaço único. Use uma indentação pendente.
```

## Exemplo de uma mensagem de commit

```
Adicione suporte ao agendador para filtro de arquitetura de CPU

Em um ambiente misto de…
```

### Uma linha de assunto de commit git bem formada deve sempre ser capaz de completar a seguinte frase

Se aplicado, este commit `<sua linha de assunto aqui>`

## Regras para um ótimo estilo de mensagem de commit

- Separe o assunto do corpo com uma linha em branco
- Não termine a linha de assunto com um ponto
- Capitalize a linha de assunto e cada parágrafo
- Use o modo imperativo na linha de assunto
- Limite as linhas a 72 caracteres
- Use o corpo para explicar o que e por que você fez algo. Na maioria dos casos, você pode deixar de fora os detalhes sobre como uma mudança foi feita.

### Especifique o tipo de commit

- feat: um novo recurso que você está adicionando a um aplicativo específico
- fix: correção de um bug
- style: recurso e atualizações relacionadas ao estilo
- refactor: refatoração de uma seção específica do código
- test: tudo relacionado a testes
- docs: tudo relacionado à documentação
- chore: manutenção regular do código

### Informações em mensagens de commit

- Descreva por que uma mudança está sendo feita.
- Como ela resolve o problema?
- Quais efeitos a correção tem?
- Não presumir que o revisor entenda qual era o problema original.
- Não presumir que o código é autoexplicativo ou autodocumentado.
- Leia a mensagem do commit para ver se ela sugere uma estrutura de código aprimorada.
- A primeira linha do commit é a mais importante.
- Descreva quaisquer limitações do código atual.
- Não inclua comentários específicos do conjunto de correções.

Detalhes para cada ponto e exemplos de boas mensagens de commit podem ser encontrados em [https://wiki.openstack.org/wiki/GitCommitMessages#Information_in_commit_messages](https://wiki.openstack.org/wiki/GitCommitMessages#Information_in_commit_messages)

### Referências em mensagens de commit

Se o commit se refere a um problema, adicione essas informações ao cabeçalho ou ao corpo da mensagem do commit. Por exemplo, a plataforma web do GitHub converte automaticamente os ids dos problemas (por exemplo, #123) em links que referem-se ao problema relacionado. Para rastreadores de problemas como o Jira, existem plugins que também convertem tickets do Jira, como o [Jirafy](https://chrome.google.com/webstore/detail/jirafy/npldkpkhkmpnfhpmeoahhakbgcldplbj).

No cabeçalho:

```shell
[#123] Referência ao problema do GitHub…
```

```objectivec
CAT-123 Referência ao ticket do Jira com identificador do projeto CAT…
```

No corpo:

```less
… Corrige #123, #124
```

# Fontes

[FreeCodeCamp - Como escrever boas mensagens de commit: um guia prático do Git](https://www.freecodecamp.org/portuguese/news/como-escrever-boas-mensagens-de-commit-um-guia-pratico-do-git/)
[A Note about Git Messages](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html) [https://wiki.openstack.org/wiki/GitCommitMessages](https://wiki.openstack.org/wiki/GitCommitMessages) 
[Chris Beams - Git Commit](http://chris.beams.io/posts/git-commit/)






