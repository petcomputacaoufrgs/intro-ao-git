# `git diff`

Para visualizar diferenças entre versões do projeto, é possível utilizar o
comando `git diff`. O comando exibe diferenças no seguinte formato: uma versão
é dada como versão mais antiga, a outra como mais nova, as linhas que a versão
mais nova introduziu são marcadas com um `+` e as que a versão mais nova removeu
são marcadas com um `-`. Para visualizar a diferença entre um _commit_ antigo
`e544ad4` e um _commit_ novo `d4b67d0`, basta executar:
```sh
git diff e544ad4 d4b67d0
```
Para sair do comando, basta digitar `q`.

Para visualizar a diferença apenas nos arquivos `main.c` e `vetor.c`, em relação
a esses mesmos _commits_, basta executar:
```sh
git diff e544ad4 d4b67d0 -- main.c vetor.c
```

Para visualizar a diferença entre algum _commit_ `e544ad4` e os arquivos que
você vê no diretório do projeto (_working tree_), basta executar:
```sh
git diff e544ad4
```

Para comparar duas _branches_ "_master_" e "desenvolvimento", basta executar:
```sh
git diff master desenvolvimento
```
