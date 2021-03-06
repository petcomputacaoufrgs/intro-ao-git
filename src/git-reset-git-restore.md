# `git reset` E `git restore`

Para o caso de ser necessário tirar uma mudança do estado _staged_, ou até mesmo
voltar ao estado do _commit_ atual (_HEAD_), é possível usar os comandos `git reset`
e `git restore`.

# `git restore`

O comando `git restore` restaura os arquivos que estão visiveis (_working tree_)
para serem idênticos aos do _commit_ atual (_HEAD_). Para restaurar os arquivos
`main.c` e `vetor.c`, por exemplo:
```sh
git restore -- main.c vetor.c
```

O comando `git restore`, no entanto, não está presente em versões desatualizadas
do Git, por isso, você pode precisar usar o comando `git reset`.

# `git reset`

O comando `git reset` é semelhante ao `git restore`, mas tem mais variações
além de ser mais fácil de fazer algo errado. Se não for usada nenhuma _flag_, ou
a _flag_ `--mixed` for usada, os arquivos que estavam _staged_ vão deixar de ser
_staged_, mas não serão alterados. Por exemplo, para restaurar todos os
arquivos:
```sh
git reset --mixed HEAD
# ou simplesmente
git reset HEAD
```

Com a _flag_ `--hard`, o comportamento é semelhante ao de `git restore`, exceto
que arquivos novos não serão deletados.
```sh
git reset --hard HEAD
```

Há ainda a _flag_ `--soft`, que será explicado mais a frente, pois envolve um uso
do comando ainda não explicado.
