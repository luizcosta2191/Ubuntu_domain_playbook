## :brazil: **Ansible Playbooks para adicionar o Ubuntu ao domínio [PT-BR]**
Este repositório contém dois playbooks que demonstram como realizar as seguintes tarefas em sistemas Ubuntu:

- Alterar o hostname
- Criar um usuário local
- Adicionar a uma domínio

Esses playbooks foram desenvolvidos para demonstrar habilidades e conhecimento em Ansible, servindo tanto como portfólio pessoal quanto como material de estudo para outros interessados em aprender Ansible.

### Playbook Monolítico
O playbook monolítico realiza todas as etapas em um único arquivo, além de um arquivo de variáveis separado (vars_ubuntu_domain.yml). Este é um exemplo simples e direto de como utilizar Ansible para automatizar as tarefas mencionadas. A estrutura é a seguinte:

    ├── ubuntu_domain.yml
    └── vars_ubuntu_domain.yml

### Playbook Modular
O playbook modular utiliza a estrutura recomendada pelo Ansible, separando a lógica em roles, handlers, templates, etc. Isso facilita a manutenção e a reutilização de código. A estrutura é a seguinte:

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

### Contribuição
Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests para melhorias, correções ou novas funcionalidades.

##  :us: Ansible Playbooks to Add Ubuntu to a Domain [English]

This repository contains two playbooks that demonstrate how to perform the following tasks on Ubuntu systems:

- Change the hostname
- Create a local user
- Add to a domain

These playbooks were developed to showcase skills and knowledge in Ansible, serving both as a personal portfolio and as study material for others interested in learning Ansible.

### Monolithic Playbook
The monolithic playbook performs all steps in a single file, along with a separate variables file (vars_ubuntu_domain.yml). This is a simple and straightforward example of how to use Ansible to automate the mentioned tasks. The structure is as follows:

    ├── ubuntu_domain.yml
    └── vars_ubuntu_domain.yml

### Modular Playbook
The modular playbook uses the recommended Ansible structure, separating the logic into roles, handlers, templates, etc. This facilitates maintenance and code reuse. The structure is as follows:

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

### Contribution
Contributions are welcome! Feel free to open issues and pull requests for improvements, fixes, or new features.
