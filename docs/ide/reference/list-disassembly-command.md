---
title: Afficher le code machine, commande
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64951810020d99239a47b9c6bdba751b2c0a3dfd
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704731"
---
# <a name="list-disassembly-command"></a>Afficher le code machine, commande
Commence le processus de débogage et permet de spécifier comment les erreurs sont gérées.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Commutateurs
 Chaque commutateur peut être appelé à l’aide de sa forme complète ou abrégée.

 /count: `number` [ou] /c: `number` [ou] /length: `number` [ou] /l: `number`

 Facultative. Nombre d’instructions à afficher. La valeur par défaut est 8.

 /endaddress: `expression` [ou] /e: `expression`

 Facultative. Adresse à laquelle le code machine doit s’arrêter.

 /codebytes:`yes`&#124;`no` [ou] /bytes:`yes`&#124;`no` [ou] /b:`yes`&#124;`no`

 Facultative. Spécifie si les octets de code doivent être affichés. La valeur par défaut est `no`.

 /source:`yes`&#124;`no` [ou] /s:`yes`&#124;`no`

 Facultative. Spécifie si le code source doit être affiché. La valeur par défaut est `no`.

 /symbolnames:`yes`&#124;`no` [ou] /names:`yes`&#124;`no` [ou] /n:`yes`&#124;`no`

 Facultative. Spécifie si les noms de symbole doivent être affichés. La valeur par défaut est `yes`.

 [/linenumbers:`yes`&#124;`no`]

 Facultative. Active l’affichage des numéros de ligne associés au code source. Le commutateur /source doit avoir la valeur `yes` pour utiliser le commutateur /linenumbers.

## <a name="example"></a>Exemple

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Voir aussi

- [Afficher la pile des appels, commande](../../ide/reference/list-call-stack-command.md)
- [Répertorier les threads, commande](../../ide/reference/list-threads-command.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)