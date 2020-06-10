# Linhas do Tempo E Branches

No Git, os _commit_ s são arranjados em uma linha do tempo. Por padrão, essa
linha do tempo é linear, mas o Git também permite expressar bifurcações na linha
do tempo. Para isso, existe o conceito de "_branch_" (literalmente "galho",
"ramo").

Por padrão, a primeira branch do repositório se chama "_master_". Ao fazer o
primeiro commit, essa _branch_ é criada. Esses diferentes "galhos" na linha do
tempo, podem eventualmente juntar-se novamente, no que chamamos de _merge_
(literalmente "união" ou "mescla"). É uma estratégia comum fazer-se várias
_branches_ com o objetivo de uní-las com a _master_ eventualmente.