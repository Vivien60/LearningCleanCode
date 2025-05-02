# LearningCleanCode
Just notes about my second lecture of RCM's Clean Code book

***
## Chapitre 2 - Nommages explicites
Remplacer "List" dans les noms de fonctions avec par ex "**bunchOf**" ou "**Group**" ou juste avec un "**s**". Car List, dans certains langages est un type particulier, ou  signifie quelque chose de précis.
<br/>Note de moi-même : de plus cela induit un certain format dans la représentatio de la donnée, ce qui signifie que si l'on change la donnée, on devra changer le nom : contraire au principe OCP si je ne me trompe pas.

La longueur  d'un nom doit correspondre à la taille de sa portée dans le code => utiliser j ou k peut être ok, surtout que c'est une convention dans le cas des boucles for par exemple. 
<br/>Mais il FAUT que la portée de la variable soit très limitée, à peu près limitée à la boucle dans le cas de i,j, ou k par exemple. Autrement le lecteur du code devra en mémoriser le sens, puisque son nom ne le transporte pas, passant parfois par ce processus que nous avons tous : lui donner mentalement un autre nom... autant le faire explicitement dans le code !

Classe = nom ou groupe nominal
Méthode/fonction = verbe ou groupe verbal

La plupart des noms ne sont pas significatifs en eux-mêmes : il convient alors de les englober dans une classe ou une fonction ou un namespace, qui leur donne suffisamment de contexte pour en appréhender le sens.
***
## Chapitre 3 - Fonctions
Une fonction réalise-t-elle plusieurs choses ? <br/>
  - Si toutes les étapes de son process se situent à un niveau d'abstraction en-dessous de celui du nom de la fonction, alors OUI.<br/>
  En effet, elle fera alors une seule chose : ce que son nom indique (sans v"AND", trichez pas ! ).<br/>
  - Exemple de tentative de détection de plusieurs reponsabilités : <br/>
  POUR générer une page qui comprend un montage et un démontage (TO nom_de_la_fonction), nous vérifions que la page est une page de test et si c'est le cas, nous incluons les pages de montage et de démontage.<br/>
  Dans tous les cas, nous présentons la page en HTML<br/>
  => ici, une seule responsabilité, car pas besoin d'autre "POUR" pour expliquer un autre détail, un autre "niveau" de détail.<br/>

_Note et question de moi-même : j'arrive à comprendre, concernant le listing 3.7 p56, que la fonction "render" a plusieurs niveaux d'abstraction grâce à l'abstraction des 4 méthodes dans la fonction includeTrucAndTruc appelée, mais cependant pas en déterminant le niveau d'abstraction ou le nombre d'abstractions, plutôt en pensant à l'OCP.<br/>
Autre Note : difficile de compter le nombre de niveaux d'abstractions. A  réfléchir et travailler_

Séparer commandes et demandes<br/>
  - une fonction devrait soit faire une chose, soit répondre à une question.<br/>
  Par ex `public boolean set(String attribute, String value);` fait une chose : elle assigne une valeur à un attribut, et elle retoure aussi un booléen indiquant la réussite de l'opération<br/>
  Cela peut conduire à `if (set("nomUtilisateur", "OncleBob"))`. Or "set" est soit adjectif soit verbe... Lequel des 2 est-ce ici ?
  Mieux vaudrait écrire :
  `
  if (attributeExists("nomUtilisateur")) {
    setAtribute(.....
  }

Le véritable objectif de bien nommer et structurer ses fonctions est de **raconter l'histoire** du système.

***
## Chapitre 6 - Objets et structures de données
- Structure de données : des objets ne faisant qu'exposer leurs données<br/>
- **A retenir, c'est FORT :**
>Un code procédural (un code qui utilise des structures de données), facilite l'ajout de nouvelles fonction sans modifier les structures de données existantes. <br/>
Un code orienté objet facilite l'ajout de nouvelles classes sans modifier les fonctions existantes.<br/><br/>Un code procédural complexifie l'ajout de nouvelles structures de données car toutes les fonctions doivent être modifiées. Tandis qu'un  code OO complexifie l'ajout de nouvelles fonctions car toutes les classes doivent être modifiées
- Loi de Déméter : Dans une méthode, il ne faut pas invoquer les méthodes des objets retournés, seulement celles de ceux passées en paramètre ou de ceux qui sont membres de l'objet.
  <br/>Pourquoi ? Cela ajoute des connaissances, du couplage. Diminuer ce couplage augmentee la maintenabilité.
- Page 110 : relire le pb et sa résolution de temps en temps

## Chapitre 7 : Gestion des erreurs
- Ma pensée<br/>
  _Faut-il vraiment faire une règle de séparer ibjet et structure de données ? A quel moment une "fausse structure de données (un objet avec des mtutateurs et des variables privés) deviuent-ils un véritable objet? Posé autrement: Quelle est la     caractéristique minimale qui fait basculer une entité de l'un à l'autre ?_
- Exceptions : n'utiliser des classes différentes que si l'on souhaite n'en intercepter qu'une et ignorer les autres.

