---
title: 'Erreur : Le processus cible s’est arrêté avec le code &#39;code&#39; lors de l’évaluation de la fonction &#39;fonction&#39; | Documents Microsoft'
ms.custom: ''
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5e9221ccf162180a89cc88b1ceebcf55be39eef
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922509"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Erreur : Le processus cible s’est arrêté avec le code &#39;code&#39; lors de l’évaluation de la fonction &#39;(fonction)&#39;

Texte du message complet : le processus cible s’est arrêté avec le code 'code' lors de l’évaluation de la fonction 'fonction'.

Pour faciliter l’inspecter l’état des objets .NET, le débogueur force automatiquement le processus débogué à exécuter du code supplémentaire (en général, les méthodes d’accesseur Get de propriété et `ToString` fonctions). Dans la plupart des scénarios, ces fonctions terminent correctement ou lever des exceptions qui peuvent être interceptées par le débogueur. Toutefois, il existe certains cas dans lequel les exceptions ne peuvent pas être interceptées, car elles franchissent les limites de noyau, nécessitent le pompage de messages utilisateur ou sont irrécupérables. Un résultat, un accesseur Get de propriété ou la méthode ToString qui exécute le code qui soit explicitement met fin au processus (par exemple, appelle `ExitProcess()`) ou lève une exception non gérée ne peut pas être interceptée (par exemple, `StackOverflowException`) mettra fin à la processus débogué et fin de la session de débogage. Si vous rencontrez ce message d’erreur, cela s’est produite.
 
Une des raisons courantes de ce problème sont que lorsque le débogueur évalue une propriété qui s’appelle elle-même, cela peut entraîner une exception de dépassement de capacité de pile. L’exception de dépassement de capacité de pile ne peuvent pas être récupérée et que le processus cible va se terminer.
 
## <a name="to-correct-this-error"></a>Pour corriger cette erreur
 
Il existe deux solutions possibles à ce problème.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Solution #1 : Empêcher le débogueur à partir de l’appel de la propriété d’accesseur Get ou la méthode ToString 

Le message d’erreur vous indique le nom de la fonction que le débogueur a essayé d’appeler. Avec le nom de la fonction, vous pouvez essayer de réévaluer cette fonction à partir de la **exécution** fenêtre pour déboguer l’évaluation. Le débogage est possible lors de l’évaluation de la **immédiat** fenêtre car, contrairement aux évaluations implicites à partir de la **automatique/variables locales/espion** windows, le débogueur s’arrête sur les exceptions non gérées.

Si vous pouvez modifier cette fonction, vous pouvez empêcher le débogueur de l’appel de l’accesseur Get de propriété ou `ToString` (méthode). Essayez l’une des opérations suivantes :
 
* Modifier la méthode en un autre type de code en dehors d’un accesseur Get de propriété ou méthode ToString et le problème disparaîtra.
    - ou -
* (Pour `ToString`) définir un `DebuggerDisplay` attribut sur le type et vous pouvez que le débogueur évaluer un élément autre que `ToString`.
    - ou -
* (Pour un accesseur Get de propriété) Placez le `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` attribut sur la propriété. Cela peut être utile si vous avez une méthode qui doit rester une propriété pour des raisons de compatibilité d’API, mais il doit être réellement d’une méthode.

Si vous ne pouvez pas modifier cette méthode, vous pourrez peut-être arrêter le processus cible à une autre instruction, puis réessayez de l’évaluation.
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>Solution #2 : Désactiver tous les évaluation implicite
 
Si les solutions précédentes ne résout le problème, accédez à **outils** > **Options**et désactivez le paramètre **débogage**  >   **Général** > **activer l’évaluation de la propriété et d’autres appels de fonction implicite**. Cela désactive la plupart des évaluations de fonction implicite et devrait résoudre le problème.



  
