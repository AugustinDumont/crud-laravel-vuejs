# Quelques explications sur l'architecture Larael

## app

Le dossier app est le dossier le plus important de votre projet. C'est celui qui contiendra votre application, c'est à dire, tout votre code PHP (fonctions, classes…).

## bootstrap

Le dossier bootstrap n'est pas utile. Il contient principalement des fichiers liés au lancement du framework ainsi qu'un dossier cache pour certaines optimisations.

## config

Le dossier config permet la configuration du framework. À l'intérieur, chaque fichier correspond à une fonctionnalité configurable. Par exemple, le fichier config/database.php contient un tableau PHP avec différentes valeurs de configuration pour l'URL de la base de données, l'utilisateur, le mot de passe…

Nous verrons, lorsque nous en aurons besoin, comment modifier ces fichiers.

## database

Le dossier database permet la gestion de la base données.

Le principal sous-dossier est le sous-dossier migrations. Les migrations sont des fichiers permettant de décrire votre base de données afin de permettre à Laravel de créer, modifier ou supprimer les tables et les colones automatiquement pour vous. Si vous avez déjà utilisé PHPMyAdmin, les migrations remplacent une partie l'utilisation de PHPMyAdmin.

Les sous-dossiers seeds et factories ne sont pas utiles pour le moment.

## public

Le dossier public contient tous les fichiers accessibles directement par vos visiteurs.

Par exemple, si vous avez des images publiques sur votre site, elles doivent être dans le dossier public (ou dans un sous-dossier du dossier public). Même chose pour vos fichiers CSS et JavaScript.

Laravel fournit de base quelques fichiers utiles comme un favicon, un fichier robots.txt…

Le fichier index.php est la porte d'entrée de votre application. C'est le seul fichier PHP accessible de l'extérieur et il sera responsable de lancer le framework et d'appeler votre code situé dans le dossier app. Vous n'aurez jamais à modifier ce fichier directement car, comme dit précédemment, notre code PHP se trouve dans le dossier app.

## resources

Le dossier resources contient de nombreuses choses diverses. Principalement pour les autres fichiers de notre application qui ne sont pas du code PHP.

Le dossier resources/js et resources/sass contient des fichiers pré-CSS et pré-JS avant leur compilation. Si vous n'avez jamais compilé de fichier SASS, ni utilisé Babel, Webpack ou autre pour compiler votre JavaScript, passez votre chemin. Nous aurons tout le temps d'étudier ces concepts par la suite.

Le dossier resources/lang contient les fichiers de traduction pour votre application. Ils ne vous seront utiles que si vous souhaitez créer un site multi-lingue.

Le dossier resources/views contient les vues de votre application. Les vues sont des fichiers majoritairement composés de HTML et sont chargés de la partie affichage de votre site. C'est l'un des dossiers les plus importants après le dossier app.

## routes

Si vous avez l'habitude d'une architecture PHP simple : https://mon-site.com/contact.php exécute le code situé dans contact.php et https://mon-site.com/compte.php exécute compte.php. Dans une architecture MVC comme celle de Laravel, toutes les requêtes des utilisateurs arrivent via le fichier public/index.php il est donc nécessaire de faire le lien entre l'URL entrée par le visiteur (« /contact », « /mon-compte »…) et le code qui sera exécuté. C'est dans le fichier routes/web.php que vous allez configurer ce lien. Nous verrons justement ça dans le prochain chapitre.

Si vous souhaitez développer une API, le fichier routes/api.php sera l'endroit où mettre vos liens. Si vous souhaitez mettre en place des actions en ligne de commande pour votre application, ce sera le fichier routes/console.php. Et si vous souhaitez envoyer des messages avec des websockets à vos visiteurs, ce sera le fichier routes/channel.php. Mais ces trois fichiers ne sont pas indispensable contrairement au fichier routes/web.php.

## storage

Le dossier storage/app contient tous les fichiers générés par votre application, par exemple des factures PDF, les photos de profil de vos utilisateurs, etc.

Le dossier storage/framework contient des fichiers utilisés uniquement par le framework. Il est recommandé de ne pas ajouter ou supprimer de fichiers à ce dossier.

Enfin, le dossier storage/logs contient les fichiers de logs de votre application. Les fichiers de logs contiennent des informations sur l'activité de votre application. Par défaut, Laravel enregistrera dans un fichier storage/logs/laravel-YYYY-MM-DD.log tous les problèmes rencontrés par votre application : très utile pour comprendre pourquoi votre site ne fonctionne pas par exemple.

## tests

Les tests sont un moyen rapide et automatisé de vérifier que votre application fonctionne comme vous le souhaitez. Si votre application commence à grossir, il est important de comprendre comment fonctionne les tests en programmation.

Les tests sont un sujet complexe, si vous connaissez déjà la programmation vous pouvez regarder mes vidéos Développement Laravel et E-Commerce avec Laravel où je présente comment réaliser une application avec des tests.

## vendor

Le dossier vendor contient toutes les dépendances PHP téléchargées par Composer. Vous pouvez par exemple retrouver dans vendor/laravel/framework le code source de Laravel. Vous ne devez jamais changer les fichiers de ce dossier, car ces modifications seront écrasées par Composer à la prochaine mise à jour.

Les fichiers
À la racine de notre projet, Composer a également ajouté de nombreux fichiers. La plupart sont des fichiers de configuration pour des outils externes (Git, Composer, NPM, PHPUnit…) et nous ne les utiliserons pas avant d'avoir découvert ces outils.

## .env

Les fichiers .env contient les mots de passe de vos services ainsi que toutes les données sensibles de votre application (mot de passe de base de données, adresse de la base de données…). Ce fichier ne doit jamais être partagé. Afin de connaître les informations à renseigner, il existe un fichier .env.example qui contient uniquement des valeurs d'exemple.

.gitattributes et .gitignore
Ces fichiers sont utilisés par le logiciel Git. Si vous n'utilisez pas Git, vous n'avez pas à vous en occuper.

## artisan

Le fichier artisan permet de lancer des commandes comme php artisan serve. Ces commandes vont nous permettre de faire beaucoup de choses avec Laravel et nous verrons au fur et à mesure des tutoriels les différentes commandes existantes.

## composer.json et composer.lock

Le fichier composer.json contient toutes les dépendances requises par notre application. Le fichier composer.lock est un fichier généré automatiquement par Composer lors de la commande composer update. Vous ne devez jamais le modifier manuellement.

## webpack.mix.js

Webpack est un outil permettant de transformer des fichiers SASS en fichier CSS ou encore de compiler du JavaScript. Si vous ne savez pas ce que cela signifie, il n'est pas nécessaire de s'en occuper pour le moment.

## packages.json et yarn.lock

Le fichier packages.json est identique au fichier composer.json en PHP mais pour le JavaScript avec l'outil NPM. Nous ne l'utiliserons pas pour le moment.

## phpunit.xml

PHPUnit est un outil qui permet de lancer les tests unitaires et fonctionnels. Ce fichier sera utile lorsque vous utilisez des tests dans le dossire tests.

## server.php

Le fichier server.php est uniquement présent pour que la commande php artisan serve fonctionne. Vous ne devriez jamais avoir à y toucher.
# ----------------------------------------------------------

# REALISATION DU CRUD SINGLE PAGE

![Screenshot app](/screenshot1.png)
![Screenshot app](/screenshot2.png)

## STEP 1) INSTALLATION LARAVEL

## Installation de Laravel avec Composer
```
$ composer create-project --prefer-dist laravel/laravel project-name
```

# STEP 2) INSTALATION VUE DEPENDENCY ET EDITAGE DES CONFIGURATIONS

## Installation de Vue
```
$ npm install vue
```

## Installation de vue-router et de vue-axios

### Par défaut Vue.js n'est pas équipé pour gérer des requêtes HTTP alors, il faut installer ces deux packages.
```
$ npm install vue-router vue-axios --saved
```
### Attention, si utilisation de Bottstrap, il est nécessaire de faire les commandes suivantes :
```
$ composer require laravel/ui --dev
```
\$ php artisan ui boostrap

## Installation des packages ajoutés au package.json
```
$ npm install
```

### Ensuite, il faut déclarer ces nouveaux composants (, bootstrap, vue, vue-router et vue-axios) dans notre fichier ressources/assets/js/app.js
```
    require('./bootstrap');

    window.Vue = require('vue');                // To load Vue and import Vue in all Laravel before the plugins

    import VueRouter from 'vue-router';         // import VueRouter from package vue-router
    Vue.use(VueRouter);                         // tell Vue to use VueRouter with the method Vue.use()

    import VueAxios from 'vue-axios';           // import VueAxios from package vue-axios
    import axios from 'axios';                  // importe axios from package axios
    Vue.use(VueAxios, axios);                   // tell Vue to use VueAxios and axios
   ```

### Installation d'un component exemple, également dans le fichier app.js

```
    Vue.component('example-component', require('./components/ExampleComponent.vue'));
```

    // Ci-dessus, création d'un component exemple (intérêt est de montrer ou se situe la configuration des components) dont le nom est example-component avant de directement l'importer dans le dossier components. PascalCase : example-component sera référencé ExampleComponent.

    Cet ExampleComponent sera supprimé lors de l'ajout des véritables components à l'étape 4.

### Hash mode et vue-router ou comment éviter les rechargements de page

    // Par défaut, le vue-router est un hash mode. Càd qu'il utilise le URL hash pour simuler un full URL et éviter que les pages se rechargent lors des changements de page.

    // Pour supprimer le hachage, nous utilisons le mode historique du router afin de permettre la navigation dans les URL sans rechargement de page.

    const router = new VueRouter({ mode: 'history'});

### Construction of Vue Instance (cfr id 'app') with the router property

// Grâce à la création de cette instance Vue, avec les propriétés du router et monté sur l'id #app présent dans le post.blade.php du dossier view.

    const app = new Vue(Vue.util.extend({ router })).$mount('#app');

## Création de post.blade.php

// C'est ici qu'on va retrouver l'id "app" dans lequel va être pusher le exampleComponent.vue.
Post.blade.php est en quelque sorte notre page index.
```
    // post.blade.php

    <!doctype html>
    <html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
        <head>
            <meta charset="utf-8">
            <meta name="viewport" content="width=device-width, initial-scale=1">
            <title>Laravel</title>
            <link href="https://fonts.googleapis.com/css?family=Nunito:200,600" rel="stylesheet" type="text/css">
            <link href="{{ mix('css/app.css') }}" type="text/css" rel="stylesheet" />
            <meta name="csrf-token" value="{{ csrf_token() }}" />
        </head>
        <body>
            <div id="app">
            <example-component></example-component>
            </div>
            <script src="{{ mix('js/app.js') }}" type="text/javascript"></script>
        </body>
    </html>
```
## Change the route inside route/web.php / Ce que le client voit suite requête URL

Tout d'abbord, quand on parle de routing, il est essentiel de connaître les principales méthodes HTTP :

-   GET : c’est la plus courante, on demande une ressource qui ne change jamais, on peut mémoriser la requête, on est sûr d’obtenir toujours la même ressource,
-   POST : elle est aussi très courante, là la requête modifie ou ajoute une ressource, le cas le plus classique est la soumission d’un formulaire (souvent utilisé à tort à la place de PUT),
-   PUT : on ajoute ou remplace complètement une ressource,
-   PATCH : on modifie partiellement une ressource (donc à ne pas confondre avec PUT),
-   DELETE : on supprime une ressource.

Pour Laravel on veut que toutes les requêtes aboutissent obligatoirement sur le fichier index.php situé dans le dossier public. Pour y arriver on peut utiliser une URL de ce genre :

http://monsite.fr/index.php/mapage

Mais ce n’est pas très esthétique avec ce index.php au milieu. Si vous avez un serveur Apache lorsque la requête du client arrive sur le serveur où se trouve notre application Laravel elle passe en premier par le fichier .htaccess, s’il existe, qui fixe des règles pour le serveur. Il y a justement un fichier .htaccess dans le dossier public de Laravel avec une règle de réécriture de telle sorte qu’on peut avoir une url simplifiée :

http://monsite.fr/mapage

Lorsque la requête atteint le fichier public/index.php l’application Laravel est créée et configurée et l’environnement est détecté. Ensuite le fichier routes/web.php est chargé.

    //route/web.php

    <?php

    Route::get('/{any}', function () {
    return view('post');
    })->where('any', '.*');

Comme Laravel est explicite vous pouvez déjà deviner à quoi sert ce code :

Route : on utilise le routeur,
get : on regarde si la requête a la méthode « get »,
‘/’ : on regarde si l’url comporte uniquement le nom de domaine,
dans la fonction anonyme on retourne (return) une vue (view) à partir du fichier « post ».

C’est ce fichier post.blade.php comportant du code Html qui génère le texte d’accueil que vous obtenez au démarrage initial de Laravel.

# STEP 3) CREATION DES VUE COMPONENTS

Création de quatre fichier.vue, pour chacunes des "pages" à pusher dans la single page. Fichier vue permet de combiner CSS, HTML et JS ou vuejs.

    //ressources/js/components

HomeComponent.vue
CreateComponent.vue
EditComponent.vue
IndexComponent.vue

## Exemple : ressources/js/components/HomeComponent.vue

    <template>
    <div class="row justify-content-center">
        <div class="col-md-8">
            <div class="card card-default">
                <div class="card-header">Home Component</div>

                <div class="card-body">
                    I'm the Home Component component.
                </div>
            </div>
        </div>
    </div>
    </template>

    // Après avoir créé le component, on l'exporte afin de pouvoir le récupérer dans exampleComponent.vue qui sera pushé dans post.blade.php

    <script>
        export default {
            mounted() {
                console.log('Component mounted.')
            }
        }
    </script>


    Pour voir la composition des différents components, se rendre dans chacun des fichiers. Ils correspondent tous aus visuels accessibles en fonction des requêtes de l'utilisateur.

# STEP 4 : CONFIGURER LE VUE ROUTER

Précédemment, nous avions créé un ExampleComponent :

Vue.component('example-component', require('./components/ExampleComponent.vue'));

### Dans le fichier app.js, nous allons maintenant importer les différents components créés dans l'étape précédente.

    import HomeComponent from './components/HomeComponent.vue';
    import CreateComponent from './components/CreateComponent.vue';
    import IndexComponent from './components/IndexComponent.vue';
    import EditComponent from './components/EditComponent.vue';

### Ensuite, il faut définir les routes.

// Chaque route doit correspondre à un composant. Le « composant » peut soit être un véritable composant créé via `Vue.extend()`, // ou juste un objet d'options.

    const routes = [
    {
        name: 'home',  // le rooter amènera la page app.vue (statique) et entre les balises <router-view> sera appelées /home, etc
        path: '/',
        component: HomeComponent
    },
    {
        name: 'create',
        path: '/create',
        component: CreateComponent
    },
    {
        name: 'posts',
        path: '/posts',
        component: IndexComponent
    },
    {
        name: 'edit',
        path: '/edit/:id',
        component: EditComponent
    }
    ];

### Créez l'instance du routeur et passez l'option routes avant de la passer à notre application Vue

// Vous pouvez également passer des options supplémentaires, comme 'history' vu précédemment.

    const router = new VueRouter({ mode: 'history', routes: routes});

### Créer et monter l'instance de Vue sur id "app" avec les propriétés du router.

// Soyez sûr d'injecter le routeur avec l'option router pour
// permettre à l'application tout entière d'être à l'écoute du routeur.
// le "App" appelle le router sur App.vue !!! App.vue redirigera ensuite vers home / create / ,...

    const app = new Vue(Vue.util.extend({ router }, App)).$mount('#app');

## Création de App.vue

// js/components/app.vue

    <template>
        <div class="container">
            <div>
                <transition name="fade">
                    <router-view></router-view>
                </transition>
            </div>
        </div>
    </template>

    <style>
        .fade-enter-active, .fade-leave-active {
        transition: opacity .5s
        }
        .fade-enter, .fade-leave-active {
        opacity: 0
        }
    </style>

    <script>

        export default{
        }
    </script>

Le router va appeler en premier le app.vue qui restera statique. Cette page appelera les autres components dans la balise <router-view> pour donner l'aspect dynamique.

# STEP 5 : CREATION DE LA BARRE DE NAVIGATION

// App.vue

    <template>
    <div class="container">
        <nav class="navbar navbar-expand-sm bg-dark navbar-dark">
        <ul class="navbar-nav">
            <li class="nav-item">
            <router-link to="/" class="nav-link">Home</router-link>
            </li>
            <li class="nav-item">
            <router-link to="/create" class="nav-link">Create Post</router-link>
            </li>
            <li class="nav-item">
            <router-link to="/posts" class="nav-link">Posts</router-link>
            </li>
        </ul>
        </nav><br />
        <transition name="fade">
        <router-view></router-view>
        </transition>
    </div>
    </template>

    <style>
        .fade-enter-active, .fade-leave-active {
        transition: opacity .5s
        }
        .fade-enter, .fade-leave-active {
        opacity: 0
        }
    </style>

    <script>

        export default{
        }
    </script>

# STEP 6) CREATION DU FORM

// On a besoin de créer un formulaire pour entrer les détails .
// On a également définit l'objet appelé "post". L'objet post à deux propriétés, title et body.

// On a une méthode appellée addPost(), donc quand un utilisateur submit the form, on récuperera le input dans la méthode addPost(). A partir de là, nous pourrons envoyer une request POST à Laravel server and sauvegarder la data dans la DB.

    <template>
    <div>
        <h1>Create A Post</h1>
        <form @submit.prevent="addPost"> // method addPost() appelée au submit + preventdefault pour éviter le rechargement
        <div class="row">
            <div class="col-md-6">
            <div class="form-group">
                <label>Post Title:</label>
                <input type="text" class="form-control" v-model="post.title">
            </div>
            </div>
            </div>
            <div class="row">
            <div class="col-md-6">
                <div class="form-group">
                <label>Post Body:</label>
                <textarea class="form-control" v-model="post.body" rows="5"></textarea>
                </div>
            </div>
            </div><br />
            <div class="form-group">
            <button class="btn btn-primary">Create</button>
            </div>
        </form>
    </div>
    </template>

    <script>
        export default {
            data(){  // on export data = input et on return post pour les v-model post.title et post.body
                return {
                    post:{}
            }
        },
        methods: { // on définit la méthode addPost() appelée dans le haut du formulaire.
        addPost(){
            console.log(this.post);
        }
        }
    }
    </script>

# STEP 7) CREATION DU LARAVEL BACKEND

## Construction d'un schema pour la table post

// Générer un modèle Post tout en génrant la migration vers la DB (-m)

\$ php artisan make:model Post -m

// va créer un fichier app/Post.php

## Ajouter ce schema dans create_posts_table.php

// on complète le schéma avec d'autres table pour compléter la DB à migrer

public function up()
{
Schema::create('posts', function (Blueprint $table) {
            $table->increments('id');
$table->string('title');
            $table->text('body');
\$table->timestamps();
});
}

## Migrer la DB

\$ php artisan migrate

## Prevenir the mass assignment exception

L'erreur massAssignmentException est une sécurité de Laravel par défaut lorsque nous utilisons des tableaux PHP pour spécifier notre attributs. Laravel exige que nous indiquions explicitement les colonnes autorisées à être remplies de cette manière.

Pour indiquer les colonnes autorisées à Laravel, nous devons créer dans notre modèle Utilisateur, un attribut \$fillable (« remplissable » en français).

// Post.php

    <?php

    namespace App;

    use Illuminate\Database\Eloquent\Model;

    class Post extends Model
    {
        protected $fillable = ['title', 'body'];
    }

## Créer un controller pour amener à la table Post

\$ php artisan make:controller PostController

va créer le fichier app/Http/Controllers/Auth/PostController.php

// PostController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;

    class PostController extends Controller
    {
        //
    }

-   0n trouve en premier l’espace de nom (App\Http\Controllers),
-   Le contrôleur hérite de la classe Controller qui se trouve dans le même dossier et qui permet de factoriser des actions communes à tous les contrôleurs.

## Utilisation de Laraval Ressource Collection pour le développement API

\$ php artisan make:resource PostCollection

Il s'agit de l'ensemble des fonction post, edit, show, put, delete,...

Va générer une classe resource qui sera créé dans app/Http/Resources/PostCollection.php = links pour attribuer les ressources de Laravel.

    <?php

    // PostCollection.php

    namespace App\Http\Resources;

    use Illuminate\Http\Resources\Json\ResourceCollection;

    class PostCollection extends ResourceCollection
    {
        /**
        * Transform the resource collection into an array.
        *
        * @param  \Illuminate\Http\Request  $request
        * @return array
        */
        public function toArray($request)
        {
            return parent::toArray($request);
        }
    }

# STEP 8) DEFINIR LES OPERATIONS CRUD

## 8.1. Premièrement, définir la function qui store les data dans la DB mysql

    <?php

    // PostController.php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Http\Resources\PostCollection;
    use App\Post;

    class PostController extends Controller
    {
        public function store(Request $request)
        {
        $post = new Post([
            'title' => $request->get('title'),
            'body' => $request->get('body')
        ]);

        $post->save();

        return response()->json('success');
        }
    }

## 8.2. Ajouter les fonctions edit, update, index et delete

    <?php

    // PostController.php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;
    use App\Http\Resources\PostCollection;
    use App\Post;

    class PostController extends Controller
    {
        public function store(Request $request)
        {
        $post = new Post([
            'title' => $request->get('title'),
            'body' => $request->get('body')
        ]);

        $post->save();

        return response()->json('successfully added');
        }

        public function index()
        {
        return new PostCollection(Post::all());
        }

        public function edit($id)
        {
        $post = Post::find($id);
        return response()->json($post);
        }

        public function update($id, Request $request)
        {
        $post = Post::find($id);

        $post->update($request->all());

        return response()->json('successfully updated');
        }

        public function delete($id)
        {
        $post = Post::find($id);

        $post->delete();

        return response()->json('successfully deleted');
        }
    }

# STEP 9) Define the API routes

Les routes API permettent, lorsque l'utilisateur clique sur un évenement save, create, update,... de rediriger vers le controller, qui apporte la réponse.

    <?php

    // api.php

    use Illuminate\Http\Request;                                                    // access Laravel class for request

    Route::middleware('auth:api')->get('/user', function (Request $request) {        // middelware, checking before access to controller
        return $request->user();
    });

    Route::post('/post/create', 'PostController@store');
    Route::get('/post/edit/{id}', 'PostController@edit');
    Route::post('/post/update/{id}', 'PostController@update');
    Route::delete('/post/delete/{id}', 'PostController@delete');
    Route::get('/posts', 'PostController@index');

    // Avant le router, la requête passe par le middleware... si l'utilisateur remplit le syst§me d'authentification, alors il a accès aux controllers.
