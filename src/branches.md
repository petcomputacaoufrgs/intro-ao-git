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
```
git checkout minha-branch
```

Para **criar e trocar** de branch ao mesmo tempo, use `git checkout` com a
_flag_ `-b`, assim:
```
git checkout -b minha-branch
```

Por padrão, a nova _branch_ começa do _commit_ atual (HEAD).

# Exemplo

Suponhamos um _commit_ `3c97506` seguido de um _commit_ `ec49a96`, ambos dentro
da branch `master`. A `HEAD` aponta para este último. Temos uma árvore assim:

```
master
ec49a96 <- HEAD
   |
3c97506
```

Após fazermos uma nova _branch_ "teste" (`git checkout -b teste`), e produzirmos
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

Se voltarmos para a _master_ (`git checkout master`), e produzirmos um novo
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

# Deletando Branches

Para deletar branches, existem duas formas. A primeira, a forma segura, requer
que você tenha feito _merge_ dessa branch em outra antes (será explicado nos
próximos dois capítulos). Basta passar a flag `-d` para o comando `git branch`,
junto ao nome da branch:
```
git branch -d minha-branch
```

Para forçar a deleção sem ter salvo a `branch` em outra, use `-D`:
```
git branch -D minha-branch
```