---
title: "Mettre à niveau Dotfuscator Community Edition (CE) | Microsoft Docs"
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protection, Community Edition, obfuscation, .NET, gratuit, Visual Studio 2017, mettre à niveau, ligne de commande"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: "Découvrez comment mettre à jour la version gratuite de Dotfuscator Community Edition incluse dans Visual Studio 2017."
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 60ca38639f6523cdbace4efa4aa48b48d5e9a886
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---

# Mettre à niveau Dotfuscator Community Edition (CE)
<a id="upgrade-dotfuscator-community-edition-ce" class="xliff"></a>

Dotfuscator Community Edition (Dotfuscator CE) offre immédiatement de nombreuses fonctionnalités de renforcement et de protection des applications à tous les développeurs utilisant Microsoft Visual Studio.
Toutefois, les utilisateurs qui mettent à niveau leur version de Dotfuscator peuvent disposer de fonctionnalités supplémentaires.

## Inscription de Dotfuscator CE
<a id="registering-dotfuscator-ce" class="xliff"></a>

Les utilisateurs de Dotfuscator inscrits peuvent accéder à des fonctionnalités supplémentaires, telles que la [prise en charge des lignes de commande][cli], ce qui permet d’intégrer facilement Dotfuscator CE au processus de génération automatisé.

L’inscription est rapide, simple et gratuite.
Pour inscrire Dotfuscator CE, consultez [la section relative à l’inscription de Dotfuscator CE dans la page de prise en main du guide d’utilisation complet de Dotfuscator CE][register-ce].

## Dotfuscator Professional
<a id="dotfuscator-professional" class="xliff"></a>

Alors que Dotfuscator Community Edition fournit un niveau de protection de base, **_PreEmptive Protection - Dotfuscator_, Professional Edition** inclut des transformations d’obfuscation et des fonctionnalités de protection améliorées.
Elles incluent notamment les suivantes :

* *Protection de la propriété intellectuelle*
  * Options de renommage supplémentaires, notamment la méthode Overload Induction™ améliorée et la sélection d’identificateur aléatoire.
  * Outils de décodage des traces de pile obfusquées.
  * Accès aux transformations d’obfuscation de niveau entreprise, notamment les [transformations visant à mettre en échec la décompilation de code automatisée][control-flow].
  * La possibilité de [masquer des chaînes sensibles][string-encryption], ce qui rend impossible une recherche simple du code décompilé.
  * La possibilité d’[incorporer discrètement des chaînes de propriété et la distribution dans vos assemblys][watermarking] (filigranage de logiciels), ce qui vous permet de déterminer la source de fuites logicielles non autorisées.
  * La possibilité de [regrouper plusieurs assemblys en un seul][linking], ce qui complique encore davantage la tâche des personnes malveillantes souhaitant déterminer les rôles des éléments de code puisque plus rien n’est séparé.
  * La possibilité de [supprimer automatiquement le code non utilisé de votre application][pruning], ce qui réduit la quantité de code sensible fourni.
* *Protection de l’intégrité des applications*
  * [Comportements de défense des applications][check-actions] supplémentaires.
  * La possibilité d’injecter du code anti-violation et anti-débogage dans des assemblys `.dll`.
  * La possibilité de fournir un délai d’avertissement avant l’échéance de fin de vie d’une application.
  * La possibilité de notifier le code d’application dans le délai d’avertissement de fin de vie ou après la date limite.
  * Chiffrement des données de télémétrie.
* *Surveillance d’applications*
  * La possibilité de collecter des informations et de les enregistrer lors d’indisponibilités temporaires du réseau.
  * La possibilité de collecter des informations d’identification personnelle.
  * Utilisation illimitée du [suivi des fonctionnalités][features].
  * La possibilité d’effectuer le suivi des exceptions interceptées et levées par votre code, en plus des exceptions non gérées.
  * La possibilité d’effectuer le suivi des exceptions dans les assemblys `.dll`.
  * Chiffrement des données de télémétrie.

Dotfuscator Professional est l’[obfuscateur .NET][net-obfuscator] standard. Il est approprié pour les développeurs d’entreprise nécessitant un support technique, une maintenance et des mises à jour de produits continus.
De plus, Dotfuscator Professional offre une intégration à Visual Studio plus étroite et est concédé sous licence pour une utilisation commerciale.

Pour plus d’informations sur les fonctionnalités de protection des applications avancées de Dotfuscator Professional, visitez la [page de vue d’ensemble de Dotfuscator][product-about] de PreEmptive Solutions et [comparez-le à Community Edition][product-compare].
[Des versions d’évaluation entièrement prises en charge sont disponibles sur demande sur le site preemptive.com][eval].

## Voir aussi
<a id="see-also" class="xliff"></a>

[Cette rubrique dans le guide d’utilisation complet de Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]: https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]: https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]: https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]: https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]: https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Check%20Actions.html
[features]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Feature_Usage_Tracking_and_the_Feature_Attribute.html

[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[eval]: https://www.preemptive.com/eval-request

[product-about]: https://www.preemptive.com/products/dotfuscator/overview
[product-compare]: https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
