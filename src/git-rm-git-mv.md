# `git rm` E `git mv`

Às vezes o Git não é tão inteligente e não sabe diferenciar o caso de:
- Você reescreveu um arquivo vs. você removeu o arquivo e criou um novo com
  mesmo nome;
- Você renomeou um arquivo vs. você removeu o arquivo e criou outro parecido.

Para resolver isso, existem os comandos `git rm` e `git mv`.

# `git rm`

O comando `git rm` registra no repositório que você removeu o arquivo, de tal
forma que o Git não considerará que você reescreveu o arquivo ou renomeou.
Exemplo, para remover o arquivo `main.c`:

```sh
git rm main.c
```

# `git mv`

O comando `git mv` registra no repositório que você renomeou o arquivo, de tal
forma que o Git não considerará que você removeu arquivo. Exemplo, para renomear
o arquivo `main.c` de tal forma que o nome seja `main.py`:

```sh
git mv main.c main.py
```
