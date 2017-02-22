---
title: "IDebugStackFrame2::GetThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetThread"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetThread"
ms.assetid: cbeef85b-3dd7-4f97-adc2-c4d197d979fc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le thread associé à un frame de pile.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetThread (   
   IDebugThread2** ppThread  
);  
```  
  
```c#  
int GetThread (   
   out IDebugThread2 ppThread  
);  
```  
  
#### Paramètres  
 `ppThread`  
 \[out\]  Retourne un objet d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) qui représente le thread.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)