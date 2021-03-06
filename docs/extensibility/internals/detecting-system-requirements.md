---
title: Detecting System Requirements | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a794391001934164e52bdd73d940cb73ff3b5f3b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500080"
---
# <a name="detect-system-requirements"></a>Détecter la configuration système requise
Un VSPackage ne peut pas fonctionner, sauf si Visual Studio est installé. Lorsque vous utilisez le programme d’installation de Microsoft Windows pour gérer l’installation de votre VSPackage, vous pouvez configurer le programme d’installation pour détecter si Visual Studio est installé. Vous pouvez également configurer pour vérifier le système pour d’autres exigences, par exemple, une version particulière de Windows ou une quantité spécifique de mémoire vive.  
  
## <a name="detect-visual-studio-editions"></a>Détecter les éditions de Visual Studio  
 Pour déterminer si une édition de Visual Studio est installée, vérifiez que la valeur de la **installer** clé de Registre est *(REG_DWORD) 1* dans le dossier approprié, comme répertorié dans le tableau suivant. Notez qu’il existe une hiérarchie des éditions de Visual Studio :  
  
1.  Entreprise  
  
2.  Professionnel  
  
3.  Communauté  
      
Lorsqu’une version plus récente est installée, les clés de Registre pour cette édition sont ajoutés, ainsi que pour les éditions antérieures. Autrement dit, si l’édition Enterprise est installée, le **installer** clé est définie sur *1* pour l’entreprise, ainsi que pour les éditions Professional et Community. Par conséquent, vous devez ne vérifier que pour la version la plus récente que vous avez besoin.  
  
> [!NOTE]
>  Dans la version 64 bits de l’Éditeur du Registre, les clés de 32 bits sont affichées sous **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. Les clés de Visual Studio sont sous **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.  
  
|Produit|Touche|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (intégré et isolé)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detect-when-visual-studio-is-running"></a>Détecter quand Visual Studio est en cours d’exécution  
 Votre package Visual Studio ne peut pas être inscrit correctement si Visual Studio est en cours d’exécution lorsque le VSPackage est installé. Le programme d’installation doit détecter lorsque Visual Studio est en cours d’exécution et refuser puis à installer le programme. Programme d’installation de Windows ne vous permettent d’utiliser les entrées de table pour activer la détection de ce type. Au lieu de cela, vous devez créer une action personnalisée, comme suit : utilisez le `EnumProcesses` (fonction) pour détecter les *devenv.exe* traiter et ensuite définir une propriété du programme d’installation qui est utilisée dans une condition de lancement ou afficher une boîte de dialogue de manière conditionnelle Pour inviter l’utilisateur de fermer Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer des VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)