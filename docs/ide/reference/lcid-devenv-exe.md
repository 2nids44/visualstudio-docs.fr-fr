---
title: -LCID (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac74f5275288cdba35d3a70f4a7813c800e4327d
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704718"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Définit la langue par défaut utilisée pour le texte, la monnaie et d’autres valeurs au sein de l’environnement de développement intégré (IDE, Integrated Development Environment).

## <a name="syntax"></a>Syntaxe

```cmd
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Arguments
 `LocaleID` Obligatoire. LCID (ID de paramètres régionaux) de la langue que vous spécifiez.

## <a name="remarks"></a>Notes
 Charge l’IDE et définit le langage naturel par défaut pour l’environnement. Ce changement est persistant d’une session à une autre et est répercuté dans le volet **Paramètres internationaux** des options **Environnement** de la boîte de dialogue **Options** dans l’IDE.

 Si la langue spécifiée n’est pas disponible sur le système de l’utilisateur, le commutateur /LCID est ignoré.

 Le tableau suivant répertorie les LCID des langues prises en charge par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|Langue|dans le dossier HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\|
|--------------|----------|
|Chinois (simplifié)|2052|
|Chinois (traditionnel)|1028|
|Anglais|1033|
|Français|1036|
|Allemand|1031|
|Italien|1040|
|Japonais|1041|
|Coréen|1042|
|Espagnol|3082|

## <a name="example"></a>Exemple
 Cet exemple charge l’IDE avec des chaînes de ressources en anglais.

```cmd
devenv /LCID 1033
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Paramètres internationaux, Environnement, boîte de dialogue Options](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md)