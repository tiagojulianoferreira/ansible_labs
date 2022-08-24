# ANSIBLE - Conceitos básicos

> Ansible é uma linguagem de automação simples que pode descrever perfeitamente uma infraestrutura de aplicativos de TI. É fácil de aprender, autodocumentado e não requer um diploma de graduação em ciência da computação para ser lido. A automação não deve ser mais complexa do que as tarefas que está substituindo. (Red Hat)

O uso correto do Ansible alcança uma característica fundamental chamada **idempotência**, em que é garantido que uma determinada rotina, ainda que executada mais de uma vez, não altere o estado de uma infraestrutura sem a real necissidade.

## Possibilidades com Ansible

- Implantação do aplicativo

- Gerenciamento de configurações

- Orquestração de fluxo de trabalho

- Orquestrar o ciclo de vida do aplicativo

- Elimina tarefas repetitivas

- Reduz erros causadas por falhas humanas

## Sem agente
O Ansible não requer instalação de agentes específicos nos hosts alvos pois usa protcolos de conexão remota segura como **OpenSSH** e **WinRM**.


**Playbook** - 

**Tasks** - 

**Roles** - as roles facilitam o reuso de código na medida em que separam tasks, handlers, defaults, templates em estruturas de diretórios específicas para cada parte da implementação. Assim, podem ser evocadas a partir de playbooks mais genéricos. Exemplo: podemos reaproveitar a pilha de servidores LAMP em diversas aplicações como Wordpress, Moodle, GLPI, entre outras que dependam de Apache, PHP, Mysql.

**Handlers** - Útil principalmente para restart de serviços, sendo que pode ser chamado a partir de uma notificação (_notify_), ou seja, sem precisar ser executado como uma task em sequência.

Exemplo de definição de um handler:

```shell
 handlers:
  - name: restart mariadb
    service: 
      name: mariadb
      state: restarted

```
Exemplo de notificação que requisita a execução do handler:
```shell
- name: Install mariadb and python dependencies
  ansible.builtin.apt:
   pkg:
    - mariadb-server
    - python3-mysqldb
    - python3-pymysql
   state: present
  notify: restart mariadb

```
**Defaults** - define valores default que são carregados caso o usuário não especifique. Útil para definição de variáveis de aplicação, por exemplo.
**Meta** - útil para definir as dependências das tarefas/roles. Exemplo: podemos definir uma role de instalação do Apache como dependẽncia para a implementação do Wordpress.
