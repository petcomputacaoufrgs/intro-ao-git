# Branches

Uma _branch_ é uma ramificação na linha do tempo do Git.

# Criando E Trocando De Branch

Existem várias formas de criar uma _branch_. Uma delas, usando o comando
`git branch`, que simplesmente cria uma _branch_ e não faz mais nada. Para criar
a _branch_ com o nome "minha-branch", use:
```sh
git branch minha-branch
```

Por padrão, você não vai estar na branch que criou.  Para trocar de branch use
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

Para **criar e trocar** de branch ao mesmo tempo, use `git checkout` com a
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
da branch `master`. A `_HEAD_` aponta para este último. Temos uma árvore assim:

```
master
ec49a96 <- _HEAD_
   |
3c97506
```

Após fazermos uma nova _branch_ "teste" (`git checkout -b teste`), e produzirmos
um novo _commit_ `4b12d0a` nela, temos a seguinte:

```
         teste
         4b12d0a <- _HEAD_
        /
master /
ec49a96
   |
3c97506
```

Se voltarmos para a _master_ (`git checkout master`), e produzirmos um novo
_commit_ `80ba4e4`, temos:

```
        master   teste
_HEAD_ -> 80ba4e4  4b12d0a
           |    /
           |   /
        ec49a96
           |
        3c97506
```

# Deletando Branches

Para deletar branches, existem duas formas. A primeira, a forma segura, requer
que você tenha feito _merge_ dessa branch em outra antes (será explicado nos
próximos dois capítulos). Basta passar a _flag_ `-d` para o comando `git branch`,
junto ao nome da branch:
```
git branch -d minha-branch
```

Para forçar a deleção sem ter salvo a `branch` em outra, use `-D`:
```
git branch -D minha-branch
```
