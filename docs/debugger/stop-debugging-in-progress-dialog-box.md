---
title: Arrêter le débogage dans la boîte de dialogue Progression | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe7eca0124869a9c636738c8641f5d2e97e63404
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475681"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Arrêt du débogage en cours (boîte de dialogue)
Cette boîte de dialogue s'affiche lorsque le débogueur tente d'arrêter une session de débogage, mais que l'arrêt de la session prend du temps. L'arrêt d'une session de débogage est généralement très rapide et cette boîte de dialogue ne s'affiche pas. Cependant, il arrive que l'opération prenne du temps pour détacher tous les processus débogués. Si l'arrêt de la session dépasse quelques secondes (ou si une erreur de détachement se produit), cette boîte de dialogue apparaît. Si cela se produit fréquemment, cela peut être dû à un problème interne et vous pouvez contacter le Support Technique Microsoft.  
  
 Vous pouvez attendre les détachement des processus et cette boîte de dialogue disparaît, ou utiliser le **arrêter maintenant** bouton pour forcer l’arrêt immédiat.  
  
 **Arrêter maintenant**  
 Cliquez sur le bouton pour terminer immédiatement la session de débogage. À l’aide de **arrêter maintenant** va se terminer au lieu de détachement du processus en cours de débogage. Si vous déboguez des processus système, arrêt de ces processus avec **arrêter maintenant** peut avoir des effets inattendus et indésirables.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Détachement de programmes](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)