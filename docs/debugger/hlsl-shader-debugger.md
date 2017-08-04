---
title: "D&#233;bogueur du nuanceur HLSL | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics.shaderviewer"
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;bogueur du nuanceur HLSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le débogueur HLSL de Visual Studio Graphics Analyzer vous aide à comprendre comment votre code de nuanceur HLSL s'exécute dans les conditions réelles de fonctionnement de votre application.  
  
 Il se présente comme suit :  
  
 ![Débogage HLSL utilisant la fenêtre de la pile des appels et la fenêtre espion.](../debugger/media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx\_diag\_demo\_hlsl\_debugger\_orientation")  
  
## Présentation du débogueur HLSL  
 Le débogueur HLSL peut vous aider à comprendre les problèmes qui surviennent dans votre code de nuanceur.  Le débogage du code HLSL dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ressemble au débogage du code écrit dans un autre langage, par exemple, C\+\+, C\# ou Visual Basic.  Vous pouvez examiner le contenu des variables, définir des points d'arrêt, parcourir le code, et remonter la pile d'appels, comme lorsque vous déboguez d'autres langages.  
  
 Toutefois, comme les GPU atteignent des performances élevées via l'exécution du code de nuanceur sur des centaines de threads simultanément, le débogueur HLSL est conçu pour collaborer avec les autres outils Graphics Analyzer pour afficher toutes ces informations et en faciliter le décryptage.  Graphics Analyzer recrée les frames capturés en utilisant les informations stockées dans un journal de graphisme. Le débogueur HLSL ne contrôle pas l'exécution du GPU en temps réel quand il exécute le code d'un nuanceur.  Dans la mesure où un journal de graphisme contient suffisamment d'informations pour recréer une partie de la sortie, et où Graphics Analysis fournit des outils permettant de désigner exactement le pixel et l'événement précis où se produit une erreur, le débogueur HLSL doit simplement simuler le thread nuanceur qui vous intéresse.  Cela signifie que le travail du nuanceur peut être simulé sur l'UC, où les mécanismes internes sont affichés en plein écran.  Cela permet au débogueur HLSL de bénéficier d'une expérience de débogage similaire à celle de l'UC.  
  
 Toutefois, le débogueur HLSL est actuellement limité comme suit :  
  
-   Le débogueur HLSL ne prend pas en charge l'option Modifier & Continuer. Toutefois, vous pouvez apporter des changements à vos nuanceurs et régénérer ensuite le frame pour voir les résultats.  
  
-   Il est impossible de déboguer une application et son code de nuanceur simultanément.  Toutefois, vous pouvez les alterner.  
  
-   Vous pouvez ajouter des variables et des registres à la fenêtre Espion, mais les expressions ne sont pas prises en charge.  
  
 Néanmoins, le débogueur HLSL offre une expérience de débogage meilleure et plus similaire à celle de l'UC.  
  
## Modification et application du nuanceur HLSL  
 Le débogueur du nuanceur HLSL ne prend pas en charge Modifier & Continuer de la même manière que le débogueur d'UC, car le modèle d'exécution du GPU n'autorise pas l'annulation de l'état du nuanceur.  À la place, le débogueur HLSL prend en charge Modifier & Appliquer, ce qui vous permet de changer les fichiers sources HLSL, puis de choisir **Appliquer** pour régénérer le frame et voir le résultat de vos changements.  Votre code de nuanceur modifié est stocké dans un fichier distinct pour préserver l'intégrité du fichier source HLSL d'origine de votre projet. Toutefois, quand vous êtes satisfait de vos changements, vous pouvez choisir **Copier dans...** pour copier les changements dans votre projet.  À l'aide de cette fonctionnalité, vous pouvez rapidement itérer le code du nuanceur qui contient des erreurs, et éliminer les étapes coûteuses de régénération et de capture dans votre flux de travail de débogage HLSL.  
  
## Code machine HLSL  
 Le débogueur du nuanceur HLSL fournit une liste d'assemblys du nuanceur HLSL à droite de la liste de codes source HLSL.  
  
## Débogage du code HLSL  
 Vous pouvez accéder au débogueur HLSL à partir de la fenêtre Étapes de canalisation ou Historique des pixels.  
  
#### Pour démarrer le débogueur HLSL à partir de la fenêtre Étapes de canalisation Graphics  
  
1.  Dans la fenêtre **Étapes de canalisation Graphics**, recherchez l'étape de pipeline associée au nuanceur que vous souhaitez déboguer.  
  
2.  Sous le titre de l'étape de pipeline, choisissez **Démarrer le débogage**, qui apparaît sous la petite flèche verte.  
  
    > [!NOTE]
    >  Ce point d'entrée dans le débogueur HLSL débogue uniquement le premier thread nuanceur pour l'étape correspondante, c'est\-à\-dire le premier vertex ou le premier pixel qui est traité.  Vous pouvez utiliser la fonctionnalité Historique des pixels pour accéder à d'autres threads de ces étapes du nuanceur.  
  
#### Pour démarrer le débogueur HLSL de l'historique des pixels Graphics  
  
1.  Dans la fenêtre **Historique des pixels Graphics**, développez l'appel de dessin associé au nuanceur que vous souhaitez déboguer.  Chaque appel de dessin peut correspondre à plusieurs primitives.  
  
2.  Dans les détails de l'appel de dessin, développez une primitive dont la contribution de couleur résultante indique un bogue dans son code shader.  Si plusieurs primitives indiquent un bogue, choisissez la première afin d'éviter une accumulation d'erreurs pouvant rendre le diagnostic du problème plus difficile.  
  
3.  Dans les détails de primitives, choisissez de déboguer le **Nuanceur de sommets** ou le **Nuanceur de pixels**.  Déboguez le nuanceur de sommets lorsque vous suspectez que le nuanceur de pixels est correct mais qu'il génère une proportion incorrecte de couleur car le nuanceur de sommets lui passe des constantes incorrectes.  Sinon, déboguez le nuanceur de pixels.  
  
     À droite du nuanceur choisi, choisissez **Démarrer le débogage**, qui apparaît sous la petite flèche verte.  
  
    > [!NOTE]
    >  Ce point d'entrée dans le débogueur HLSL débogue soit le thread nuanceur de pixels qui correspond à l'appel de dessin choisi, à la primitive, et au pixel que vous avez choisis, soit les threads de nuanceur de sommets dont les résultats sont interpolés par l'appel de dessin, la primitive, et le pixel que vous avez choisis.  Dans le cas des nuanceurs de sommets, vous pouvez affiner davantage le point d'entrée à un sommet spécifique en développant les détails du nuanceur de sommets.  
  
 Pour obtenir des exemples d'utilisation du débogueur HLSL pour déboguer les erreurs de nuanceur, consultez [Exemples Graphics Diagnostics](../debugger/graphics-diagnostics-examples.md) ou les procédures pas à pas liées dans la section Voir aussi.  
  
## Voir aussi  
 [Procédure pas à pas : objets manquants en raison de Vertex Shader](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Procédure pas à pas : débogage des erreurs de rendus dues à la trame](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)   
 [Procédure pas à pas : utilisation de Graphics Diagnostics pour déboguer un Shader de calcul](../debugger/walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)