# Sobre o Sistema

Sistema base elaborado por mim para um start mais rápido no desenvolvimento de um projeto laravel

## Proposta do Sistema

Simples sistema de posts realizados pelos usuários. Contém as funcionalidades:

- Cadastro, Visualização, Edição e Remoção de Usuários;
- Cadastro, Visualização, Edição e Remoção de Posts dos Usuários;
- Sistema de Restrição de Acesso com cadastro de perfis e permissões;
- Sistema de Auditoria das atualizações das informações dos dados;
- Área de gestão de Usuários, Regras de Acesso e Auditoria


### Configurações Iniciais

- `docker-compose up -d`    **( Cria o container do docker )**
- `docker-compose run --rm composer install` **( Instala a dependecia do php via composer )**
- `cp .env.example .env` **( Copia e cria o arquivo de configuracao do laravel )**
- `docker-compose run --rm artisan key:generate` **( Gera a chave do sistema )**

O arquivo .env deve ser configurado nesse momento para que o comando migrate funcione.
É fundamental que a configuração esteja nesta ordem.
e posteriormente os dados de acesso ao banco do sistema. O env.example já esta neste formato só 
aguardando os dados.

### ACESSO AO BANCO LOCAL

DB_CONNECTION=pgsql
DB_HOST=postgres
DB_PORT=5432
DB_DATABASE=crud_db
DB_USERNAME=postgres
DB_PASSWORD=crud_password

## Configurações Frontend, dependencias e permissões 


- `docker-compose run --rm npm install` **( Instala as dependencias do frontEnd )**
- `docker-compose run --rm npm run dev` **( Compilacao das libs do frontEnd )**

- `docker-compose run --rm artisan migrate --seed` **( Cria as tabelas do banco de dados e popula ele )**

- `docker-compose run --rm composer update` **( Atualiza a dependecia do php via composer )**

- `docker-compose run --rm artisan storage:link` **( Cria o link nas pastas storage )**

- `docker-compose run --rm app chmod -R 775 bootstrap storage` **( Mudo a permisao )**
- `docker-compose run --rm app chown -R www-data.www-data bootstrap storage` **( Coloco o nginx para se dono da pasta )**
