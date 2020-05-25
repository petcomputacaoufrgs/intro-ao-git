# Navegando Entre Commits

É possível, no Git, mudar o commit o HEAD para um commit passado. Esse é mais um
uso do comando `git checkout`.

Pàra navegar até o commit `fae6c2e`, use:
```sh
git checkout fae6c2e
```

No entanto, ao fazer isso, você entrará no "_detached HEAD state_" (estado de
_HEAD_ descolado). Isso significa que você a _HEAD_ não aponta para uma
_branch_, mas para um _commit_ específico. O problema disso é: se você for fazer
um novo _commit_, ele não pertencerá a nenhuma _branch_. Portanto, não use
`git checkout` com o intuito de alterar a linha do tempo a partir de um _commit_
passado. Use-o somente para alternar entre _branches_ ou para visualizar os
arquivos de um _commit_ antigo.

Semelhantemente, é possível usar `git reset`.
```sh
git reset fae6c2e
```

Mas isso também entra no "_detached HEAD state_".

Para sair do "_detached HEAD state_", faça _checkout_ para uma _branch_.
```sh
git checkout master
```
