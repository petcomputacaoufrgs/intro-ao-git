# Função _Main_

Vamos fazer uma função _main_ e juntar tudo! Vamos decompor a função _main_ em um
`switch-case` e uma outra função.

Arquivo `main.c`:
```C
#include "parser.h"
#include "stack.h"
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

enum result {
    result_ok,
    result_syntax_err,
    result_stack_err,
};

void show_usage(void);

enum result parse_and_exec();

int main(int argc, char const *argv[])
{
    char const *source = argv[1];
    char const *cursor = source;
    struct stack *stack = NULL;
    double result;
    enum result status;

    if (argc != 2) {
        show_usage();
        exit(1);
        abort();
    }

    status = parse_and_exec(&cursor, &stack);
    if (status == result_ok) {
        if (!stack_pop(&stack, &result)) {
            status = result_stack_err;
        }
    }

    switch (status) {
    case result_syntax_err:
        fprintf(stderr, "Syntax error near: \"%s\"\n", cursor);
        break;
    case result_stack_err:
        fprintf(stderr, "Stack error near: \"%s\"\n", cursor);
        break;
    case result_ok:
        printf("%lf\n", result);
        break;
    }

    stack_free(&stack);
    return status;
}

enum result parse_and_exec(char const **cursor, struct stack **stack)
{
    struct parser parser = { *cursor };
    struct token token;
    enum result status = result_ok;
    int end_of_input = 0;

    do {
        token = parse_token(&parser);
        switch (token.kind) {
        case token_num:
            stack_push(stack, token.data.num);
            break;
        case token_op:
            if (!op_exec(token.data.op, stack)) {
                status = result_stack_err;
                end_of_input = 1;
            }
            break;
        case token_end:
            end_of_input = 1;
            break;
        case token_error:
            status = result_syntax_err;
            end_of_input = 1;
            break;
        }
    } while (!end_of_input);

    *cursor = parser.cursor;

    return status;
}

void show_usage(void)
{
    fputs("Usage: rpn-calc 'expression'\n", stderr);
}
```

Vamos ver se não ocorre algum erro de compilação (no Linux):
```sh
gcc -o main.o -c main.c
```
Perfeito, não ocorre.

Agora, vamos ao _commit_:

```sh
git add .
git status
git commit -m 'implementado a função main'
git push github master
```

Vamos testar (no Linux):
```sh
gcc main.o parser.o stack.o ops.o -o rpn-calc
```

TODO: fazer o teste

Funciona!
