---
title: Programme d'amélioration de l'expérience utilisateur
description: Découvrez comment gérer les paramètres de confidentialité dans Visual Studio.
ms.date: 05/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba68d0d369d178606777944c9dc4dcd633a503f4
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280642"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Programme d’amélioration du produit Visual Studio

Le programme VSCEIP (Programme d’amélioration du produit Visual Studio) est conçu pour aider Microsoft à améliorer Visual Studio au fil du temps. Ce programme [collecte des informations sur les erreurs](../ide/diagnostic-data-collection.md), le matériel informatique et la façon dont les utilisateurs se servent de Visual Studio, sans les interrompre dans leurs tâches. Les informations collectées permettent à Microsoft d’identifier les fonctionnalités à améliorer. Ce document explique comment accepter ou refuser de participer au programme VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]

## <a name="opt-in-or-out"></a>Accepter ou refuser de participer

Le programme VSCEIP est activé par défaut. Vous pouvez le désactiver ou le réactiver en suivant les instructions ci-après :

1. Démarrez Visual Studio.

1. Dans le menu **Aide**, pointez sur **Envoyer des commentaires**, puis sélectionnez **Paramètres**.

   La boîte de dialogue **Programme d’amélioration de l’expérience utilisateur Visual Studio** s’ouvre.

1. Pour refuser de participer, sélectionnez **Non, je ne souhaite pas participer**, puis sélectionnez **OK**.
   Pour accepter de participer, sélectionnez **Oui, je souhaite participer**, puis sélectionnez **OK**.

   ![Boîte de dialogue Programme d’amélioration de l’expérience utilisateur Visual Studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Paramètres du Registre

Si vous installez [Visual Studio Build Tools](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), vous devez mettre à jour le Registre pour configurer le programme VSCEIP. Les clients en entreprise peuvent créer une stratégie de groupe pour accepter ou refuser le programme VSCEIP en définissant une stratégie basée sur le Registre.

La clé et les paramètres de Registre appropriés sont les suivants :

Sur un système d’exploitation 64 bits, la clé est **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM** Sur un système d’exploitation 32 bits, la clé est **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM** Quand la stratégie de groupe est activée, la clé est **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

Entry = **OptIn**

Valeur = (DWORD)
- **0** pour refuser de participer (permet de désactiver le programme VSCEIP)
- **1** pour accepter de participer (permet d’activer le programme VSCEIP)

> [!CAUTION]
> Une modification incorrecte du registre peut endommager sérieusement votre système. Avant de modifier le registre, vous devez sauvegarder toutes les données importantes sur l'ordinateur. Vous pouvez également utiliser l’option de démarrage **Dernière bonne configuration connue**, si vous rencontrez des problèmes après l’application des changements manuels.

Pour plus d’informations sur les informations collectées, traitées ou transmises par le programme VSCEIP, consultez la [Déclaration de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Voir aussi

* [Informations de diagnostic collectées par Visual Studio](diagnostic-data-collection.md)
* [Nous contacter](../ide/talk-to-us.md)
* [Comment signaler un problème avec Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)
* [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/)
* [Déclaration de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement)
