# AUTOMAÇÃO DE CONFIGURAÇÃO E INSTALAÇÃO DE SOFTWARE NOS LABORATÓRIOS DE INFORMÁTICA COM ANSIBLE
Este projeto contém rotinas úteis para executar comandos remotamente e de forma automatizada tanto nos hosts Linux quanto Windows instalados nos
laboratórios de informática.

# Funcionalidades

- [x] Configurações e comandos básicos de sistema usando WinRM(ver lista de módulos [Windows](https://docs.ansible.com/ansible/2.9/modules/list_of_windows_modules.html#windows-modules) e [Linux](https://docs.ansible.com/ansible/2.9/modules/list_of_all_modules.html))
- [x] Instalação do Chocolatey para implementação de pacotes/aplicativos no Windows
- [x] Cria e configura usuário de gerência (ansible_user) e envia chave ssh pro host(somente Linux)

# Organização das roles
A ideia é organizarmos as roles conforme os perfis de uso dos PCs. Isso pode ser atualizado com o tempo.

**roles/basico** - contém aplicativos e configurações básicas genéricas, aplicáveis a todos os perfis de máquinas
**roles/basico_academico** - contém aplicativos e configurações básicas gerais aplicáveis a laboratórios e PCs de professor
...

# Hosts

No arquivo de inventário na raiz do projeto, chamado [hosts](hosts_exemplo) onde podemos definir os IPs e variáveis (usuário, senha, métodos de conexão, etc).

Importante: **A versão de produção desse arquivo não deve ser exposta**

> Se for fazer push do projeto pro Gitlab, certtifique-se de que este arquivo conste no .gitignore

# Contribuição
Para colaborar incluindo novos roles(funcionalidades) a esse projeto, siga os [seguintes passos](docs/contributing.md).