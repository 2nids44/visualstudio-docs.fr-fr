---
title: "Guide pratique pour déverrouiller Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/20/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: c3521e1de25854db012cb91bbe09d9463ecb42c7
ms.openlocfilehash: db9fff46d52be80e53bd5c09fb8ab9d1f06d4f3c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/21/2017

---

# <a name="how-to-unlock-visual-studio"></a>Guide pratique pour déverrouiller Visual Studio
Vous pouvez évaluer Visual Studio gratuitement pendant 30 jours. La connexion à l’environnement de développement intégré étend la période d’évaluation à 90 jours. Pour continuer à utiliser Visual Studio, déverrouillez l'IDE en :  
  
1.  utilisant un abonnement en ligne ou  
1.  entrant une clé de produit.  
  
ed## Pour déverrouiller Visual Studio à l'aide d'un abonnement en ligne  
 Pour déverrouiller Visual Studio à l’aide d’un abonnement MSDN ou Visual Studio Team Services associé à un compte Microsoft ou à un compte professionnel ou scolaire :  
  
1.  Cliquez sur le bouton « Connexion » en haut à droite de l’IDE (ou sélectionnez Fichier > Paramètres de compte pour ouvrir la boîte de dialogue Paramètres de compte et cliquez sur le bouton « Connexion »).  
  
1.  Entrez les informations d'identification d'un compte Microsoft ou d'un compte professionnel ou scolaire. Visual Studio recherche un abonnement MSDN ou Visual Studio Team Services associé à votre compte.  
  
> [!IMPORTANT]
>  Visual Studio recherche automatiquement les abonnements en ligne associés quand vous vous connectez à un compte Visual Studio Team Services à partir de la fenêtre d’outils Team Explorer. Quand vous vous connectez à un compte Visual Studio Team Services, vous pouvez utiliser un compte Microsoft ou un compte professionnel ou scolaire. Si un abonnement en ligne existe pour ce compte d'utilisateur, Visual Studio déverrouille automatiquement l'IDE.  
  
## <a name="to-unlock-visual-studio-with-a-product-key"></a>Pour déverrouiller Visual Studio avec une clé de produit  
  
1.  Sélectionnez **Fichier > Paramètres de compte** pour ouvrir la boîte de dialogue Paramètres de compte, puis cliquez sur le lien « **Licence avec une clé de produit** ».  
1.  Entrez la clé de produit dans la zone fournie.  
  
> [!TIP]
>  Les versions préliminaires de Visual Studio n'ont pas de clés de produit. Vous devez vous connecter à l'IDE pour utiliser les versions préliminaires.  
  
## <a name="address-license-problem-states"></a>Corriger les problèmes d’état des licences  
  
### <a name="update-stale-licenses"></a>Mettre à jour des licences obsolètes  
 Vous avez peut-être vu le message suivant indiquant que votre licence est sur le point d’expirer dans Visual Studio « Votre licence est sur le point d'expirer et doit être mise à jour. »
  
 ![Message d’expiration de licence Visual Studio](~/ide/media/vs2017_stale-license.png)  
  
 Ce message indique que, même si votre abonnement est peut-être toujours valide, le jeton de licence que Visual Studio utilise pour maintenir votre abonnement à jour n’a pas été actualisé et est devenu obsolète en raison de l’une des raisons suivantes :  
  
1.  Vous n’avez pas utilisé Visual Studio ou n’avez établi aucune connexion Internet pendant une longue période.   
1.  Vous vous êtes déconnecté de Visual Studio.  
  
 Avant que le jeton de licence ne soit périmé, Visual Studio affiche un message d’avertissement vous invitant à entrer à nouveau vos informations d’identification.  
  
 Si vous n’entrez pas à nouveau vos informations d’identification, le jeton est sur le point d’expirer et la boîte de dialogue Paramètres du compte indique le nombre de jours restants avant que votre jeton n’expire entièrement. Une fois votre jeton arrivé à expiration, vous devez entrer à nouveau les informations d'identification de ce compte ou obtenir une licence avec une autre méthode mentionnée ci-dessus pour pouvoir continuer à utiliser Visual Studio.  
  
> [!Important]
>  Si vous utilisez Visual Studio pendant de longues périodes dans des environnements ayant un accès limité ou nul à Internet, vous devez utiliser une clé de produit pour déverrouiller Visual Studio afin d'éviter toute interruption.  
  
### <a name="update-expired-licenses"></a>Mettre à jour des licences ayant expiré  
 Si votre abonnement a expiré et vous n'avez plus accès à Visual Studio, vous devez :  
  
1.  Renouveler votre abonnement. Pour plus d’informations sur la licence que vous utilisez, accédez à **Fichier > Paramètres du compte** et examinez les informations de licence sur le côté droit de la boîte de dialogue.  
  
1.  Si vous avez un autre abonnement associé à un autre compte, ajoutez ce compte à la liste **Tous les comptes** à gauche de la boîte de dialogue **Fichier > Paramètres du compte** en sélectionnant le lien **Ajouter un compte...**.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion à Visual Studio](../ide/signing-in-to-visual-studio.md)
