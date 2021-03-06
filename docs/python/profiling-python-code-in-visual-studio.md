---
title: Mesure des performances du code Python
description: Guide pratique pour utiliser le profileur Visual Studio pour vérifier les performances du code Python en cas d’utilisation d’interpréteurs CPython.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: feafc7d53e8d450bc980b6d842e9c2a5f0ade2e4
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468814"
---
# <a name="profile-python-code"></a>Profiler du code Python

Vous pouvez profiler une application Python si des interpréteurs CPython sont utilisés. (Consultez [Profilage dans la matrice des fonctionnalités](overview-of-python-tools-for-visual-studio.md#matrix-profiling) pour connaître la disponibilité de cette fonctionnalité dans les différentes versions de Visual Studio.)

## <a name="profiling-for-cpython-based-interpreters"></a>Profilage pour les interpréteurs CPython

La commande de menu **Analyser** > **Lancer le profilage Python** permet de lancer le profilage, ce qui entraîne l’ouverture d’une boîte de dialogue de configuration :

![Boîte de dialogue de configuration du profilage](media/profiling-start.png)

Lorsque vous sélectionnez **OK**, le profileur s’exécute et ouvre un rapport de performances vous permettant de connaître la répartition du temps dans l’application :

![Rapport de performances de profilage](media/profiling-results.png)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo") | [Regardez une vidéo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567) pour obtenir une démonstration du profilage de Python (3 min00s).|

> [!Note]
> Actuellement, Visual Studio ne prend en charge que ce niveau de profilage sur l’application tout entière, mais nous serions ravis de recevoir vos commentaires sur les fonctionnalités à venir. Utilisez le [bouton **Faire des commentaires sur les produits** ](#feedback) au bas de cette page.

## <a name="profiling-for-ironpython"></a>Profilage pour IronPython

IronPython n’étant pas un interpréteur CPython, la fonctionnalité de profilage ci-dessus ne fonctionne pas.

Utilisez plutôt le profileur Visual Studio .NET en lançant *ipy.exe* directement en tant qu’application cible. Utilisez les arguments appropriés pour lancer votre script de démarrage. Ajoutez `-X:Debug` sur la ligne de commande pour s’assurer que l’ensemble de votre code Python peut être débogué et profilé. Cet argument génère un rapport de performances qui inclut le temps passé dans le runtime IronPython et votre code. Votre code est identifié à l’aide de noms tronqués.

IronPython possède également ses fonctionnalités de profilage intégrées, mais à ce jour, aucun visualiseur approprié n’est disponible pour celles-ci. Consultez [An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Un profileur IronPython) (blogs MSDN) pour connaître ce qui est disponible.