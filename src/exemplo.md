# Exemplo

Como um exemplo de projeto que use Git, vamos desenvolver uma calculadora
RPN e usaremos Git para versionar o projeto. O projeto desenvolvido pode
ser encontrado no endereço <https://github.com/petcomputacaoufrgs/rpn-calc>.

NOTA: neste exemplo, não usaremos `--set-upstream`, e escreveremos sempre
o nome das _branches_ em _pushes_ e _pulls_ por questões de clareza.

Uma calculadora RPN usa notação polonesa reversa, uma notação pósfixa. Por
exemplo, `3 + 2` em RPN é escrito `3 2 +`, enquanto `(5 + 4/3 - 1) * 2` é
escrito `5 4 3 / + 1 - 2 *`. Parentesis normalmente não são usados, mas a
expressão anterior pode ser lida como `((5 (4 3 /) +) 1 -) 2 *`. RPN funciona
através de uma pilha de operandos. Passo a passo da execução da expressão acima:

1. Estado Inicial
```sh
Expressão: 5 4 3 / + 1 - 2 *
Pilha: topo = fundo
```

2. Trazer `5` para a pilha
```sh
Expressão: 4 3 / + 1 - 2 *
Pilha: fundo = 5 = topo
```

3. Trazer `4` para a pilha
```sh
Expressão: 3 / + 1 - 2 *
Pilha: fundo = 5, 4 = topo
```

4. Trazer `3` para a pilha
```sh
Expressão: / + 1 - 2 *
Pilha: fundo = 5, 4, 3 = topo
```

5. Executar a operação `/` nos dois elementos mais ao topo da pilha.
```sh
Expressão: + 1 - 2 *
Pilha: fundo = 5, 1.3333... = topo
```

6. Executar a operação `+` nos dois elementos mais ao topo da pilha.
```sh
Expressão: 1 - 2 *
Pilha: fundo = 6.3333... = topo
```

7. Trazer `1` para a pilha
```sh
Expressão: - 2 *
Pilha: fundo = 6.3333..., 1 = topo
```

8. Executar a operação `-` nos dois elementos mais ao topo da pilha.
```sh
Expressão: 2 *
Pilha: fundo = 5.3333... = topo
```

9. Trazer `2` para a pilha
```sh
Expressão: *
Pilha: fundo = 5.3333..., 2 = topo
```

10. Executar a operação `*` nos dois elementos mais ao topo da pilha.
```sh
Expressão: vazia
Pilha: fundo = 10.6666... = topo
```

Resultado: `10.6666...`.
