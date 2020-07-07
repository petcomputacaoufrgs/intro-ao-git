# Instalação E Configuração

# Windows

Acesse o link <https://git-scm.com/download/win>.

# Linux

Você já tenha o Git instalado. Você pode verificar com o seguinte comando:
```sh
git --version
```
Se o git tiver instalado, o comando te dirá a versão do Git. Se não tiver, o
recomendado é instalar pelo gerenciador de pacotes do seu sistema.

## Arch Linux, Manjaro, etc
```sh
sudo pacman -S git
```

## Debian, Ubuntu, etc
```sh
sudo apt-get install git
```

## Fedora, RedHat Linux, etc
```sh
sudo dnf install git
```

Etc...

# Configuração

A configuração obrigatória do Git é simples: basta dar nome e email.

Para definir seu nome como "João da Silva", basta executar:
```sh
git config user.name 'João da Silva'
```

Para definir seu email como "jdsilva@mail.com", basta executar:
```sh
git config user.email 'jdsilva@mail.com'
```

Para verificar o nome definido:
```sh
# Vai escrever na tela 'João da Silva'
git config user.name
```

Para verificar o email definido:
```sh
# Vai escrever na tela 'jdsilva@mail.com'
git config user.email
```

Dependendo da versão do Git, você pode precisar executar o seguinte comando
também:

```sh
git config --global pull.rebase false
```
