# Branches

Uma _branch_ é uma ramificação na linha do tempo do Git.

# Criando E Trocando De Branch

Existem várias formas de criar uma _branch_. Uma delas, usando o comando
`git branch`, simplesmente cria uma _branch_ e não faz mais nada. Para criar
a _branch_ com o nome `minha-branch`, use:
```sh
git branch minha-branch
```

Por padrão, você não vai estar na _branch_ que criou.  Para trocar de _branch_ use
`git checkout`, assim:
```sh
git checkout minha-branch
```

É possível, também, utilizar `git reset` para trocar de _branch_.
```sh
git reset minha-branch
```

A _flag_ `--soft` troca de _branch_ preservando alterações feitas mas que não
entraram no _commit_:
```sh
git reset --soft minha-branch
```

Para **criar e trocar** de _branch_ ao mesmo tempo, use `git checkout` com a
_flag_ `-b`, assim:
```sh
git checkout -b minha-branch
```

Por padrão, a nova _branch_ começa do _commit_ atual (_HEAD_). É possível criar
uma branch a partir de um _commit_, digamos, `0935946`.
```sh
git branch minha-branch 0935946
```

# Exemplo

Suponhamos um _commit_ `3c97506` seguido de um _commit_ `ec49a96`, ambos dentro
da branch `master`. A _HEAD_ aponta para este último. Temos uma árvore assim:

```
master
ec49a96 <- HEAD
   |
3c97506
```

Após fazermos uma nova _branch_ `teste` (`git checkout -b teste`), e produzirmos
um novo _commit_ `4b12d0a` nela, temos a seguinte:

```
         teste
         4b12d0a <- HEAD
        /
master /
ec49a96
   |
3c97506
```

Se voltarmos para a `master` (`git checkout master`), e produzirmos um novo
_commit_ `80ba4e4`, temos:

```
        master   teste
HEAD -> 80ba4e4  4b12d0a
           |    /
           |   /
        ec49a96
           |
        3c97506
```

# Renomeando _Branches_

Para renomear _branches_, basta usar a _flag_ `-m`, passando em seguida o nome
da _branch_ a ser renomeada, e depois o novo nome da _branch_.
```
git branch -m nome-antigo nome-novo
```

Se a _branch_ alvo for a _branch_ atual, o nome dela pode ser omitida, e
somente o novo nome da _branch_ atual precisa ser informado:
```
git branch -m nome-novo
```

Portanto, podemos renomear a `master` para `main` da seguinte forma:
```
git branch -m master main
```

# Deletando _Branches_

Para deletar _branches_, existem duas formas. A primeira, a forma segura, requer
que você tenha feito _merge_ dessa _branch_ em outra antes (será explicado nos
próximos dois capítulos). Basta passar a _flag_ `-d` para o comando `git branch`,
junto ao nome da branch:
```
git branch -d minha-branch
```

Para forçar a deleção sem ter salvo a `branch` em outra, use `-D`:
```
git branch -D minha-branch
```
