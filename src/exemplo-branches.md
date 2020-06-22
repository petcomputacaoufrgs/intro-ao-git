# Criando _Branches_

Suponha que temos mais um colega no time. Suponha que ele decidiu
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
git commit -m 'implementada exponenciação'
git push github exp
```

# A _Branch_ Do Colega

Agora suponha que trocamos de computador, que somos o colega no computador
dele. A _HEAD_ deve estar na "master" a partir de agora.

Para criar a nova _branch_, e ao mesmo tempo mudar para ela:
```sh
git checkout -b trig
```

O colega vai adicionar as operações trignonométricas que quer adicionar. Vamos
começar pelas três funções mais conhecidas: `sin`, `cos`, `tan`.

Arquivo `ops.h`:
```C
 #define OP_MUL_SYM "*"
 #define OP_DIV_SYM "/"
+#define OP_POW_SYM "sin"
+#define OP_EXP_SYM "cos"
+#define OP_EXP_SYM "tan"
 
 enum operation {
     op_add,
     op_sub,
     op_mul,
-    op_div
+    op_div,
+    op_sin,
+    op_cos,
+    op_tan
 };
```

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
+    case op_sin:
+        success = stack_pop(stack, &left);
+        if (success) {
+            stack_push(stack, sin(left));
+        }
+        break;
+    case op_cos:
+        success = stack_pop(stack, &left);
+        if (success) {
+            stack_push(stack, cos(left));
+        }
+        break;
+    case op_tan:
+        success = stack_pop(stack, &left);
+        if (success) {
+            stack_push(stack, tan(left));
+        }
+        break;
     }

     return success;
```

O colega vai ver se não ocorre algum erro de compilação (no Linux):
```sh
gcc -o ops.o -c ops.c
```
Perfeito, não ocorre.

O colega vai testar também (precisa de `-lm  para usar funções `math`):
```sh
gcc main.o parser.o stack.o ops.o -lm -o rpn-calc
```

TODO: fazer teste.

Funciona! Agora ele pode subir as modificações:

```sh
git add .
git status
git commit -m 'implementada trigonometria básica'
git push github trig
```

O colega vai adicionar trigonometria inversa também:

Arquivo `ops.h`:
```C
 #define OP_EXP_SYM "cos"
 #define OP_EXP_SYM "tan"
+#define OP_POW_SYM "arcsin"
+#define OP_EXP_SYM "arccos"
+#define OP_EXP_SYM "arctan"
     
 enum operation {
     op_add,
     op_sub,
     op_mul,
     op_div,
     op_sin,
     op_cos,
-    op_tan
+    op_tan,
+    op_arcsin,
+    op_arccos,
+    op_arctan
 };
```

Arquivo `ops.c`:
```C
 #include "ops.h"
+#include <math.h>

 int op_exec(enum operation op, struct stack **stack)
 {
...
             stack_push(stack, tan(left));
         }
         break;
+    case op_arcsin:
+        success = stack_pop(stack, &left);
+        if (success) {
+            stack_push(stack, asin(left));
+        }
+        break;
+    case op_arccos:
+        success = stack_pop(stack, &left);
+        if (success) {
+            stack_push(stack, acos(left));
+        }
+        break;
+    case op_arctan:
+        success = stack_pop(stack, &left);
+        if (success) {
+            stack_push(stack, atan(left));
+        }
+        break;
     }

     return success;
```

O colega vai ver se não ocorre algum erro de compilação (no Linux):
```sh
gcc -o ops.o -c ops.c
```
Perfeito, não ocorre.

O colega vai testar também (precisa de `-lm  para usar funções `math`):
```sh
gcc main.o parser.o stack.o ops.o -lm -o rpn-calc
```

TODO: fazer teste.

Funciona! Agora ele pode subir as modificações:

```sh
git add .
git status
git commit -m 'implementada trigonometria inversa'
git push github trig
```

O colega está pronto, e vai mandar as mudanças pra _branch_ "master". Primeiro,
ele vai trocar para ela.
```sh
git checkout master
```

Após isso, ele vai checar se o repositório local está atualizado.
```sh
git pull github master
```

TODO: colocar print.

Ele está atualizado. Ele vai executar o `merge`.

```sh
git merge trig
```

TODO: colocar print.

Não é necessário resolver conflitos. O colega vai publicar as mudanças.

```sh
git push github master
```

# Voltando Para Nosso Computador

Temos que estar na _branch_ "exp". Vamos fazer mais uma mudança, vamos
adicionar logaritmos.

Arquivo `ops.h`:
```C
 #define OP_POW_SYM "^"
 #define OP_EXP_SYM "exp"
+#define OP_LOG_SYM "log"
+#define OP_LN_SYM "ln"
 
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
             stack_push(stack, pow(left, right));
         }
         break;
+    case op_log:
+        success = stack_pop(stack, &right) && stack_pop(stack, &left);
+        if (success) {
+            stack_push(stack, log(right) / log(left));
+        }
+        break;
+    case op_ln:
+        success = stack_pop(stack, &left);
+        if (success) {
+            stack_push(stack, log(left));
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
git commit -m 'implementado logaritmo'
git push github exp
```
Já podemos fazer `merge`.
```sh
git checkout master
```

Agora, vamos ver se não estamos desatualizados:
```sh
git pull github master
```

TODO: colocar print.

Ok, estávamos desatualizados, mas baixamos as atualizações. É possível que tenhamos
que resolver algum conflito. Vamos ver:
```sh
git merge exp
```

TODO: colocar print.

E... deu conflito. Resolveremos no próximo capítulo.