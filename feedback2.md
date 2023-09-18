# Feedback

Le projet n'est pas entièrement fonctionnel, mais ce n'est pas grave, regardons ensemble ce qu'il te manquait pour faire mieux la prochaine fois 😉

## Retours Globaux

Au niveau du code, j'ai remarqué à plusieurs reprises du Code commenté non retiré avant le push, rien de grave, mais ça joue son rôle dans la clarté et lisibilité du code 😉 

## Retours Cas par Cas

### Active dans la barre de navigation (navbar)

Petite erreur d'inattention ici, rien de grave 😉

```php
<li class="nav-item">
    <a class="nav-link" <?php if($viewData["currentPage"] == "students/students_list") echo "active"; ?>" href="<?= $router->generate('students-list') ?>">Etudiants</a>
</li>
```

Si on regarde ton lien, on voit que tu as fermés ton champ "class" juste avant la vérification de la page en php, ce qui empêche l'ajout de la classe "active" à ton lien.

Version Corrigée sans le " en trop :

```php
<li class="nav-item">
    <a class="nav-link <?php if($viewData["currentPage"] == "students/students_list") echo "active"; ?>" href="<?= $router->generate('students-list') ?>">Etudiants</a>
</li>
```

### Indentation 

Attention à l'indentation de ton code ! Celle-ci est très importante pour la lisiblité de celui-ci (et parfois nécessaire à son fonctionnement, selon le language de programmation).

Reprenons ensemble l'indentation de ton TeachersController pour voir comment corriger ça :

```php
    /**
     * Méthode s'occupant de la page d'accueil
     *
     * @return void
     */
    public function list()
    {
        // On appelle la méthode show() de l'objet courant
        // En argument, on fournit le fichier de Vue
        // Par convention, chaque fichier de vue sera dans un sous-dossier du nom du Controller

        $teachersList = Teacher::findAll();

        $this->show('teachers/teachers_list', ["teachersResults" => $teachersList]);

        }

        public function add()
        {
            // On appelle la méthode show() de l'objet courant
            // En argument, on fournit le fichier de Vue
            // Par convention, chaque fichier de vue sera dans un sous-dossier du nom du Controller
    
    
            $this->show('teachers/teachers_add');
    
            }
```

Comme tu peut le voir, les deux fonctions ne se trouvent pas au même niveau alors qu'elles n'ont pas de raison de ne pas l'être, cela nuisant à la lisibilité de ton code.
Au premier regard, on pourrait croire que la fonction add est sous-jacente à la fonction list, alors que pas du tout. 

Voyons comment corriger ça :

```php
    /**
     * Méthode s'occupant de la page d'accueil
     *
     * @return void
     */
    public function list()
    {
        // On appelle la méthode show() de l'objet courant
        // En argument, on fournit le fichier de Vue
        // Par convention, chaque fichier de vue sera dans un sous-dossier du nom du Controller

        $teachersList = Teacher::findAll();

        $this->show('teachers/teachers_list', ["teachersResults" => $teachersList]);
    }

    public function add()
    {
        // On appelle la méthode show() de l'objet courant
        // En argument, on fournit le fichier de Vue
        // Par convention, chaque fichier de vue sera dans un sous-dossier du nom du Controller
    
        $this->show('teachers/teachers_add');
    }
```

Et voila ! En descendant la fonction add d'un niveau, ainsi que son crochet de fin de deux niveau, on obtient un code bien indenté ! 😉

Comme tu peux aussi le voir, j'ai aussi retiré l'espace entre la dernière ligne et le crochet de fin, question de lisibilité ! 😛 (Ce retirement d'espace est valable aussi pour les autres endroits dans ton code)

Voici une petite ressource pour t'aider avec tout ça : [Click-moi](https://courses.cs.washington.edu/courses/cse154/17au/styleguide/php/spacing-indentation-php.html)

### Affichage des templates _list, collés aux bord de l'écran

A l'affichage des pages utilisant les templates : students_list.tpl.php et teachers_list.tpl.php on remarque un petit problème d'affichage, le contenu étant collé au bord de la page.

Il s'agit simplement je pense ici d'un petit oubli, rien de grave 😊

Pour corriger ça, il faut simplement venir ajouter :
```html
    <div class="container my-4">
```
autour de ton contenu, comme tu l'as fait dans teachers_add ! 😉

### Commentaires de typage des propriétés de models

Petit truc, mais important ici : N'oublie pas d'ajouter des commentaires de typages sur tes propriétés de models, cela permet à ton IDE de bien identifier le type de la variable, et de t'aider en conséquence (En plus de permettre aux autres développeurs d'être sûr du type de ta propriété) 😉

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

## Petit mot de la fin

Pour tout ce qui reste (en gros, pour terminer le projet), je t'invite à jeter un oeil à la correction pour te guider ! 

Ne te décourage pas, malgré quelques petites erreurs, tu as les bases, il ne te reste plus qu'à les appliquer 😉

Si tu as des questions concernant ce parcours (ou pas d'ailleurs), ou si tu as besoin d'aide pour pouvoir le terminer, n'hésite surtout pas à revenir me voir en message privé, je suis la pour aider en cas de besoin 😉