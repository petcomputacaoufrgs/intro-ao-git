# `git pull` E `git push`

Para "puxar" mudanças de um repositório remoto, existe o `git pull`, e para
"empurar" mudanças a um repositório remoto, existe o `git push`.

# `git push`

Para mandar suas mudanças a um remoto salvo como `origin` numa _branch_
`main`, use:
```sh
git push origin main
```

**Lembre-se**: o GitHub usa `main` como a _branch_ padrão, não `master`, por
isso você precisa renomear a `master` para `main` antes de enviar ao GitHub.

Você pode omitir a _branch_ se na primeira vez você utilizar a flag
`--set-upstream` ou `-u'. Assim:

```
git push origin --set-upstream main
```
ou
```sh
git push origin -u main
```

Nos _pushes_ subsequentes, basta executar:

```sh
git push
```

O comando, no entanto, pode falhar pelo fato de você não ter seu repositório
local atualizado com novas mudanças do remoto. Nesse caso, você terá de executar
o comando `git pull` antes, resolver um _merge_, e só então poderá executar
`git push`. Veja abaixo como executar `git pull`.

# `git pull`

Semelhantemente, para receber mudanças de um repositório remoto salvo como
`origin` numa _branch_ `main`, use:
```sh
git pull origin main
```

Tome cuidado para que a _HEAD_ esteja apontando para a mesma _branch_.

Além disso, note que, se seu repositório local tiver novos _commits_, e o remoto
também tiver novos _commits_, divergindo a respeito da história da _branch_,
você terá de resolver um _merge_.  

Você pode omitir a _branch_ se na primeira vez você utilizar a flag
`--set-upstream`, tal como no comando `git push` (mas sem `-u`). Assim:

```
git pull origin --set-upstream main
```

Nos _pulls_ subsequentes, basta executar:

```sh
git pull
```

# _Tags_ Também Podem Ser Movimentadas

Suponha que você tenha executado:
```sh
git tag v0.3.5
```

Para mandar essa _tag_ para o remoto `origin`, execute:
```
git push origin v0.3.5
```
