# Inicializando (E Com `.gitignore`)

Primeiro, criaremos o projeto:

```sh
mkdir rpn-calc
cd rpn-calc
git init
```
Pronto. Projeto inicializado. Depois, faremos um arquivo de `.gitignore` para
ignorar arquivos binários.

Arquivo `.gitignore`:
```
*.o
/rpn-calc
```

Dessa forma, todos arquivos objetos (`.o`) e o executável que nomearemos
`rpn-calc` serão ignorados.
