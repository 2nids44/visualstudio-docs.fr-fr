---
title: "ScriptEngine, fonction (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ScriptEngine"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngine (fonction)"
ms.assetid: 65674b2b-d2c2-4493-99b3-f0d20fda8249
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# ScriptEngine, fonction (JavaScript)
Obtient le nom du langage de script utilisé.  
  
## Syntaxe  
  
```  
ScriptEngine()  
```  
  
## Notes  
 La fonction `ScriptEngine` retourne « JScript », qui indique que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] est le moteur de script actuel.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `ScriptEngine` :  
  
```javascript  
if (window.ScriptEngine) {  
    console.log(window.ScriptEngine());  
}  
  
// Output: JScript  
```  
  
## Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Voir aussi  
 [ScriptEngineBuildVersion, fonction](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion, fonction](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion, fonction](../../javascript/reference/scriptengineminorversion-function-javascript.md)