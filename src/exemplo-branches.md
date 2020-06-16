# _Fazendo branches_

Suponha que temos mais um coleguinha no time. Suponha que ele decidiu
adicionar trigonometria. Suponha que nós decidimos adicionar exponenciação
e logaritmo. Para fazer tais tarefas, vamos criar mais duas _branches_, uma
chamada "trig", a outra chamada "exp".

# Nossa _Branch_

Para criá-la, e ao mesmo tempo mudar para ela:
```sh
git checkout -b exp
```

Vamos começar com exponenciação adicionando os identificadores das operações. Uma
exponenciação em qualquer base, e outra na base `e` (número de Euler). As linhas
marcadas com `-` no início serão excluídas, e as marcadas com `+` serão incluídas.

Arquivo `ops.h`:
```C
 #define OP_MUL_SYM "*"
 #define OP_DIV_SYM "/"
+#define OP_POW_SYM "^"
+#define OP_EXP_SYM "exp"
 
 enum operation {
     op_add,
     op_sub,
     op_mul,
-    op_div
+    op_div,
+    op_pow,
+    op_exp
 };
```

Depois, vamos implementar a execução dessas operações:

Arquivo `ops.c`:
```C
 #include "ops.h"
+#include <math.h>

 int op_exec(enum operation op, struct stack **stack)
 {
...
             stack_push(stack, left / right);
         }
         break;
+    case op_pow:
+        success = stack_pop(stack, &right) && stack_pop(stack, &left);
+        if (success) {
+            stack_push(stack, pow(left, right));
+        }
+        break;
+    case op_exp:
+        success = stack_pop(stack, &left);
+        if (success) {
+            stack_push(stack, exp(left));
+        }
+        break;
     }

     return success;
```

Vamos ver se não ocorre algum erro de compilação (no Linux):
```sh
gcc -o ops.o -c ops.c
```
Perfeito, não ocorre.

Vamos testar também (precisamos de `-lm  para usar funções `math`):
```sh
gcc main.o parser.o stack.o ops.o -lm -o rpn-calc
```

TODO: fazer teste.

Funciona! Agora podemos subir as modificações:

```sh
git add .
git status
git commit -m 'implementado exponenciação'
git push github exp
```
