---
title: Développer des applications pour la plateforme Windows universelle (UWP) | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.technology:
- tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: stevehoag
ms.author: shoag
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: db88545393eeda280df898ee896f54123f4a1627
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251535"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Développer des applications pour la plateforme Windows universelle (UWP)
Avec la plateforme Windows universelle et notre noyau Windows, vous pouvez exécuter la même application sur n’importe quel appareil Windows 10, des téléphones jusqu’aux postes de travail. Créez ces applications Windows universelles avec Visual Studio et les outils de développement d’applications Windows universelles.

 ![Plateforme Windows universelle](../cross-platform/media/uwp_coreextensions.png "UWP_CoreExtensions")

 Exécutez votre application sur un téléphone Windows 10, un Bureau Windows 10 ou une console Xbox. C’est le même package d’application ! Avec l’introduction d’un noyau unifié unique dans Windows 10, le même package d’application peut s’exécuter sur toutes les plateformes. Plusieurs plateformes ont des kits SDK d’extension que vous pouvez ajouter à votre application pour bénéficier des comportements spécifiques à une plateforme. Par exemple, un SDK d’extension pour mobile gère le comportement du bouton Précédent sur un Windows Phone. Si vous référencez un kit SDK d’extension dans votre projet, il vous suffit ensuite d’ajouter des vérifications à l’exécution pour vérifier si ce kit SDK est disponible sur cette plateforme. C’est comme cela que vous pouvez utiliser le même package d’application pour toutes les plateformes !

 **Qu’est-ce que le noyau Windows ?**

 Pour la première fois, Windows a été refactorisé pour avoir un noyau commun sur toutes les plateformes Windows 10. Il y a donc maintenant un code source commun, un noyau Windows commun, une seule pile d’E/S de fichier et un modèle d’application unique. Pour l’interface utilisateur, il y a seulement un framework d’interface utilisateur XAML et un framework d’interface utilisateur HTML. Vous pouvez vous concentrer sur la création de l’application proprement dite, car nous avons fait en sorte qu’il soit facile de l’exécuter sur différents appareils Windows 10.

 **Qu’est-ce que la plateforme Windows universelle plus précisément ?**

La plateforme Windows universelle est simplement un ensemble de contrats et de versions. qui vous permettent de choisir les cibles d’exécution de votre application. Vous ne ciblez plus un système d’exploitation, mais une ou plusieurs familles d’appareils. Pour obtenir plus de détails, consultez [Introduction à la plateforme Windows universelle](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Configuration requise
 Les outils de développement d’applications Windows universelles sont fournis avec des émulateurs qui vous permettent de vérifier l’apparence de votre application sur différents appareils. Si vous souhaitez utiliser ces émulateurs, vous devez installer ce logiciel sur un ordinateur physique. L’ordinateur physique doit exécuter Windows 8.1 (x64) Professionnel ou une version ultérieure, et être équipé d’un processeur qui prend en charge Hyper-V Client et la conversion SLAT (Second Level Address Translation). Vous ne pouvez pas utiliser les émulateurs quand Visual Studio est installé sur un ordinateur virtuel.

 Voici la liste des logiciels dont vous avez besoin :

-   [Windows 10](http://windows.microsoft.com/windows/downloads). Visual Studio 2017 prend en charge le développement UWP uniquement sur Windows 10. Pour plus d’informations, consultez [Ciblage de la plateforme ](/visualstudio/productinfo/vs2017-compatibility-vs) et [Configuration requise](/visualstudio/productinfo/vs2017-system-requirements-vs) pour Visual Studio.

-   [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). Vous avez également besoin de la charge de travail de développement de la plateforme Windows universelle facultative.

     ![Charge de travail UWP](media/uwp_workload.png)

Après avoir installé ce logiciel, vous devez activer votre appareil Windows 10 pour le développement. Consultez [Activer votre appareil pour le développement](/windows/uwp/get-started/enable-your-device-for-development). Vous n’avez plus besoin d’une licence de développeur par appareil Windows 10.

## <a name="universal-windows-apps"></a>Applications pour la plateforme Windows universelle
Choisissez votre langage de développement préféré entre C#, Visual Basic, C++ ou JavaScript pour créer une application de plateforme Windows universelle pour les appareils Windows 10. Consultez [Créer votre première application](/windows/uwp/get-started/your-first-app) ou regardez la vidéo [Tools for Windows 10 Overview](http://channel9.msdn.com/Series/ConnectOn-Demand/229).

Si vous avez des applications Windows Store 8.1, Windows Phone 8.1 ou Windows universelles créées à l’aide de Visual Studio 2015, vous devez porter ces applications afin d’utiliser la dernière plateforme Windows universelle. Consultez [Passer de Windows Runtime 8.x à UWP](/windows/uwp/porting/w8x-to-uwp-root).

Après avoir créé votre application Windows universelle, vous devez l’empaqueter pour l’installer sur un appareil Windows 10 ou l’envoyer au Windows Store. Consultez [Création de packages d’application](/windows/uwp/packaging/index).

## <a name="see-also"></a>Voir aussi
[Développement mobile multiplateforme dans Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
