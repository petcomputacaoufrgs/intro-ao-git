# _Fazendo branches_

O nosso cenário é o seguinte: nosso código não funciona e vamos criar uma
_branch_ "bugfix" para implementar a resolução do problema. Além disso, um
colega entrou para um time e vai implementar mais operações, em paralelo.
Para isso, ele vai criar uma _branch_ "mais-ops".

# Nossa _Branch_

Vamos criar e trocar de _branch_:

```sh
git checkout -b bugfix
```

O problema está no arquivo `parser.c`. Esta é a modificação que devemos fazer,
na linha 36:
```C
     if (strncmp(parser->cursor, test, size) == 0) {
         ch = parser->cursor[size];
-        if (is_whitespace(ch)) {
+        if (ch == 0 || is_whitespace(ch)) {
             success = 1;
             parser->cursor += size;
```

Vamos ver se não ocorre algum erro de compilação (no Linux):
```sh
gcc -o parser.o -c parser.c
```
Perfeito, não ocorre.

Agora, vamos ao _commit_:

```sh
git add .
git status
git commit -m 'corrigido bug que fazia operador no fim falhar'
git push github bugfix
```

# A _Branch_ Do Coleguinha

Primeiro, criaremos e trocaremos de _branch_:
```sh
git checkout -b mais-ops
```

