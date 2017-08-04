---
title: "Repr&#233;sentation JavaScript des types Windows Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "types Windows Runtime (JavaScript)"
  - "JavaScript, types Windows Runtime"
ms.assetid: f4851802-8b40-4afa-ba6c-8a162a9a43cc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Repr&#233;sentation JavaScript des types Windows Runtime
Le tableau suivant décrit la façon dont les types Windows Runtime sont représentés dans JavaScript.  
  
> [!IMPORTANT]
>  Les fonctionnalités de Windows Runtime ne sont pas disponibles pour les applications exécutées dans Internet Explorer.  
  
## Types Windows Runtime dans JavaScript  
  
|Type Windows Runtime.|Représentation JavaScript|Description|  
|---------------------------|-------------------------------|-----------------|  
|`UInt8`|`Number`|`Uint8` Windows Runtime est un entier 8 bits non signé, représenté comme un nombre de JavaScript.  Une valeur de JavaScript est d'abord convertie en nombre JavaScript, puis le processus `ToUint32` est suivi.  Si la valeur du nombre JavaScript est en dehors de la plage d'un Uint8, le modulo 2^8 sera appliqué au résultat.|  
|`Int32`|`Number`|Un `Int32` Windows Runtime est un entier 32 bits non signé, représenté comme un nombre JavaScript.  Une valeur de JavaScript est d'abord convertie en nombre JavaScript, puis le processus `ToInt32` est suivi.  Si la valeur du nombre JavaScript est en dehors de la plage d'un `Int32`, le modulo 2^16 sera appliqué au résultat.|  
|`Int64`|`Number`|Un `Int64` Windows Runtime est un entier 64 bits signé, représenté comme un nombre standard s'il se situe dans la plage \[\- 2^53, 2^53\].  S'il se situe en dehors de cette plage, il est représenté comme une valeur de nombre disposant d'un magasin de stockage personnalisé qui gère les 64 bits complets des données de type entier.  Toutes les opérations mathématiques effectuées sur ces valeurs de nombre personnalisé d'Int64 entraînent la conversion de la valeur en nombre standard dans la plage \[\- 2^53, 2^53\].  Si la valeur est en dehors de cette plage, une erreur de type est déclenchée.  Les exceptions à ce processus de conversion sont les opérations `==`, `===`, `SameValue`, et `RelationalComparison`, qui comparent les arguments en fonction des 64 bits complets lorsque deux valeurs représentées de 64 bits sont passées.  Si l'un ou l'autre des arguments est un nombre JavaScript standard, ces opérations convertissent également l'argument en un nombre JavaScript avant sa comparaison.  Une valeur JavaScript lui est assignée directement s'il a la valeur Int64 lui\-même ; si ce n'est pas le cas, le résultat de l'application de la conversion `ToInteger` sur la valeur est passé au Windows Runtime.  Si la contrainte de type échoue, une exception est retournée.|  
|`Uint64`|`Number`|Un `Uint64` Windows Runtime est un entier 64 bits non signé, représenté comme un nombre standard s'il se situe dans la plage \[0, 2^53\].  S'il se situe en dehors de cette plage, il est représenté comme un nombre disposant d'un magasin de stockage personnalisé qui gère les 64 bits complets des données non signées de type entier.  Toutes les opérations mathématiques effectuées sur ces valeurs de nombre personnalisé d'Uint64 entraînent la conversion de la valeur en nombre standard dans la plage \[0, 2^53\].  Si la valeur est en dehors de cette plage, une erreur de type est déclenchée.  Les exceptions à ce processus de conversion sont les opérations `==`, `===`, `SameValue`, et `RelationalComparison`, qui comparent les arguments en fonction des 64 bits complets lorsque deux valeurs de 64 bits sont passées.  Si l'un ou l'autre des arguments est un nombre JavaScript standard, ces opérations convertissent également l'argument en un nombre JavaScript avant sa comparaison.  Une valeur JavaScript est assignée directement si c'est une valeur Uint64 elle\-même ; dans le cas contraire, le résultat de l'application de la conversion `ToInteger` sur la valeur est passé à Windows Runtime, après avoir pris le modulo 2^52.  Si la conversion de type échoue, une exception est retournée.|  
|`Single`|`Number`|`Single` Windows Runtime est un nombre de 32 bits à virgule flottante, représenté comme un nombre JavaScript en sélectionnant la valeur double précision la plus proche de la valeur simple précision.  Une valeur JavaScript est convertie en nombre JavaScript puis contrôlée par plage pour vérifier que la valeur peut être représentée dans un nombre à virgule flottante IEEE 754 simple précision 32 bits.  Si la conversion ou le contrôle par plage échoue, une erreur de marshaling est retournée.|  
|`Double`|`Number`|Un `Double` Windows Runtime est un nombre à virgule flottante 64 bits.  `ToNumber` est utilisé pour convertir `Double` Windows Runtime en un nombre JavaScript.  Si la conversion échoue, une erreur de marshaling est retournée.|  
|`Boolean`|`Boolean`|Une valeur `Boolean` Windows Runtime est une valeur 8 bits pour laquelle le zéro a la valeur `false`. Si la valeur est autre que zéro, elle a la valeur `true`, représentée en tant que `Boolean` JavaScript.  Une valeur JavaScript est d'abord convertie en `Boolean` JavaScript par `ToBoolean`.  Cela signifie qu'une fonction Windows Runtime déclarée en tant que `void func(BOOL);` peut être écrite dans JavaScript en tant que `obj.func("test");`.  La fonction Windows Runtime est appelée avec le paramètre `BOOL` passé en tant que `TRUE`.  Si la conversion échoue, une erreur de marshaling est retournée.|  
|`Char16`|`String`|Un `Char16` Windows Runtime est un caractère Unicode 16 bits, représenté en tant que chaîne JavaScript contenant un caractère unique.  Une valeur de JavaScript est convertie en chaîne JavaScript par `ToString` puis vérifiée pour garantir que la longueur de la chaîne n'est que d'un seul caractère.  Le caractère unique est alors passé en tant que valeur `Char16`.  Si la conversion ou le contrôle de longueur échoue, une erreur de marshaling est retournée.|  
|`String`|`String`|Une `String` Windows Runtime est une séquence immuable d'objets `Char16`.  Les chaînes sont représentées comme des objets JavaScript `String`.  Pour les chaînes Windows Runtime, `null` et une chaîne vide \(« »\) ont la même valeur.  La valeur `null` et les valeurs de chaîne vide sont converties en une chaîne vide JavaScript.  Remarque : lorsque la valeur JavaScript `null` est passée à un paramètre Windows Runtime qui attend une chaîne, la valeur de chaîne produite est « null », et non pas `null` ou une chaîne vide \(« »\).  Les chaînes passées à Windows Runtime doivent toujours être instanciées en chaîne vide.|  
|`Enumeration`|`Object`|Une `Enumeration` Windows Runtime est un entier 32 bits \(signé ou non signé\) ayant une énumération composée associée de constantes nommées.  Dans JavaScript, une énumération est représentée comme un objet contenant un champ en lecture seule pour chaque valeur nommée.  Les valeurs d'énumération sont converties en nombres JavaScript comme défini précédemment pour `Int32` et `UInt32`.  Lorsqu'une valeur JavaScript est convertie en une énumération Windows Runtime, elle est convertie, tronquée et contrôlée par plage comme décrit précédemment.  Toutefois, la valeur résultante n'est pas vérifiée par rapport aux valeurs nommées définies spécifiées dans l'énumération.|  
|`Structure`|`Object`|Une `Structure` Windows Runtime est une collection hétérogène de champs de données nommés.  Dans JavaScript, une structure est représentée comme un objet JavaScript contenant une propriété nommée pour chaque champ de la structure.  Si la conversion d'une valeur de structure échoue, une erreur de marshaling est retournée.  Les champs dans l'objet JavaScript qui n'ont pas d'équivalents dans la structure Windows Runtime sont ignorés.  Remarque : une structure Windows Runtime ne peut pas être instanciée dans JavaScript avec le mot clé `new`.|  
|`Array`|`Array`|Un `Array` Windows Runtime est converti en tableau JavaScript.  Toutefois, les tableaux Windows Runtime ne sont pas redimensionnables et par conséquent, certaines opérations de tableau JavaScript sont impossibles.  La \[\[Class\]\] de propriété interne d'un tableau converti n'est pas configurée en « Array » car cela n'est pas autorisé par la spécification de ECMAScript 5.  Cela signifie que `Array.isArray(v)` retourne la valeur `false`.  Une valeur JavaScript est convertie en un tableau Windows Runtime comme suit : si la valeur est `null` ou `undefined`, elle est convertie en valeur native `null`.  Si sa \[\[Class\]\] interne de propriété est « Array », elle est copiée dans un tableau natif et une référence à ce tableau est passée.  S'il s'agit d'un tableau converti, comme décrit précédemment, le tableau natif sous\-jacent est passé.  Remarque : passer une valeur de tableau JavaScript à une méthode Windows Runtime provoque une copie complète du tableau.|  
|Délégué \(fonction de rappel\)|`Function`|Un délégué Windows Runtime est une référence à une méthode unique.  Un délégué Windows Runtime est représenté dans JavaScript en tant que `Function` JavaScript, dont l'appel sur le thread est garanti.  Lorsque la `Function` est appelée, les arguments sont convertis en types de paramètre Windows Runtime équivalents.  S'il y a moins arguments JavaScript que de paramètres délégués `in`, l'appel du délégué échoue.  S'il y a plus d'arguments JavaScript que de paramètres `in` dans le délégué, les arguments JavaScript supplémentaires sont ignorés.  Une fois que le délégué est appelé, les paramètres `out` sont convertis en types JavaScript et retournés.  Si un objet de fonction JavaScript natif est converti en un délégué Windows Runtime, il est encapsulé dans un délégué Windows Runtime du type correspondant.  Lorsque le délégué est appelé, les paramètres `in` sont convertis en types JavaScript.  Une fois que le délégué est appelé, la valeur de retour est convertie en paramètres `out` du délégué.|  
|Interface|`Object`|Les interfaces et les groupes d'interfaces ne sont pas représentés directement dans JavaScript en tant qu'objets.  Toutefois, les interfaces sont représentées comme paramètre et retournent des types de méthodes Windows Runtime.  Une instance d'interface Windows Runtime est convertie comme suit :<br /><br /> 1.  S'il existe une classe Windows Runtime valide, elle représente l'objet en tant qu'instance de cette classe.<br />2.  S'il n'existe aucune classe d'exécution valide, elle représente l'objet en tant qu'instance d'une classe d'exécution sans nom qui implémente exactement l'interface dont l'instance est connue pour implémenter, plus ses interfaces requises.<br /><br /> Une valeur JavaScript est testée pour déterminer s'il s'agit d'une instance d'une classe d'exécution ou d'une interface.  Si tel est le cas, et que la valeur Windows Runtime d'origine implémente l'interface, l'objet est passé à Windows Runtime.|  
|Classes de runtime|`Object`|Les objets Windows Runtime peuvent être des instances de classes de runtime qui implémentent une ou plusieurs interfaces.  Les objets Windows Runtime sont représentés dans JavaScript en tant qu'objets.  L'union des méthodes, propriétés et événements définie dans toutes les interfaces implémentées dans la classe, représente les propriétés nommées dans le prototype de l'objet JavaScript.  Les consommateurs JavaScript peuvent accéder directement à un membre de la classe.  Les objets Windows Runtime ont un prototype contenant tous les membres de toutes les interfaces implémentées de la classe de runtime.|  
  
## Voir aussi  
 [Utilisation de Windows Runtime dans JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)