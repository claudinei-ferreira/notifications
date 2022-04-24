<div align="center">
  <h1>LARAVEL NOTIFICATIONS</h1>
  <p>Claudinei Ferreira de Jesus</p>
</div>

<div align="left">
    <ul>
        <li><a href="#sobre">Sobre</a></li>        
        <li><a href="#instalação-do-laravel">Instalação do Laravel</a></li>
        <li><a href="#posts-e-comentários">Posts e Comentários</a></li>
        <li><a href="#notificações-por-e-mail">Notificações por E-mail</a></li>
        <li><a href="#notificações-por-database">Notificações por Database</a></li>
        <li><a href="#gerenciar-notificações-vuejs">Gerenciar Notificações VueJS</a></li>
        <li><a href="#real-time">Real-time</a></li>
        <li><a href="#referência-de-estudos">Referência de Estudos</a></li>
        <li><a href="#autor">Autor</a></li>
    </ul>
</div>

# Sobre
Este é um projeto de estudos para conhecimento sobre notificações no Laravel.

# Instalação do Laravel

```bash
composer create-project --prefer-dist laravel/laravel notifications
```

## Configurar arquivo .env
O arquivo .env encontra se na raiz do projeto Laravel.

### Nome do Projeto
Deixe o nome do projeto como a seguir:
~~~~env
APP_NAME="Estudos com Notificações"
~~~~

### Url do Projeto
No meu caso criei um virtual host que aponta para o seguinte endereço.
~~~~env
APP_URL=http://notifications.test
~~~~


## Banco de Dados
Crie um banco de dados com o nome "notifications". Com charset "utf8mb4_unicode_ci" <br>

Configure as informações do banco no arquivo .env, localizado na raiz do projeto
```bash
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=notifications
DB_USERNAME=root
DB_PASSWORD=#senha-do-banco-de-dados
```

## Configurar AppServiceProvider
Vamos configurar a quantidade máxima de caracteres nos campos do banco de dados, quando não informamos um valor padrão na migration. <br>
Para isso acesse o arquivo: "app/Providers/AppServiceProvider.php" e no metódo boot adicione o código a seguir:
~~~php
use Illuminate\Support\Facades\Schema;
.
.
.
public function boot()
{
    Schema::defaultStringLength(191);
}
~~~

## Configurar Timezone do projeto
- Acesse o arquivo "config/app.php"
- Localize a config "timezone" e altere como a seguir:
~~~~php
'timezone' => 'America/Sao_Paulo'
~~~~ 

## Criação de Models e Migrations: Posts
Pelo terminal rode os comandos a partir da pasta do seu projeto. <br>
Este comando criará a model de Post, bem como a migration de post
```bash
php artisan make:model Post -m
```

Acesse o arquivo de migration da tabela de posts: "database/migrations/2022_04_24_120034_create_posts_table.php" <br>
O nome da migration de post pode variar de acordo com a data que você fez a criação. <br>


~~~php
Schema::create('posts', function (Blueprint $table) {
    $table->id();
    $table->unsignedBigInteger('user_id');
    $table->string('title')->unique();
    $table->text('body');
    $table->timestamps();

    $table->foreign('user_id')
        ->references('id')
        ->on('users')
        ->onDelete('cascade');
});
~~~

Vamos rodar o camando para criar as tabelas no banco de dados:
```bash
php artisan migrate
```
Se tudo correr corretamente, seu banco de dados "notifications" deverá ter agora as tabelas que criamos com o comando de migrate. As tabelas são essas:
- filed_jobs
- migrations
- password_resets
- personal_access_tokens
- posts
- users

# Posts e Comentários
>Estudando...


# Notificações por E-mail
>Estudando...



# Notificações por Database
>Estudando...



# Gerenciar Notificações Vue.js
>Estudando...



# Real-time
>Estudando...



# Referência de Estudos
[Especializa Ti](https://especializati.com.br/)


# Autor
[Claudinei Ferreira de Jesus](https://github.com/claudinei-ferreira)


