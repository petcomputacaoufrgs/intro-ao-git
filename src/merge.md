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
