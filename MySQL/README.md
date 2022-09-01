# MySQL Installation

## Pré-requisitos

| Ferramenta  | Versão  |
|---|---|
|Docker|20.10.17|
|Docker Compose|1.29.2|

## Configurando o ambiente

Crie um arquivo de configuração .env conforme o exemplo em anexo. As variáveis podem ser configuradas conforme as informações abaixo:

| Variavel  | Descrição  | Obrigatória? |
|---|---|---|
|  MYSQL_ROOT_PASSWORD | Esta variável é obrigatória e especifica a senha que será definida para a conta de superusuário root do MySQL. | :heavy_check_mark: |
| MYSQL_DATABASE  | Permite especificar o nome de um banco de dados a ser criado na inicialização da imagem. Se um usuário/senha foi fornecido, então esse usuário terá acesso de superusuário (correspondente a GRANT ALL) a este banco de dados. |
| MYSQL_USER  | Usada em conjunto com MYSQL_PASSWORD para criar um novo usuário e definir a senha desse usuário. Este usuário receberá permissões de superusuário para o banco de dados especificado pela variável MYSQL_DATABASE. | |
| MYSQL_PASSWORD  | Usada em conjunto com MYSQL_PASSWORD para criar um novo usuário e definir a senha desse usuário. Este usuário receberá permissões de superusuário para o banco de dados especificado pela variável MYSQL_DATABASE.  | |
|  MYSQL_ALLOW_EMPTY_PASSWORD | Defina como um valor não vazio, como ex. *yes*, para permitir que o contêiner seja iniciado com uma senha em branco para o usuário root. NOTA: Definir essa variável como yes não é recomendado a menos que você realmente saiba o que está fazendo, pois isso deixará sua instância do MySQL completamente desprotegida, permitindo que qualquer pessoa obtenha acesso completo de superusuário.
  | |
| MYSQL_RANDOM_ROOT_PASSWORD  | Defina como um valor não vazio, como ex. *yes*, para gerar uma senha inicial aleatória para o usuário root. A senha de root gerada será impressa em stdout (GENERATED ROOT PASSWORD: \*\*\*).  | |
|  MYSQL_ONETIME_PASSWORD | Define o usuário root (não o usuário especificado em MYSQL_USER) como expirado assim que o init for concluído, forçando uma alteração de senha no primeiro login. Qualquer valor não nulo ativará essa configuração. NOTA: Este recurso é suportado apenas no MySQL 5.6+. Usar esta opção no MySQL 5.5 lançará um erro apropriado durante a inicialização.  | |

>Observe que não há necessidade de usar este mecanismo para criar o superusuário root, esse usuário é criado por padrão com a senha especificada pela variável MYSQL_ROOT_PASSWORD.

## Como executar

Em um terminal, execute o comando abaixo:

```bash
docker-compose up -d
```

## Referências

- [Dockerhub](https://hub.docker.com/_/mysql)