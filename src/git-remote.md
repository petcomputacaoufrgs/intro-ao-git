# `git remote`

Para gerenciar comunicação repositórios remotos, você precisa salvar no seu
repositório local referências para os repositórios remotos. Para fazer isso,
existe o comando `git remote`. Para adicionar um remoto, com nome "origin" e URL
<https://github.com/petcomputacaoufrgs/intro-ao-git.git>:
```sh
git remote add origin https://github.com/petcomputacaoufrgs/intro-ao-git.git
```

Por padrão, quando você usa `git clone`, ele cria um remoto chamado "origin".

Para visualizar os remotos salvos, basta executar:
```sh
git remote
```

Para visualizar a URL de um remoto chamado "origin", basta executar:
```sh
git remote get-url origin
```

Para remover um remoto chamado "origin", basta executar:
```sh
git remote remove origin
```

Para redefinir a URL de um remoto chamado "origin" com a URL
<https://github.com/fulanodasilva/intro-ao-git.git>, basta executar:
```sh
git remote set-url origin https://github.com/fulanodasilva/intro-ao-git.git
```
