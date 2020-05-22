# git commit

Para registrar uma nova versão, utiliza-se o comando `git commit`. Somente as
mudanças com estado "_staged_" farão parte do _commit_. Sintaxe do comando:
```sh
git commit -m 'mensagem do commit'
```

A mensagem do commit deve ser um resumo ou uma identificação das mudanças
introduzidas. É recomendado que a mensagem do commit não tenha muito mais do que
50 caracteres. É possível inserir a mensagem usando um editor de texto, basta
ocultar a opção `-m` e a mensagem, assim:
```sh
git commit
```
