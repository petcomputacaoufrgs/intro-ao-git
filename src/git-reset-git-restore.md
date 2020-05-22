# git reset E git restore

Para o caso de ser necessário tirar uma mudança do estado _staged_, ou até mesmo
voltar ao estado do commit atual (HEAD), é possível usar os comandos `git reset`
e `git restore`.

# `git restore`

Esse comando restaura os arquivos que estão visiveis (working tree) para serem
idênticos aos do commit atual (HEAD). Para restaurar os arquivos `main.c` e
`vetor.c` por exemplo:
```sh
git restore -- main.c vetor.c
```

# `git reset`

Esse comando é semelhante ao `git restore`, mas tem mais variações além de ser
mais fácil de fazer algo errado.
