# Feedback

Le projet est fonctionnel dans son entièreté (à l'exception d'une petite erreur de permissions), mes félicitations à toi. 👏👏

Rien à redire sur l'affichage de l'application, tout est parfait ! 👌

## Retours Globaux

Au niveau du code, j'ai remarqué à plusieurs reprises ces petits éléments :

- Commentaires parfois non terminés/manquants
- Du Code commenté non retiré avant le push

Attention à ces petites choses qui ont leur importance 😛

## Retours Cas par Cas

### Erreur de Permission

Actuellement, en tant qu'utilisateur possedant le rôle "user", je n'ai pas le droit d'accéder à la page listant les profs, alors que normalement, si.

En relisant les consignes, on se rends mieux compte :

```
- les pages liées aux profs ont des permissions plus précises :
  - ajout, modification et suppression autorisés au _Role_ `admin`
  - liste autorisée aux _Roles_ `admin` et `user`
```

Pour que ce soit bon dans ton code, il fallait juste modifier dans le CoreController les droits de "teacher_list" et ajouter 'user' à son tableau de permissions 😉

~~'teacher_list' => ['admin']~~
'teacher_list' => ['admin', 'user']

### Commentaire de séparation des routes

Plusieurs choses ici, même si ce n'est qu'un peu de chipotage 😉

Premièrement, fait au plus simple pour ce genre de commentaire de séparation :

~~// route pour la home~~
// Accueil

ou encore

// Home

Il n'en sera que plus simple de retrouver d'un seul coup d'oeil la route que tu cherche dans ton code 😉

Deuxièmement, petit conseil ici, si tu utilise VSCode, tu peut utiliser l'extension "Comment Divider" qui permet d'un simple raccourci clavier de faire des beaux commentaires :

/* --------------------------------- Accueil -------------------------------- */

Voili Voilou, c'était pas grand chose 😛

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