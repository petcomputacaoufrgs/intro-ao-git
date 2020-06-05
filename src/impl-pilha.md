# Implementando Uma Pilha

Como o nosso avaliador de expressões precisa de uma pilha para avaliar as
expressões, vamos primeiro implementar uma pilha. Primeiro, criaremos o projeto:

```sh
mkdir rpn-calc
cd rpn-calc
git init
```
Pronto. Projeto inicializado.

# Cabeçalho C

Agora vamos fazer um cabeçalho da linguagem C. Nossa pilha vai guardar `double`,
já que é o que a calculadora precisa. Vamos declarar duas funções básicas de
pilhas: `push` e `pop`. Elas vão receber um ponteiro duplo, mas não se assuste,
o ponteiro de dentro representa a pilha em si, que pode ser `NULL`, e o ponteiro
de fora serve para modificarmos o endereço do ponteiro de dentro, e não pode ser
`NULL`.

Arquivo `stack.h`:
```C
#ifndef STACK_H
#define STACK_H

typedef double stack_data;

struct stack {
    stack_data data;
    struct stack *next;
};

void stack_push(struct stack **stack, stack_data data);

int stack_pop(struct stack **stack, stack_data *data);

#endif
```

Agora, vamos salvar nossa ideia de pilha em um _commit_.

```sh
git add .
git status
git commit -m 'ideia de stack adicionada'
```

Mas hmmmm, talvez fosse interessante salvar esse projeto em um serviço como o
GitHub. Por isso, eu criei um repositório remoto com a URL
<https://github.com/petcomputacaoufrgs/rpn-calc>. No repositório do GitHub, já
tem uma licença e um arquivo de `README`. Se você utilizar um remoto, lembre de
substituir a URL por uma adequada. Vamos salvar esse remoto:

```sh
git remote add origin https://github.com/petcomputacaoufrgs/rpn-calc
```

Agora vamos executar um `push`.

```sh
git push origin master
```

TODO: adicionar imagem com o erro.

Oopsss... Eu criei o repositório remoto com licença e `README`. Primeiro vamos
ter que executar `git pull`.

```sh
git pull origin master
```

TODO: adicionar imagem com o erro.

Oopsss de novo...Esse erro aconteceu porque as histórias dos repositórios não
têm conexão. Basta usar a _flag_ `--allow-unrelated-histories`.

```sh
git pull origin master --allow-unrelated-histories
```

Pronto, agora podemos executar `git push` tranquilamente.
```sh
git push origin master
```

# Arquivo de Implementação C

Agora, vamos implementar a pilha.

Arquivo `stack.c`:

```c
#include "stack.h"
#include <stdlib.h>

void stack_push(struct stack **stack, stack_data data)
{
    struct stack *new_node = malloc(sizeof(struct stack));

    if (new_node == NULL) {
        abort();
    }

    new_node->data = data;
    new_node->next = *stack;
    *stack = new_node;
}

int stack_pop(struct stack **stack, stack_data *data)
{
    int success = 0;
    struct stack *node_ptr = *stack;

    if (node_ptr != NULL) {
        success = 1;
        *stack = node_ptr->next;
 
        if (data != NULL) {
            *data = node_ptr->data;
        }

        free(node_ptr);
    }

    return success;
}
```

Agora vamos fazer um _commit_.
```sh
git add .
git status
git commit -m 'implementação da stack'
```

E publicar a mudança:
```sh
git push origin master
```
