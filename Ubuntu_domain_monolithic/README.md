## ﻿🇧🇷 Ansible Playbook: Colocar Ubuntu no Domínio (playbook monolítico) [PT-BR]

Este repositório contém um playbook Ansible para adicionar uma máquina Ubuntu a um domínio Active Directory. O playbook executa uma série de tarefas, incluindo a configuração do hostname, instalação de pacotes necessários, configuração de arquivos de configuração, e a junção da máquina ao domínio.



**Requisitos:**

-   Ansible 2.9 ou superior

-   Ubuntu 18.04 ou superior

-   Acesso a um domínio Active Directory






## Estrutura do Playbook

-   **Alteração do Hostname:** Atualiza o hostname da máquina.
-   **Criação de Usuário Local:** Adiciona um novo usuário local.
-   **Instalação de Pacotes:** Instala pacotes necessários para a integração com o AD.
-   **Configuração do krb5.conf:** Configura o arquivo de configuração Kerberos.
-   **Atualização do PAM:** Atualiza as configurações do PAM.
-   **Junção ao Domínio:** Realiza a junção da máquina ao domínio Active Directory.
-   **Configuração do sssd.conf:** Configura o SSSD para autenticação.
-   **Reinicialização do Serviço SSSD:** Reinicia o serviço SSSD.
-   **Reinicialização da Máquina:** Reinicia a máquina para aplicar todas as mudanças.

### Arquivos:

-   **ubuntu_domain.yml**: O arquivo principal do playbook.

-   **vars_ubuntu_domain.yml**: Arquivo de variáveis contendo informações sensíveis e específicas do ambiente.


## Instruções de Uso



### Passo 1: Clonar o Repositório


Clone o repositório para sua máquina local:



    git clone https://github.com/luizcosta2191/Ubuntu_domain_playbook.git
    cd Ubuntu_domain-playbook/Ubuntu_domain_monolithic


### Passo 2: Configurar Variáveis


Edite o arquivo vars_ubuntu_domain.yml com as informações específicas do seu ambiente:


```yaml
    hostname: "hostname"
    user_local: "usuário local da máquina"
    password: "senha do usuário local"
    domain_upper: "endereço do dominio em maiúsculo"
    domain_lower: "endereço do dominio em minúsculo"
    admin_user: "usuário admin do Active Directory"
    admin_pass: "senha do admin do Active Directory"
    domain_component: "componente de domínio"
```

### Passo 3: Proteger Variáveis Sensíveis


Use o Ansible Vault para proteger o arquivo de variáveis:



    ansible-vault encrypt vars_ubuntu_domain.yml



### Passo 4: Executar o Playbook


Execute o playbook com o comando:



    ansible-playbook -i hosts ubuntu_domain.yml --ask-vault-pass



### Passo 5: Verificar


Após a execução, verifique se a máquina foi corretamente adicionada ao domínio e se todas as configurações foram aplicadas.



## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e enviar pull requests.


🇺🇸 Ansible Playbook: Join Ubuntu to Domain (monolithic playbook) [English]
-
This repository contains an Ansible playbook for adding an Ubuntu machine to an Active Directory domain. The playbook performs a series of tasks including configuring the hostname, installing necessary packages, configuring configuration files, and joining the machine to the domain.

### Requirements

 - Ansible 2.9 or higher
 - Ubuntu 18.04 or higher
 - Access to an Active Directory domain


## Playbook Structure

- **Change Hostname:** Updates the machine's hostname.
- **Create Local User:** Adds a new local user.
- **Install Packages:** Installs necessary packages for AD integration.
- **Configure krb5.conf:** Configures the Kerberos configuration file.
- **Update PAM:** Updates PAM configuration.
- **Join Domain:** Joins the machine to the Active Directory domain.
- **Configure sssd.conf:** Configures SSSD for authentication.
- **Restart SSSD Service:** Restarts the SSSD service.
- **Reboot Machine:** Reboots the machine to apply all changes.


### File Descriptions:

 - **ubuntu_domain.yml**: The main playbook file.
 - **vars_ubuntu_domain.yml**: Variable file containing sensitive and environment-specific information.



## Usage Instructions

### Step 1: Clone the Repository

Clone the repository to your local machine:

    git clone https://github.com/luizcosta2191/Ubuntu_domain_playbook.git
    cd Ubuntu_domain-playbook/Ubuntu_domain_monolithic



### Step 2: Configure Variables

Edit the vars_ubuntu_domain.yml file with your environment-specific information:


```yaml
    hostname: "hostname"
    user_local: "local machine user"
    password: "local machine user's password"
    domain_upper: "uppercase domain address"
    domain_lower: "lowercase domain address"
    admin_user: "Active Directory admin user"
    admin_pass: "Active Directory admin password"
    domain_component: "domain component"
```


### Step 3: Protect Sensitive Variables

Use Ansible Vault to encrypt the variable file:



    ansible-vault encrypt vars_ubuntu_domain.yml



### Step 4: Run the Playbook

Run the playbook with the following command:



    ansible-playbook -i hosts ubuntu_domain.yml --ask-vault-pass



### Step 5: Verify

After execution, verify that the machine has been successfully added to the domain and all configurations have been applied.


## Contributions

Contributions are welcome! Feel free to open issues and submit pull requests.
