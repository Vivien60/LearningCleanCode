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
  `
***
