---
title: -Run (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e10b12729ed8f547c2658c0f4ce6ece84a12dbe
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704627"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
Compile et exécute la solution ou le projet spécifié.

## <a name="syntax"></a>Syntaxe

```cmd
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>Arguments
 `SolutionName`

 Obligatoire. Chemin complet et nom d’un fichier solution.

 `ProjectName`

 Obligatoire. Chemin complet et nom d’un fichier projet.

## <a name="remarks"></a>Notes
 Compile et exécute la solution ou le projet spécifié en fonction des paramètres spécifiés pour la configuration de la solution active. Ce commutateur lance l’environnement de développement intégré (IDE) et le maintient actif à la fin de l’exécution du projet ou de la solution.

-   Placez entre guillemets doubles les chaînes contenant des espaces.

-   Les informations résumées, notamment les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/out`.

## <a name="example"></a>Exemple
 Cet exemple exécute la solution `MySolution` en utilisant la configuration de déploiement active.

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)