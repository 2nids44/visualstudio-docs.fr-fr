---
title: 'Comment : spécifier une Version du .NET Framework pour le débogage | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2cb8da54b53814e7f044c67855e8071c627cf2e1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476671"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Comment : spécifier une version .NET Framework pour le débogage
Le débogueur [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] prend en charge le débogage des versions antérieures ainsi que de la version actuelle de Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Si vous démarrez une application à partir de Visual Studio, le débogueur identifie toujours la version correcte de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] pour l’application que vous déboguez. Si l’application est déjà en cours d’exécution et que vous utilisez **attacher à**, le débogueur pas peut toujours être en mesure d’identifier une version antérieure de le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Si cela se produit, un message d'erreur s'affiche qui indique,  
  
 Le débogueur a évalué de façon incorrecte la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que votre application va utiliser.  
  
 Dans ces cas rares, vous pouvez définir une clé de Registre pour indiquer au débogueur la version à utiliser.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Pour spécifier une version .NET Framework pour le débogage  
  
1.  Recherchez dans le répertoire Windows\Microsoft.NET\Framework les versions du .NET Framework installées sur votre ordinateur. Les numéros de version sont similaires à ceci :  
  
     `V1.1.4322`  
  
     Identifiez le numéro de version correct et prenez-en note.  
  
2.  Démarrer le **Éditeur du Registre** (regedit).  
  
3.  Dans le **Éditeur du Registre**, ouvrez le dossier HKEY_LOCAL_MACHINE.  
  
4.  Accédez à : HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Si la clé n’existe pas, cliquez sur HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine, puis cliquez sur **nouvelle clé**. Nommez la nouvelle clé `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Après avoir navigué à {449EC4CC-30D2-4032-9256-EE18EB41B62B}, recherchez dans le **nom** colonne et la clé CLRVersionForDebugging.  
  
    1.  Si la clé n’existe pas, cliquez sur {449EC4CC-30D2-4032-9256-EE18EB41B62B}, puis cliquez sur **nouvelle valeur de chaîne**. Cliquez sur la nouvelle valeur de chaîne, cliquez sur **renommer**et le type `CLRVersionForDebugging`.  
  
6.  Double-cliquez sur **CLRVersionForDebugging**.  
  
7.  Dans le **modification de la chaîne** , tapez le numéro de version de .NET Framework dans le **valeur** boîte. Par exemple : V1.1.4322  
  
8.  Cliquez sur **OK**.  
  
9. Fermer le **Éditeur du Registre**.  
  
     Si vous obtenez encore un message d'erreur lorsque vous commencez à déboguer, vérifiez que vous avez entré correctement le numéro de version dans le Registre. Assurez-vous également que la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que vous utilisez est prise en charge par Visual Studio. Le débogueur est compatible avec la version actuelle et les versions antérieures du .NET Framework, mais il n'offre peut-être pas une compatibilité ascendante avec les futures versions.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)