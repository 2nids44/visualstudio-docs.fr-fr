---
title: Comment puis-je déboguer des fonctions API Windows ? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 042f243c0469b8b37e301cf5c9f2410cf201f7be
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058604"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Comment puis-je déboguer des fonctions API Windows ?
Si vous voulez déboguer une fonction API Windows qui a chargé les symboles NT, vous devez effectuer les opérations suivantes.  
  
### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Pour définir un point d'arrêt sur une fonction API Windows qui a chargé des symboles NT  
  
-   Entrez le nom de la fonction ainsi que le nom du fichier DLL dans lequel la fonction réside. Dans du code 32 bits, utilisez la forme décorée du nom de la fonction. Pour définir un point d’arrêt sur **MessageBeep**, par exemple, vous devez entrer ce qui suit.  
  
    ```cpp
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     Pour obtenir le nom décoré, consultez [affichage de noms décorés](http://msdn.microsoft.com/en-us/f79e2717-a4db-4d12-a689-69830cce2be0).  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions de débogage du Code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
