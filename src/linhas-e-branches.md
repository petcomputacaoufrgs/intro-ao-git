# Linhas do Tempo E _Branches_

No Git, os _commits_ são arranjados em uma linha do tempo. Por padrão, essa
linha do tempo é linear, mas o Git também permite expressar bifurcações na linha
do tempo. Para isso, existe o conceito de "_branch_" (literalmente "galho",
"ramo").

Por padrão, a primeira branch do repositório se chama `master`. Ao fazer o
primeiro _commit_, essa _branch_ é criada. Esses diferentes "galhos" na linha do
tempo, podem eventualmente juntar-se novamente, no que chamamos de _merge_
(literalmente "união" ou "mescla"). É uma estratégia comum fazer-se várias
_branches_ com o objetivo de uní-las com a `master` eventualmente.

Note que apesar da _branch_ se chamar `master` pelo Git, no GitHub (serviço de
hospedagem de repositórios Git), normalmente se usa `main` como _branch_ padrão.
Você verá mais adiante qe pode renomear sua `master` para `main` com o seguinte
comando:
```shell
git branch -m master main
```
