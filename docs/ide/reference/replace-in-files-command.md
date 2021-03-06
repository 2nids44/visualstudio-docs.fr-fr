---
title: Remplacer dans les fichiers, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8bf54892d17a877cd8e2c3ffd21ebd513e303d6c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946661"
---
# <a name="replace-in-files-command"></a>Remplacer dans les fichiers, commande
Remplace le texte dans les fichiers à l’aide d’un sous-ensemble des options proposées sous l’onglet **Remplacer dans les fichiers** de la fenêtre **Rechercher et remplacer**.

## <a name="syntax"></a>Syntaxe

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat`

 Obligatoire. Texte à rechercher.

 `replacewith`

 Obligatoire. Texte de remplacement du texte trouvé.

## <a name="switches"></a>Commutateurs
 /all ou /a

 Facultative. Remplace toutes les occurrences du texte recherché par le texte de remplacement.

 /case ou /c

 Facultative. Il y a correspondance uniquement quand les caractères majuscules et minuscules correspondent exactement à ceux spécifiés dans l’argument `findwhat`.

 /ext: `extensions`

 Facultative. Spécifie les extensions des fichiers dans lesquels effectuer la recherche.

 /keep ou /k

 Facultative. Spécifie que tous les fichiers modifiés restent ouverts.

 /lookin: `searchpath`

 Facultative. Répertoire dans lequel effectuer une recherche. Si le chemin contient des espaces, placez le chemin complet entre guillemets.

 /options ou /t

 Facultative. Affiche la liste des paramètres de recherche actuels et n’effectue pas de recherche.

 /regex ou /r

 Facultative. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant des modèles de texte, plutôt que des caractères littéraux. Pour obtenir la liste complète des caractères d’expressions régulières, consultez [Expressions régulières](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset ou /e

 Facultative. Rétablit les paramètres par défaut des options de recherche et n’effectue pas de recherche.

 /stop

 Facultative. Arrête l’opération de recherche en cours, le cas échant. Quand l’argument `/stop` a été spécifié, l’opération de remplacement ignore tous les autres arguments. Par exemple, pour arrêter le remplacement en cours, vous devez taper la syntaxe suivante :

```
>Edit.ReplaceinFiles /stop
```

 /sub ou /s

 Facultative. Recherche dans les sous-dossiers du répertoire qui est spécifié dans l’argument /lookin:`searchpath`.

 /text2 ou /2

 Facultative. Affiche les résultats du remplacement dans la fenêtre **Résultats de la recherche 2**.

 /wild ou /l

 Facultative. Utilise des caractères spéciaux prédéfinis dans l’argument `findwhat` comme notations représentant un caractère ou une séquence de caractères.

 /word ou /w

 Facultative. Recherche uniquement les mots entiers.

## <a name="example"></a>Exemple
 Cet exemple recherche `btnCancel` et le remplace par `btnReset` dans tous les fichiers .cls situés dans le dossier « My Visual Studio Projects », puis affiche les informations de remplacement dans la fenêtre **Résultats de la recherche 2**.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Voir aussi

- [Recherche et remplacement de texte](../../ide/finding-and-replacing-text.md)
- [Remplacer dans les fichiers](../../ide/replace-in-files.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)