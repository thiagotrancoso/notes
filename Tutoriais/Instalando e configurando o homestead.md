# Índice

- [Importante](#importante)
- [Instalação e configuração](#Instalação-e-configuração)
- [Programas necessários](#Programas-necessários)
- [Download da box homestead vagrant](#Download-da-box-homestead-vagrant)
- [Clonar o repositório homestead](#Clonar-o-repositório-homestead)
- [Gerar os arquivos de configuração do homestead](#Gerar-os-arquivos-de-configuração-do-homestead)
- [Configurar o arquivo Homestead.yaml](#Configurar-o-arquivo-homesteadyaml)
- [Editando o arquivo Homestead.yaml após a inicialização da máquina virtual](#Editando-o-arquivo-Homesteadyaml-após-a-inicialização-da-máquina-virtual)
- [Configurar hostname no arquivo hosts do windows](#Configurar-hostname-no-arquivo-hosts-do-windows)
- [Iniciar o homestead](#Iniciar-o-homestead)
- [Acessar os projetos](#Acessar-os-projetos)
- [Acessar a máquina virtual via ssh](#Acessar-a-máquina-virtual-via-ssh)
- [Excluir a máquina virtual](#Excluir-a-máquina-virtual)
- [Conectando no banco de dados](#Conectando-no-banco-de-dados)
- [Configurar o comando homestead para gerenciar a máquina virtual](#Configurar-o-comando-homestead-para-gerenciar-a-máquina-virtual)

# Importante
- Tutorial feito no windows 10 pro.
- Todos os comandos neste tutorial serão executados usando o Git Bash.
- Algumas configurações serão exclusivas para o Git Bash.
- O simbolo `~` indica a pasta do usuário.

# Instalação e configuração
## Programas necessários
Instale os programas abaixo em seu pc.
- Virtual Box (https://www.virtualbox.org)
- Vagrant (https://www.vagrantup.com)
- Git (https://git-scm.com)

**Verificar a versão do vagrant**
```bash
vagrant -v
```

## Download da box homestead vagrant

<span  class="obs">**[OBS]** A `box` é a imagem da máquina virtual.</span>

Esse processo demora um pouco.
```bash
vagrant box add laravel/homestead
```

Aparecerá uma lista de softwares usados para vitualização.

Informe o número referente ao `VirtualBox`.

## Clonar o repositório homestead
**Clonar o repositório homestead para a pasta do usuário.**

```bash
git clone https://github.com/laravel/homestead.git ~/Homestead
```

**Fazer checkout para última versão estável do Homestead**
```bash
cd  ~/Homestead
git checkout release
```

## Gerar os arquivos de configuração do homestead

Os arquivos gerados serão colocados no diretório Homestead `~/Homestead`.
**Arquivos que serão gerados:**
- after.sh
- aliases
- Homestead.yaml

```php
// Entre na pasta do homestead
cd  ~/Homestead

// Execute o comando abaixo para gerar os arquivos
bash  init.sh
```

## Configurar o arquivo Homestead.yaml
Exemplo:

```yaml
#. Configurações da máquina virtual
ip:  "192.168.10.10"
memory:  1024
cpus:  1

#. Software de virtualização
provider:  virtualbox

#. Faz backup do banco quando exclui a máquina virtual
backup:  true

#. CONFIGURAR PASTAS COMPARTILHADAS
#. Certifique-se de criar as pastas no computador local antes de configurar as pastas compartilhadas
#. map => caminho da pasta no computador local
#. to => caminho da pasta no homestead
folders:
-  map:  D:\Projetos\primeiro
   to:  /home/vagrant/projetos/primeiro

-  map:  D:\Projetos\segundo
   to:  /home/vagrant/projetos/segundo

#. CONFIGURAR SITES NGINX
#. map => domínio a ser digitado no navegador
#. to => diretório público do projeto no homestead
sites:
    - map: primeiro.local
      to: /home/vagrant/projetos/primeiro/public

    - map: segundo.local
      to: /home/vagrant/projetos/segundo/public

#. Banco de dados que serão criados
databases:
    - primeiro
    - segundo

#. Olhar na documentação do laravel os recursos disponíveis, aqui você ativa ou desativa os recursos
features:
    - mariadb:  true

#. Redirecionamento de portas
#. send => porta na máquina host
#. to => porta na máquina virtual
ports:
    #. MariaDB
    - send: 3306
      to: 3306

    #. PostgreSQL
    - send: 5432
      to: 5432
```

## Editando o arquivo Homestead.yaml após a inicialização da máquina virtual

Se você alterou o arquivo de configuração `Homestead.yaml` com a máquina virtual ativa execute o comando abaixo.

Este comando irá atualizar as configurações da máquina virtual.

```bash
vagrant reload --provision
```

## Configurar hostname no arquivo hosts do windows

Abra o arquivo `hosts` em `C:\Windows\System32\drivers\etc` e adicione os hostnames dos seus projetos.

<span  class="obs">**[OBS]** Este arquivo precisa ser editado com permissão de administrador.</span>

Ex: Arquivo `hosts`.
```text
192.168.10.10 primeiro.test
192.168.10.10 segundo.test
192.168.10.10 terceiro.test
```

<span  class="obs">**[OBS]** **OBS:** O endereço IP listado acima é da máquina virtual definido no arquivo `Homestead.yaml`.</span>

## Iniciar o homestead
Ao iniciar a máquina virtual o Vagrant irá aplicar as configurações que estão no arquivo `Homestead.yaml`.

<span  class="obs">**[OBS]** A primeira inicialização da máquina virtual poderá demorar um pouco porque será criada a máquina virtual e aplicado toda a configuração.</span>

```php
// Entre na pasta do homestead
cd  ~/Homestead

// Inicie a máquina virtual
vagrant  up
```

## Acessar os projetos
Acesse os projetos usando o `hostname` configurado no arquivo `hosts`.

`Ex: http://primeiro.test`

## Acessar a máquina virtual via ssh

```php
// Entre na pasta do homestead
cd  ~/Homestead

// Conecte-se via ssh
vagrant  ssh
```

## Excluir a máquina virtual

<span  class="obs">**[OBS]** Se o backup automático estiver habilitado no arquivo `Homestead.yaml` então o homestead exportará seus bancos de dados para os diretórios `mysql_backup` e `postgres_backup` quando a máquina virtual for excluída.

Esses diretórios estarão na pasta do homestead `~/Homestead`.</span>

```php
// Entre na pasta do Homestead
cd  ~/Homestead

// Iniciar a máquina virtual
vagrant  up

// Excluir a máquina virtual
vagrant  destroy
```

# Conectando no banco de dados

<span  class="obs">**[OBS]** Sua aplicação deverá se conectar no banco de dados usando a porta configurada para máquina virtual.

Para se conectar no banco usando a máquina host, deverá usar a porta configurada para a máquina host.</span>

Dados necessários para conexão com o banco. O usuário e senha é definido pelo homestead.

```text
MySQL
IP: 127.0.0.1
Porta: {definida no arquivo Homestead.yaml}
Usuário: homestead
Senha: secret

MariaDB
IP: 127.0.0.1
Porta: {definida no arquivo Homestead.yaml}
Usuário: homestead
Senha: secret

PostgreSQL
IP: 127.0.0.1
Porta: {definida no arquivo Homestead.yaml}
Usuário: homestead
Senha: secret
```

# Configurar o comando homestead para gerenciar a máquina virtual

<span  class="obs">**[OBS]** Esta configuração é exclusiva para o Git Bash.</span>

Até o momento para gerenciar nossa máquina virtual precisavamos estar dentro da pasta do `Homestead`.

Vamos configurar para que possamos gerenciar a máquina virtual de qualquer lugar.

```php
// Entre na pasta do usuário
cd  ~

// Crie um arquivo .bash_profile
nano  .bash_profile
```

**Cole o código abaixo no arquivo criado**
```php
#. Alguns atalhos para facilitar a navegação e o acesso
alias  ..="cd .."
alias  vm="ssh vagrant@127.0.0.1 -p 2222"

#. Atalho Homestead
function  homestead() {
    ( cd  ~/Homestead  &&  vagrant $* )
}
```

<span  class="obs">**[OBS]** Reinicie o GitBash</span>

Agora você pode gerenciar a máquina virtual de qualquer lugar.

Exemplo:
```php
// Iniciar a máquina virtual
homestead  up

// Desligar a máquina virtual
homestead  halt

// Acessar a máquina virtual via ssh
homestead  ssh
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1ODM0MTg1MjVdfQ==
-->