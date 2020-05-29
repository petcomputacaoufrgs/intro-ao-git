# `git tag`

É possível rotular _commits_ usando aqueles rótulos bem conhecidos para se
referir a versões de software como `v0.1.3`, `v1.0`, v`2.5.3`, etc. O comando
usado para tal é o `git tag`. Para marcar o _commit_ atual como `v1.0`, basta
executar:
```sh
git tag v1.0
```

Para marcar outro _commit_ `8b37825` como `v1.3`, basta executar:
```sh
git tag v1.3 8b37825
```

Para visualizar todas as _tags_:
```sh
git tag
```

Para deletar uma _tag_ v2.0 (sem deletar o _commit_):
```sh
git tag -d v2.0
```

É importante notar que _tags_ em geral marcam pontos do _software_ onde ele está
"pronto" para ser usado. Normalmente, são _commits_ específicos que são
marcados, não todos.
