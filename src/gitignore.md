# `.gitignore`

No Git, é possível especificar arquivos para serem ignorados. Isto é, estes
arquivos não são incluídos em futuras versões do _software_, por mais que você
use `git add` neles. A especificação ocorre num arquivo chamado de `.gitignore`.
Para ignorar um arquivo `senha-secreta.txt`, basta adicionar o nome desse
arquivo ao `.gitignore`. Para ignorar todos os arquivos terminados em `.mp3`,
basta usar um asterisco seguido da extensão (`*.mp3`).

Portanto, nesse cenário hipotético, o arquivo `.gitignore` se pareceria assim:
```
/senha-secreta.txt
*.mp3
```
