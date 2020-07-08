# _Merge_

É possível aplicar as mudanças de uma _branch_  à outra, num processo chamado de
_merge_.  Usa-se o comando `git merge`. Por exemplo, suponha que estejamos em
uma _branch_ `minha-branch`, e queiramos aplicar os _commits_ de `outra-branch`
em `minha-branch`:
```sh
git merge outra-branch
```

Um _merge_ aplica somente os _commits_ que as _branches_ não têm em comum.

# Conflitos

Por padrão, sempre que houver um conflito em um arquivo, o Git tenta resolver
mesclando as versões dos arquivos. No entanto, nem sempre é válida essa
mesclagem. Nesses casos, o Git falha em resolver o conflito, e intervenção
manual é requisitada.

Em cada arquivo, o que é comum entre as duas _branches_ é mantido. Onde há o
conflito, é indicado o quê pertence à _branch_ atual, e o que pertence à outra
_branch_. Assim:

```c
int main()
{
<<<<<<< HEAD
    vindo_da_minha_branch();
=======
    vindo_da_outra_branchl();
>>>>>>> outra-branch
    return 0;
}
```

Uma resolução de conflitos manual consiste em ir em cada um desses arquivos com
conflito, e, em cada conflito, escolher uma das versões, ou até mesmo
mesclá-las. Para descobrir-se quais arquivos precisam de interveção, basta
executar o comando `git status`. Após a resolução dos conflitos, e necessário
fazer um novo _commit_ contendo os arquivos corrigidos.

Existem, no entanto, ferramentas para auxiliar na resolução dos conflitos, como
o `kdiff`.


# Exemplo
Suponha o seguinte cenário, uma _branch_ "_master_" e uma "teste":
```
        master    teste
HEAD -> 80ba4e4  b49a7ed
           |        |
           |     4b12d0a
           |    /
           |   /
        ec49a96
           |
        3c97506
```

Suponha que queiramos aplicar as os dois _commits_ `4b12d0a` e `b49a7ed` à
_branch_ "_master_". Façamos o seguinte:
```sh
git merge teste
```
O resultado será o seguinte:

```
        master
HEAD -> 47d7959
           |   \
           |    \ teste
        80ba4e4  b49a7ed
           |        |
           |     4b12d0a
           |    /
           |   /
        ec49a96
           |
        3c97506
```

Note que a _branch_ "teste" continuará existindo. Podemos fazer um novo _commit_
nela:
```
master    teste
47d7959  0935946 <- HEAD
   |   \    |
   |    \   |
80ba4e4  b49a7ed
   |        |
   |     4b12d0a
   |    /
   |   /
ec49a96
   |
3c97506
```
