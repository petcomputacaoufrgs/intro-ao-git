# O Que É O Git?

Se eu fosse resumir a resposta, ela seria: git é uma ferramenta distribuída de controle de versionamento de _software_. As alterações de uma versão do _software_ são
chamadas "_commit_". Os arquivos que contêm as versões são chamados
"repositório".

# O Que É Controle De Versionamento?

Controle de versionamento de um _software_ é o registro das alterações dos
arquivos de um _software_ ao longo do seu desenvolvimento; é o registro da
história de um _software_. No entanto, é bom notar que versionamento normalmente
não envolve grandes saltos entre versões. Ao invés disso, registram-se novas
versões em pequenas mudanças, pequenos saltos, como adicionar um arquivo ou
reescrever uma função.

# O Que Significa Ser Distribuído?

Versionadores costumam trabalhar com o conceito de "repositórios". Um
repositório contém o _software_ em questão e sua história. Alguns, como o SVN,
centralizam um _software_ em um repositório remoto (servidor). Isso significa que
toda nova versão tem de passar pelo servidor. Este **não** é o caso do Git. O
Git possibilita repositórios locais. Isto é, você pode ter toda história do
_software_ na sua máquina, fazer suas próprias mudanças, compartilhar com vários
repositórios remotos, etc.

# Git vs. GitHub

Às vezes a distinção entre Git e GitHub é confusa, mas é a seguinte: Git é o
programa que faz o versionamento em si e administra repositórios; GitHub é um
serviço que hospeda repositórios Git em um servidor. Existem outros serviços
semelhantes, como o GitLab e o BitBucket.
