---
title: Fonctions de raccordement de bloc client | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee0209c082185e111988e5f8e39f2f0b806a4995
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433117"
---
# <a name="client-block-hook-functions"></a>Fonctions de raccordement de bloc client
Si vous voulez valider ou reporter le contenu des données stockées dans des blocs `_CLIENT_BLOCK`, vous pouvez écrire une fonction spécialement dans ce but. Cette fonction doit avoir un prototype similaire au suivant, défini dans CRTDBG.H :  
  
```cpp
void YourClientDump(void *, size_t)  
  
```  
  
 En d’autres termes, votre fonction de raccordement doit accepter un **void** pointeur vers le début du bloc d’allocation, avec une **size_t** type valeur qui indique la taille de l’allocation et de retourner `void`. Pour le reste, son contenu dépend de vous.  
  
 Une fois que vous avez installé votre fonction de raccordement avec [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), elle sera appelée chaque fois qu’un `_CLIENT_BLOCK` bloc. Vous pouvez ensuite utiliser [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) pour obtenir des informations sur le type ou le sous-type des blocs sauvegardées.  
  
 Le pointeur vers votre fonction que vous passez à `_CrtSetDumpClient` est de type **_CRT_DUMP_CLIENT**, tel que défini dans CRTDBG. H :  
  
```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)
