﻿## :brazil: Ansible Playbook: Colocar Ubuntu no Domínio (playbook modular) [PT-BR]

Este repositório contém um playbook modular para adicionar uma máquina Ubuntu a um domínio Active Directory. O playbook executa uma série de tarefas, incluindo a configuração do hostname, criação de um usuário local, instalação de pacotes necessários, configuração de arquivos de configuração e a junção da máquina ao domínio.

## Requisitos

- Ansible 2.9 ou superior
- Ubuntu 18.04 ou superior
- Acesso a um domínio Active Directory

## Estrutura de Diretório
```bash
ubuntu_domain_modular/
├── ubuntu_domain.yml
├── group_vars/
│   └── linux/
│       ├── change_hostname.yml
│       ├── local_user.yml
│       ├── install_packages.yml
│       └── domain_join.yml
└── roles/
    ├── change_hostname/
    │   └── tasks/
    │       └── main.yml
    ├── local_user/
    │   └── tasks/
    │       └── main.yml
    ├── install_packages/
    │   └── tasks/
    │       └── main.yml
    └── domain_join/
        ├── meta/
        │   └── main.yml
        ├── tasks/
        │   └── main.yml
        ├── handlers/
        │   └── main.yml
        └── templates/
            ├── krb5.conf.j2
            └── sssd.conf.j2
```
### Descrição dos Arquivos

-   **ubuntu_domain.yml**: O arquivo principal do playbook que orquestra as tarefas e funções.

-   **group_vars/**: Diretório contendo arquivos de variáveis específicas do ambiente.

    -   `change_hostname.yml`: Variáveis para a alteração do hostname.
    -   `local_user.yml`: Variáveis para a criação de um usuário local.
    -   `install_packages.yml`: Variáveis para a instalação de pacotes.
    -   `domain_join.yml`: Variáveis para a junção ao domínio.
-   **roles/**: Diretório contendo tarefas, handlers e templates específicos de cada função.

    -   **change_hostname/**:
        -   `tasks/main.yml`: Arquivo de tarefas para a alteração do hostname da máquina.
    -   **local_user/**:
        -   `tasks/main.yml`: Arquivo de tarefas para a criação de um usuário local.
    -   **install_packages/**:
        -   `tasks/main.yml`: Arquivo de tarefas para a instalação dos pacotes necessários.
    -   **domain_join/**:
        -   `meta/main.yml`: Dependências da função.
        -   `tasks/main.yml`: Arquivo de tarefas para junção ao domínio e configuração.
        -   `handlers/main.yml`: Handlers para reinício de serviços.
        -   **templates/**:
            -   `krb5.conf.j2`: Template para a configuração do Kerberos.
            -   `sssd.conf.j2`: Template para a configuração do SSSD.


## Estrutura do Playbook

1. **Alteração do Hostname**: Atualiza o hostname da máquina.
2. **Criação de Usuário Local**: Adiciona um novo usuário local.
3. **Instalação de Pacotes**: Instala pacotes necessários para a integração com o AD.
4. **Configuração do `krb5.conf`**: Configura o arquivo de configuração Kerberos.
5. **Atualização do PAM**: Atualiza as configurações do PAM.
6. **Junção ao Domínio**: Realiza a junção da máquina ao domínio Active Directory.
7. **Configuração do `sssd.conf`**: Configura o SSSD para autenticação.
8. **Reinicialização do Serviço SSSD**: Reinicia o serviço SSSD.
9. **Reinicialização da Máquina**: Reinicia a máquina para aplicar todas as mudanças.

## Instruções de Uso

### Passo 1: Clonar o Repositório

Clone o repositório para sua máquina local:

```bash
git clone https://github.com/luizcosta2191/Ubuntu_domain_playbook.git
cd Ubuntu_domain-playbook/Ubuntu_domain_modular
```

### Passo 2: Configurar Variáveis

Edite os arquivos em `group_vars/linux/` com as informações específicas do seu ambiente:

- change_hostname.yml
  ```yaml
  hostname: "hostname"
  ```
- local_user.yml
  ```yaml
  user_local: "local machine user"
  password: "local machine user's password"
  ```
- domain_join.yml
  ```yaml
  domain_upper: "uppercase domain address"
  domain_lower: "lowercase domain address"
  admin_user: "Active Directory admin user"
  admin_pass: "Active Directory admin password"
  domain_component: "domain component"
  ```

### Passo 3: Proteger Variáveis Sensíveis

Use o Ansible Vault para proteger os arquivos de variáveis:

```bash
ansible-vault encrypt group_vars/linux/*.yml
```

### Passo 4: Executar o Playbook

Execute o playbook com o comando:

```bash
ansible-playbook -i hosts ubuntu_domain.yml --ask-vault-pass
```

### Passo 5: Verificar

Após a execução, verifique se a máquina foi corretamente adicionada ao domínio e se todas as configurações foram aplicadas.

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e enviar pull requests.

# :us: Ansible Playbook: Adding Ubuntu to a Domain (modular playbook) [English]

This repository contains a modular playbook for adding an Ubuntu machine to an Active Directory domain. The playbook performs a series of tasks, including configuring the hostname, creating a local user, installing necessary packages, configuring configuration files, and joining the machine to the domain.

## Requirements
- Ansible 2.9 or higher
- Ubuntu 18.04 or higher
- Access to an Active Directory domain

## Directory Structure
```bash
ubuntu_domain_modular/
├── ubuntu_domain.yml
├── group_vars/
│   └── linux/
│       ├── change_hostname.yml
│       ├── local_user.yml
│       ├── install_packages.yml
│       └── domain_join.yml
└── roles/
    ├── change_hostname/
    │   └── tasks/
    │       └── main.yml
    ├── local_user/
    │   └── tasks/
    │       └── main.yml
    ├── install_packages/
    │   └── tasks/
    │       └── main.yml
    └── domain_join/
        ├── meta/
        │   └── main.yml
        ├── tasks/
        │   └── main.yml
        ├── handlers/
        │   └── main.yml
        └── templates/
            ├── krb5.conf.j2
            └── sssd.conf.j2
```
### File Descriptions

-   **ubuntu_domain.yml**: The main playbook file that orchestrates the tasks and roles.

-   **group_vars/**: Directory containing variable files specific to the environment.

    -   `change_hostname.yml`: Variables for changing the hostname.
    -   `local_user.yml`: Variables for creating a local user.
    -   `install_packages.yml`: Variables for package installation.
    -   `domain_join.yml`: Variables for joining the domain.
-   **roles/**: Directory containing role-specific tasks, handlers, and templates.

    -   **change_hostname/**:
        -   `tasks/main.yml`: Task file for changing the machine's hostname.
    -   **local_user/**:
        -   `tasks/main.yml`: Task file for creating a local user.
    -   **install_packages/**:
        -   `tasks/main.yml`: Task file for installing necessary packages.
    -   **domain_join/**:
        -   `meta/main.yml`: Role dependencies.
        -   `tasks/main.yml`: Task file for domain join and configuration.
        -   `handlers/main.yml`: Handlers for service restarts.
        -   **templates/**:
            -   `krb5.conf.j2`: Template for Kerberos configuration.
            -   `sssd.conf.j2`: Template for SSSD configuration.

## Playbook Structure
- **Hostname Change**: Updates the machine's hostname.
- **Local User Creation**: Adds a new local user.
- **Package Installation**: Installs packages needed for AD integration.
- **krb5.conf Configuration**: Configures the Kerberos configuration file.
- **PAM Update**: Updates PAM configurations.
- **Domain Join**: Joins the machine to the Active Directory domain.
- **sssd.conf Configuration**: Configures SSSD for authentication.
- **SSSD Service Restart**: Restarts the SSSD service.
- **Machine Reboot**: Reboots the machine to apply all changes.

## Usage Instructions

### Step 1: Clone the Repository

Clone the repository to your local machine:

```bash
git clone https://github.com/luizcosta2191/Ubuntu_domain_playbook.git
cd Ubuntu_domain-playbook/Ubuntu_domain_modular
  ```

### Step 2: Configure Variables

Edit the files in `group_vars/linux/` with the specific information for your environment:
-   change_hostname.yml
  ```yaml
  hostname: "hostname"
  ```
-   local_user.yml

  ```yaml
user_local: "local machine user"
password: "local machine user's password"
```

-   domain_join.yml

 ```yaml   
 domain_upper: "uppercase domain address"
 domain_lower: "lowercase domain address"
 admin_user: "Active Directory admin user"
 admin_pass: "Active Directory admin password"
 domain_component: "domain component"
 ```
### Step 3: Secure Sensitive Variables

Use Ansible Vault to secure the variable files:

    ansible-vault encrypt group_vars/linux/*.yml

### Step 4: Run the Playbook

Run the playbook with the command:

    ansible-playbook -i hosts ubuntu_domain.yml --ask-vault-pass

### Step 5: Verify

After execution, verify that the machine has been correctly added to the domain and that all configurations have been applied.

## Contributions

Contributions are welcome! Feel free to open issues and submit pull requests.

