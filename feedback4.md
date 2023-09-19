# Feedback

Malheureusement, en l'état, le projet ne fonctionne pas, mais ne t'en fais pas, on va voir tout ça ensemble pour mieux comprendre ! 😉

Commençons par pourquoi il ne fonctionne pas :

Tout simplement car il manque des choses, si on jette un oeil à ton index.php et à ton listing de routes, on peut voir qu'il y a une route "/" qui est attribué au controller MainController, mais ce controller n'existe pas ! ☹️

Premier conseil, quand tu pars sur des projets comme ça, n'hésite pas à intégrer les routes petit à petit, et en commençant par le plus basique/le plus simple. Mettre en place la page d'accueil aurait déjà été une bonne première étape !

Deuxième chose qu'il te manque pour le fonctionnement de ton code, c'est le CoreController !

En effet, si on regarde tes controllers TeachersController et StudentController, on peut voir qu'ils étendent CoreController (Ils en [héritent](https://grafikart.fr/tutoriels/heritage-extends-560)) cependant CoreController n'existe pas dans ton code ! 

Comme dit plus haut, vas-y petit à petit, en commençant par le début ! Commence par établir les fondations de tes controllers, avant de vouloir mettre les murs 😉

Si tu as un doute d'à quoi doit ressembler CoreController, n'hésite pas à regarder la correction, et à me recontacter en cas de questions, je serais ravi d'éclairer ta lanterne à ce sujet.

On va essayer de regarder ensemble les différentes routes que tu as mise en place tout de même.

## teachers/list

Comme on peut le voir en se rendant sur cette url, on obtient une erreur parlant d'un identifier "teachers" unexpected. En effet, si l'on regarde la fonction correspondante à cette route (En regardant dans le index.php)

On voit que dans le TeachersController, dans la fonction teachers(), ligne 20 on a :

```php
    /**
     * Display teachers 
     *
     * @return void
     */
    public function teachers() {

        // VERIFICATION QUE L'UTILISATEUR AIT LES DROITS
        $teachersModel = new Teachers
        teachers();
        $teachers = $teachersdModel->findAll();

        $this->show("teachers/teachers_list", [
            'teachers' => $teachers
        ]);
        
    }
```

Il y a un appel à une fonction teachers qui n'existe pas. Pour cibler la fonction teachers du TeachersController, il aurait fallu faire "$this->teachers()", mais même la, il n'y avait pas de raison de le mettre.. Un oubli ? Un incompréhension ? N'hésite pas à m'en faire part, on peut discuter de ça ensemble ! 

Voici comment tu aurait du coder cette fonction :

```php
    /**
     * Display teachers 
     *
     * @return void
     */
    public function teachers() {
        $teachersModel = new Teachers(); // Récupération du model Teachers
        $teachers = $teachersModel->findAll(); // Récupération des Teachers dans la base de donnée

        $this->show("teachers/teachers_list", [ // Affichage de la page
            'teachers' => $teachers // On passe les teachers à la page pour pouvoir les afficher
        ]);
    }
```

Il y avait aussi une petite faute de frappe sur ton deuxième teachersModel, attention à tout ça 😛

## students/list

Malheureusement, même problème que pour les professeurs, mais tu sais comment corriger tout ça maintenant 😉

## StudentsController : teachersEdit

Attention ! Tu as oublié de renommer la fonction après le copier/coller, il faudrait changer ça 😉

## Routes Restantes

Globalement, pour le restant des routes, le CoreController manquant pose problème aussi.

## Models

### Indentation & Espaces

Attention à l'indentation de tes classes Teachers et AppUser ! Elles ne sont pas bien indentés, elles devraient être "collée" contre le bord gauche ! Comme pour Student et CoreModel

De même, attention à ne pas avoir de petits espaces avant la classe comme tu l'a fait dans CoreModel, ça casse un peu la propreté/lisibilité du fichier 😉

### Commentaires de Propriétés

Attention aux commentaires de propriétés, il ne sont pas correct dans tout les fichiers !

Il faudrait reproduire ce que tu as fait dans AppUser dans les autres models, c'était très bien ! 😉

Petit rappel, voici comment faire un commentaire de propriété :

```php
/**
 * @var string
 */
private $email;

/**
 * @var int
 */
private $teacher_id;
```

### Espaces entre les fonctions

Attention à ne pas coller les fonctions entre elles, ça casse la lisibilité, voici comment les séparer :

```php
    public static function find($id)
    {
        // contenu de la fonction
    }
        
    public static function findAll()
    {
        // contenu de la fonction
    }

    public function insert()
    {
        // contenu de la fonction
    }
```

### Nommage des models

Attention à bien nommer tes models au singulier, ce sera bien plus compréhensible ainsi ! Car une instance du model = un élève/prof/user, et non plusieurs. 😉 

## Commentaires d'oShop

Attention, j'ai retrouvé des bouts de commentaire d'oShop dans ton code qui n'ont pas lieu d'être ici 😛

# Petit mot de la fin

Malheureusement, il y pas mal de petites erreurs qui empêche le projet de fonctionner, mais je pense que c'est lié à deux choses :

- Quelques petites incompréhension
- Un manque de méthode qui t'a fait te perdre

Ce que je peut te conseiller de faire, c'est de recommencer le projet à 0. Cette fois, en t'aidant au besoin de la correction, je te conseil d'y aller petit à petit :

- Commencer par faire ton index.php et uniquement map la page d'accueil
- Faire ton CoreController
- Faire ton MainController qui contiendra la page d'accueil
- Mettre en place ton layout (header + footer) et ta navbar
- Faire en sorte que le CoreController affiche automatiquement ton layout autour de la page à afficher (Regarde la correction ou demande-moi au besoin)
- Créer le template de la page d'accueil !

Une fois que tu aura fait ça et que tu pourra afficher la page d'accueil, tu aura une bonne base pour commencer ton projet 😉

Ensuite, tu pourra commencer les models avec par exemple les professeurs :

- Créer ton CoreModel
- Créer ton model Teacher

Une fois que c'est fait, ajoute la route du listing des profs, puis ainsi de suite, jusqu'à temps en avoir fini avec les profs 😉

Tu peut y aller vraiment progressivement, en t'aidant de la correction et en demandant de l'aide au besoin, n'hésite pas à poser les questions qui te passe par la tête, si ça peut t'aider à mieux visualiser et comprendre tout ça !

Je suis certain qu'avec cette méthodo progressive et la correction, tu va y arriver, ne désespère pas ! On est derrière toi au besoin ! 