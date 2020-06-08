# Implementando As Operações

Vamos definir as operações da nossa calculadora. No momento, vamos manter apenas
as quatro operações básicas da matemática (`+`, `-`, `/`, `*`). Vamos definir,
também, como executá-las, além do símbolo correspondente a cada operação. A
função de execução retorna se ouve sucesso. Começaremos com o cabeçalho:

Arquivo `ops.h`:
```C
#ifndef OPS_H
#define OPS_H

#include "stack.h"

#define OP_ADD_SYM "+"
#define OP_SUB_SYM "-"
#define OP_MUL_SYM "*"
#define OP_DIV_SYM "/"

enum operation {
    op_add,
    op_sub,
    op_mul,
    op_div
};

int op_exec(enum operation op, struct stack **stack);

#endif
```

Vamos implementar a execução das operações:

Arquivo `ops.c`:
```C
#include "ops.h"

int op_exec(enum operation op, struct stack **stack)
{
    double left, right;
    int success;

    switch (op) {
    case op_add:
        success = stack_pop(stack, &right) && stack_pop(stack, &left);
        if (success) {
            stack_push(stack, left + right);
        }
        break;
    case op_sub:
        success = stack_pop(stack, &right) && stack_pop(stack, &left);
        if (success) {
            stack_push(stack, left - right);
        }
        break;
    case op_mul:
        success = stack_pop(stack, &right) && stack_pop(stack, &left);
        if (success) {
            stack_push(stack, left * right);
        }
        break;
    case op_div:
        success = stack_pop(stack, &right) && stack_pop(stack, &left);
        if (success) {
            stack_push(stack, left / right);
        }
        break;
    }

    return success;
}
```

Vamos ver se não ocorre algum erro de compilação (no Linux):
```sh
gcc -o ops.o -c ops.c
```
Perfeito, não ocorre.

Agora, vamos ao _commit_:

```sh
git add .
git status
git commit -m 'implementadas operações básicas'
git push github master
```
