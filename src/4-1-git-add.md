# git add

Para adicionar arquivos modificados ou não-rastreados à _staging area_, existe
o comando `git add`. A sintaxe do commando é:

Adicionando um arquivo:
```sh
git add arquivo1
```

Adicionando múltiplos arquivos:
```sh
git add arquivo2 arquivo3 arquivo4
```

Adicionando diretórios inteiros:
```sh
git add src/
```

É uma padrão comum adicionar todo diretório atual (lembre-se de que `.`
significa "o diretório atual").
```sh
git add .
```

Há também a flag `-a` que adiciona todas as modificações, do projeto inteiro.
```sh
git add -a
```

Na prática, `git add .` e `git add -a` se comportam da mesma forma. Os dois só
diferem quando o diretório atual não é a raiz do projeto, como por exemplo, o
diretório `./src/`.
