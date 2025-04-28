# Get Next Line (GNL)

Le projet Get Next Line (GNL) consiste à implémenter une fonction qui permet de lire une ligne à partir d'un fichier ou de l'entrée standard, et de renvoyer cette ligne sous forme de chaîne de caractères. Cette fonction doit gérer les lectures successives et les mémoriser de manière efficace.

## Description

- **get_next_line** : Cette fonction lit une ligne à partir d'un fichier ou de l'entrée standard. Elle lit les données par morceaux, jusqu'à ce qu'une nouvelle ligne (séparée par le caractère `\n`) soit rencontrée.
- **Mémoire** : Chaque ligne lue est renvoyée à l'appelant, et la mémoire utilisée est libérée une fois la ligne retournée.
- **Fichier** : L'implémentation doit pouvoir lire depuis n'importe quel fichier, et gérer plusieurs descripteurs de fichiers (comme l'entrée standard).
- **Fonctions auxiliaires** : Des fonctions auxiliaires sont utilisées pour traiter les chaînes de caractères et gérer la mémoire de manière efficace.

## Installation

```bash
git clone https://github.com/sbr93z/get_next_line.git
```
Utilisation

Inclure le header dans votre code et utiliser la fonction get_next_line pour lire une ligne :
```C
#include "get_next_line.h"

int main() {
    int fd = open("file.txt", O_RDONLY);
    char *line;

    while ((line = get_next_line(fd)) != NULL) {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```
## Exemple de sortie :
```bash
Ligne 1
Ligne 2
Ligne 3
```

## Fichiers

get_next_line/get_next_line.c : Implémentation de la fonction `get_next_line` qui lit une ligne à partir d'un fichier.

get_next_line/get_next_line_bonus.c : Version avec une gestion des fichiers multiples et des cas bonus.

get_next_line/get_next_line.h : Header principal contenant les déclarations des fonctions et des structures nécessaires.

get_next_line/get_next_line_utils.c : Fonctions utilitaires pour la gestion des chaînes de caractères.

get_next_line/get_next_line_utils_bonus.c : Fonctions utilitaires supplémentaires pour les cas bonus.

## Commandes Makefile
```bash
make : Compile les programmes.

make clean : Supprime les fichiers objets.

make fclean : Supprime les fichiers objets et les exécutables.

make re : fclean puis make.
```
## Fonctionnement

La fonction get_next_line lit les données depuis un fichier ou l'entrée standard, et renvoie la prochaine ligne disponible. Elle continue de lire les lignes jusqu'à ce qu'il n'y ait plus de données à lire. La gestion de la mémoire est réalisée en libérant la ligne après chaque lecture.

Le projet implémente des versions bonus qui gèrent des fichiers multiples et optimisent les performances pour la lecture de grandes quantités de données.
