## Configuração do projeto (Linux)

### Instalação e configuração inicial

Habilitar plataforma do puppet no apt (gerenciador de pacotes)

    wget https://apt.puppet.com/puppet7-release-focal.deb
    dpkg -i <>.db
    apt update
    apt upgrade

Instalar puppet server (Após habilitar plataforma puppet)

    apt install puppetserver

Iniciar servidor puppet

    sudo systemctl start puppetserver
    exec bash (ou restarte o bash manualmente)
    systemctl status puppet (valide sua ativação)

    **Configurações adicionais** : https://puppet.com/docs/puppet/7/server/install_from_packages.html

Instalar puppet agent

    sudo apt-get install puppet-agent
    source /etc/profile.d/puppet-agent.sh
    export PATH=/opt/puppetlabs/bin:$PATH

**Documentação** : https://puppet.com/docs/puppet/7/installing_and_upgrading.html

<hr>

### Gerenciar ambientes

Para a gestão de ambientes é necessário haver um repositório com o git inicializado
Obs: Cada branch existente será considerada um ambiente puppet e é obrigatória a existência de uma branch nomeada *production*

Localização dos ambientes:  /etc/puppetlabs/code/environments

Arquivos criados:

- environment.conf
- Puppetfile

**Documentação** : https://puppet.com/docs/pe/2019.0/control_repo.html

### Gerenciar módulos

Instalar um módulo

*docker* :
    
    puppet module install puppetlabs-docker
        Notice: Preparing to install into /home/user/.puppetlabs/etc/code/modules ...
        Notice: Created target directory /home/user/.puppetlabs/etc/code/modules
        Notice: Downloading from https://forgeapi.puppet.com ...
        Notice: Installing -- do not interrupt ...
        /home/user/.puppetlabs/etc/code/modules
            └─┬ puppetlabs-docker (v5.0.0)
            ├── puppetlabs-apt (v9.0.0)
            ├─┬ puppetlabs-powershell (v5.1.0)
            │ └── puppetlabs-pwshlib (v0.10.2)
            ├── puppetlabs-reboot (v4.2.0)
            └── puppetlabs-stdlib (v8.4.0)
