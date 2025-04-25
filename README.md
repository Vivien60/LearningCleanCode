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

La plupart des noms ne sont pas significatifs en eux-mêmes : i lconvient alors de les englober dans une classe ou une fonction ou un namespace, qui leur donne suffisamment de contexte pour en appréhender le sens.
***
