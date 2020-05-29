# git commit

Para registrar uma nova versão, utiliza-se o comando `git commit`. Somente as
mudanças com estado "_staged_" farão parte do _commit_. Sintaxe do comando:
```sh
git commit -m 'mensagem do commit'
```

A mensagem do commit deve ser um resumo ou uma identificação das mudanças
introduzidas. É recomendado que a mensagem do commit não tenha muito mais do que
50 caracteres. É possível inserir a mensagem usando um editor de texto (por
padrão no Linux, é o `vi`), basta ocultar a opção `-m` e a mensagem, assim:
```sh
git commit
```

A todo _commit_, o Git associa um número chamado de _hash_. O número sempre é
apresentado na sua forma hexadecimal, como por exemplo:
`80ba4e49ee1fc346ee4934bdd2b4581e61b5c5fa`.
