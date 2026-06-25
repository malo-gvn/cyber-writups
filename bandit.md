# OverTheWire — Bandit

Mes solutions du wargame Bandit. Objectif : apprendre les bases de Linux et de la ligne de commande.

## Niveau 0 -> 1
But : trouver le mot de passe du niveau 1, dans un fichier du dossier perso.

Méthode : ` ls ` pour lister, puis ` cat readme `.

Solution : ` cat readme `.

Appris : ` ls `,` cat `.



## Niveau 1 -> 2
But : lire un fichier avec un nom non-standard

Méthode : ` cat ./- ` (le ` ./ ` évite que le tiret soit pris pour une option).

Solution : ` cat ./- `.

Appris : gérer un nom de fichier non-standard



## Niveau 2 -> 3
But : lire un fichier avec des espaces dans le nom.

Méthode : ` cat ./'--spaces in this filename--' `, ou ` "cat ./--spaces in this filename--" ` ou autocomplétion avec Tab.

Solution : ` cat ./'--spaces in this filename--' `.

Appris : gérer les espaces dans les noms de fichiers.



## Niveau 3 -> 4 
But : lire un fichier caché

Méthode : ` ls -la ` pour afficher lister même les éléments cachés, puis ` cat ./ ` car le nom du fichier est non-standard.

Solution : ` cd inhere `, puis ` ls -la ` pour afficher tous les dossiers, puis ` cat ./...Hiding-From-You `.

Appris : instruction ` -la ` pour afficher les éléments cachés.



## Niveau 4 -> 5 
But : déterminer le type d'un fichier

Méthode : ` file ` pour déterminer le type du fichier, ` file ./* ` pour afficher tous les fichiers dans le chemin ainsi que leur type.

Solution : ` cd inhere `, ` file ./* ` pour tout afficher, puis ` cat./-file07 `.

Appris : instructions ` file ` et ` * `.


## Niveau 5 -> 6
But: trouver un fichier par ses propriétés

Méthode: ` find ` pour trouver un fichier dans la hiérarchie en imposant certaines conditions. Ici, ` find inhere -size 1033c ! -executable ` permet de trouver dans "inhere" un fichier de taille 1033 octets (` -size 1033c `) qui n'est pas executable (` ! -executable `).

Solution : ` find inhere -size 1033c ! -executable `, puis ` cd inhere/maybehere07 `, puis ` cat ./.file2 `

Appris : ` find ` , conditions de taille et de caractère executable d'un fichier.



## Niveau 6 -> 7
But: fichiers possédés oar des groupes ou des utilisateurs

Méthode: ` find ` avec les conditions ` -group ` et ` -user `. commande complète : ` find / -user bandit7 -group bandit6 -size 33c 2>/dev/null `, trouve le fichier possédé par le groupe bandit6 et l'utilisateur bandit7, faisant 33 octets, en partant de la racine du serveur.
Par ailleurs, l'intruction ` 2>/dev/null ` permet de rediriger les erreurs (sortie 2) vers la poubelle (le dossier /dev/null).

Solution : ` find / -user bandit7 -group bandit6 -size 33c 2>/dev/null `, puis ` cd /var/lib/dpkg/info `, puis ` cat ./bandit7.password `.

Appris: ` -user `, ` -group `, et les différentes sorties et la poubelle Linux.


## Niveau 7 -> 8
But: parcourir un fichier txt, plus précisément retrouver un mot précis.

Méthode: Utilier la commande `grep` permettant de faire ressortir un motif précis dans un fichier donné.

Solution: `grep millionth data.txt`.

Appris: commande `grep` basique.


## Niveau 8 -> 9
But: repérer des lignes ou caractères qui n'apparaissent qu'une fois dans un fichier texte.

Méthode: Utiliser un pipe `|`, en l'associant aux commandes `sort` et `uniq`

Solution: `sort data.txt | uniq -u`

Appris: Commandes `|`, `sort` et `uniq`.


## Niveau 9 -> 10
But: repérer des caractères human-readable dans un fichier texte

Méthode: pareil que précédemment, degrossir une première fois puis appliquer une condition sur ce qu'il reste.

Solution: `strings data.txt | grep '==='`

Appris: `strings`

## Niveau 10 -> 11


