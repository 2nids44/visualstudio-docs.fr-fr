---
title: "Définir le thread en cours, commande │ Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 18c417016071cc25bdccde1c85e97431f20195d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="set-current-thread-command"></a>Définir le thread en cours, commande
Définit le thread spécifié comme thread actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Obligatoire. Sélectionne un thread par son index.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commande Visual Studio](../../ide/reference/visual-studio-command-aliases.md)