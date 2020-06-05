
# OBSERVAÇÕES
- Host utilizado é a Hostinger.
- Este tutorial leva em consideração projetos feito em Laravel.

#### Como funciona
É criado um container docker dentro do GitLab, os arquivos da branch específica estarão neste container e este container fará o upload do projeto para o servidor.

# SERVIDOR
#### Exemplo de estrutura de pastas no servidor
```bash
/home
    /usuario
        /domains
            /projeto1.com.br
                /public_html #. redireciona para a pasta onde está o projeto
            /projeto2.com.br
                /public_html #. redireciona para a pasta onde está o projeto
        /projetos
            /projeto1
                /backup
                /beta #. projeto laravel nessa pasta
                    /public
                /www #. projeto laravel nessa pasta
                    /public
            /projeto2
                /backup
                /beta #. projeto laravel nessa pasta
                    /public
                /www #. projeto laravel nessa pasta
                    /public
```

#### Criar um link simbólico
```bash
#. ln -s <caminho/destino> <caminho/origem>
ln -s ~/projetos/projeto1/www/public ~/domains
```

# GITLAB
## Branch
Neste exemplo usaremos 3 branchs.
- **`desenvolvedor`**
  - Branch de desenvolvimento
- **`beta`** (marcar como protegido)
  - Branch para testar o projeto antes de ir pra produção
- **`master`** (marcar como protegido)
  - Branch com projeto em produção

## Definindo variáveis
É possível definir variáveis na configuração do GitLab e usar elas no arquivo `.gitlab-ci.yml`.

Para definir vai em: `Configurações > CI/CD > Variáveis`

Neste exemplo foi definido as variáveis abaixo:
- SSH_HOST
- SSH_USER
- SSH_PASS
- SSH_PORT

> Marque as variáveis como `protegido` dessa forma elas só estarão disponíveis em branchs protegidas.

## Arquivo de configuração
Este arquivo faz toda mágica acontecer e deve ficar na pasta raiz do projeto.

O nome do arquivo deve ser exatamente esse: `.gitlab-ci.yml`

> Atente-se a fazer as alterações de acordo com os seus dados do servidor.

**Exemplo:**
```yml
variables:
  # Define o timezone padrão
  TIMEZONE: "America/Sao_Paulo"

  # Define diretórios no servidor
  HOST_DIR: "~/projetos/blog"
  HOST_DIR_WWW: "~/projetos/blog/www"
  HOST_DIR_BETA: "~/projetos/blog/beta"
  HOST_DIR_BACKUP: "~/projetos/blog/backup"

image: php:7.3

# Configura o servidor
before_script:
  - cat /etc/[A-Za-z]*[_-][rv]e[lr]*
  - apt-get update
  - apt-get install -y zip unzip sshpass
  - eval $(ssh-agent -s)
  - mkdir -p ~/.ssh
  - chmod 700 ~/.ssh
  - echo -e "Host *\n\tStrictHostKeyChecking no\n\n" > ~/.ssh/config

# Deploy em ambiente de testes
deploy_beta:
  stage: deploy
  only:
    - beta
  artifacts:
    paths:
      - ./
  script:
    # Compacta o projeto em arquivo zip
    - zip -r projeto.zip ./ -x ./.git\* ./scripts\*

    # Move o arquivo zip para o diretório "beta"
    - sshpass -p $SSH_PASS scp -P $SSH_PORT projeto.zip $SSH_USER@$SSH_HOST:$HOST_DIR_BETA

    # Descompacta o arquivo zip substituindo os arquivos existentes
    - sshpass -p $SSH_PASS ssh -p $SSH_PORT $SSH_USER@$SSH_HOST "cd $HOST_DIR_BETA && unzip -o projeto.zip"

    # Exclui o arquivo zip
    - sshpass -p $SSH_PASS ssh -p $SSH_PORT $SSH_USER@$SSH_HOST "rm -rf $HOST_DIR_BETA/projeto.zip"

    # Instalar as dependências do projeto
    - sshpass -p $SSH_PASS ssh -p $SSH_PORT $SSH_USER@$SSH_HOST "cd $HOST_DIR_BETA && composer install --no-dev"

    # Executa as migrations
    - sshpass -p $SSH_PASS ssh -p $SSH_PORT $SSH_USER@$SSH_HOST "cd $HOST_DIR_BETA && php artisan migrate"

# Deploy em ambiente de produção
deploy_production:
  stage: deploy
  only:
    - master
  artifacts:
    paths:
      - ./
  script:
    # Compacta a NOVA_VERSAO
    - zip -r projeto.zip ./ -x ./.git\* ./scripts\*

    # Compacta a VERSAO_ATUAL na pasta "www"
    - sshpass -p $SSH_PASS ssh -p $SSH_PORT $SSH_USER@$SSH_HOST "cd $HOST_DIR_WWW && zip -r backup_$(date +%Y-%m-%d_%H-%M-%S).zip ./"

    # Move a VERSAO_ATUAL para a pasta "backup"
    - sshpass -p $SSH_PASS ssh -p $SSH_PORT $SSH_USER@$SSH_HOST "cd $HOST_DIR_WWW && mv backup* $HOST_DIR_BACKUP"

    # Move a NOVA_VERSAO a pasta "www"
    - sshpass -p $SSH_PASS scp -P $SSH_PORT projeto.zip $SSH_USER@$SSH_HOST:$HOST_DIR_WWW

    # Descompacta a NOVA_VERSAO substituindo os arquivos existentes
    - sshpass -p $SSH_PASS ssh -p $SSH_PORT $SSH_USER@$SSH_HOST "cd $HOST_DIR_WWW && unzip -o projeto.zip"

    # Exclui a NOVA_VERSAO compactada
    - sshpass -p $SSH_PASS ssh -p $SSH_PORT $SSH_USER@$SSH_HOST "rm -rf $HOST_DIR_WWW/projeto.zip"
    
    # Instala as dependências do projeto
    - sshpass -p $SSH_PASS ssh -p $SSH_PORT $SSH_USER@$SSH_HOST "cd $HOST_DIR_WWW && composer install --no-dev"

    # Executa as migrations
    - sshpass -p $SSH_PASS ssh -p $SSH_PORT $SSH_USER@$SSH_HOST "cd $HOST_DIR_WWW && php artisan migrate"
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MjEzNjg5MjZdfQ==
-->