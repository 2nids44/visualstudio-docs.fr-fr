---
title: "Apply, méthode (Function) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- apply
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Apply method
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a06a37006937b07214bf5a314d5151c3b658acf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="apply-method-function-javascript"></a>apply, méthode (Function) (JavaScript)
Appelle la fonction, en remplaçant l’objet spécifié pour le `this` la valeur de la fonction et le tableau spécifié pour les arguments de la fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
apply([thisObj[,argArray]])  
```  
  
## <a name="parameters"></a>Paramètres  
 `thisObj`  
 Facultatif. L’objet à utiliser comme le `this` objet.  
  
 `argArray`  
 Facultatif. Un jeu d’arguments à passer à la fonction.  
  
## <a name="remarks"></a>Remarques  
 Si `argArray` n’est pas un objet valide, une erreur « Objet attendu » se produit.  
  
 Si ni `argArray` ni `thisObj` sont fournis, la version d’origine `this` objet est utilisé comme `thisObj` et aucun des arguments ne sont passés.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser la méthode apply.  
  
```JavaScript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de function](../../javascript/reference/function-object-javascript.md)