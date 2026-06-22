# OverTheWire — Bandit

Mes solutions du wargame Bandit. Objectif : apprendre les bases de Linux et de la ligne de commande.

## Niveau 0 -> 1
But : trouver le mot de passe du niveau 1, dans un fichier du dossier perso.

Méthode : ` ls ` pour lister, puis ` cat readme `.

Appris : ls, cat.



## Niveau 1 -> 2
But : lire un fichier avec un nom non-standard

Méthode : ` cat ./- ` (le ` ./ ` évite que le tiret soit pris pour une option).

Appris : gérer un nom de fichier non-standard



## Niveau 2 -> 3
But : lire un fichier avec des espaces dans le nom.

Méthode : ` cat ./'spaces in this filename' `, ou ` "cat ./--spaces in this filename" ` ou autocomplétion avec Tab.

Appris : gérer les espaces dans les noms de fichiers.



## Niveau 3 -> 4 
But : lire un fichier caché

Méthode : ` ls -la ` pour afficher lister même les éléments cachés, puis ` cat ./ ` car le nom du fichier est non-standard.

Appris : instruction ` -la ` pour afficher les éléments cachés.



## Niveau 4 -> 5 
But : déterminer le type d'un fichier

Méthode : ` file ` pour déterminer le type du fichier, ` file ./* ` pour afficher tous les fichiers dans le chemin ainsi que leur type

Appris : instructions ` file ` et ` * `.

## Niveau 5 -> 6
But: trouver un fichier par ses propriétés

Méthode: ` find ` pour trouver un fichier dans la hiérarchie en imposant certaines conditions. Ici, ` find inhere -size 1033c ! -executable ` permet de trouver dans "inhere" un fichier de taille 1033 octets (` -size 1033c `) qui n'est pas executable (` ! -executable `).

Appris : ` find ` , conditions de taille et de caractère executable d'un fichier.



## Niveau 6 -> 7
But: fichiers possédés oar des groupes ou des utilisateurs

Méthode: ` find ` avec les conditions ` -group ` et ` -user `. commande complète : ` find / -user bandit7 -group bandit6 -size 33c 2>/dev/null `, trouve le fichier possédé par le groupe bandit6 et l'utilisateur bandit7, faisant 33 octets, en partant de la racine du serveur.
Par ailleurs, l'intruction ` 2>/dev/null ` permet de rediriger les erreurs (sortie 2) vers la poubelle (le dossier /dev/null).

Appris: ` -user `, ` -group `, et les différentes sorties et la poubelle Linux.