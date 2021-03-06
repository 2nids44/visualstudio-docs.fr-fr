---
title: 'Comment : signer des fichiers avec SignTool.exe (ClickOnce) d’installation | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b66d9440ebcf62c59049b45769a2244fc773480e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081499"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Comment : connexion fichiers d’installation avec SignTool.exe (ClickOnce)
Vous pouvez utiliser *SignTool.exe* pour signer un programme d’installation (*setup.exe*). Ce processus aide à garantir que les fichiers falsifiés ne sont pas installés sur les ordinateurs des utilisateurs finaux.  
  
 Par défaut, ClickOnce dispose de manifestes signés, ainsi que d'un programme d'installation signé. Toutefois, si vous souhaitez modifier ultérieurement les paramètres du programme d'installation, vous devrez également signer le programme d'installation. Si vous modifiez les paramètres après avoir signé le programme d'installation, la signature sera endommagée.  
  
 La procédure suivante génère des manifestes non signés ainsi qu'un programme d'installation non signé. La signature ClickOnce est ensuite activée dans Visual Studio pour générer des manifestes signés. Le programme d'installation n'est pas signé pour que les clients puissent signer l'exécutable avec leurs propres certificats.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Pour générer un programme d'installation non signé et le signer ultérieurement  
  
1.  Sur l'ordinateur de développement, installez le certificat avec lequel vous souhaitez signer les manifestes.  
  
2.  Sélectionnez le projet dans **l’Explorateur de solutions**.  
  
3.  Sur le **projet** menu, cliquez sur *nom_projet* **propriétés**.  
  
4.  Dans le **signature** page, désactivez **signer les manifestes ClickOnce**.  
  
5.  Dans le **publier** , cliquez sur **conditions préalables**.  
  
6.  Vérifiez que toutes les conditions préalables sont sélectionnées, puis cliquez sur **OK**.  
  
7.  Dans le **publier** page, vérifiez les paramètres de publication, puis sur **publier maintenant**.  
  
     La solution publie le manifeste d’application non signé, le manifeste de déploiement non signé, les fichiers spécifiques à la version et le programme d’installation non signé à l’emplacement du dossier de publication.  
  
8.  Dans le **publier** , cliquez sur **conditions préalables**.  
  
9. Dans le **prérequis** boîte de dialogue, décochez **créer un programme d’installation pour installer les composants prérequis**.  
  
10. Dans le **publier** page, vérifiez les paramètres de publication, puis sur **publier maintenant**.  
  
     La solution publie le manifeste d’application signé, le manifeste de déploiement signé et les fichiers spécifiques à la version à l’emplacement du dossier de publication. Le programme d'installation non signé n'est pas remplacé par le processus de publication.  
  
11. Sur le site du client, ouvrez une invite de commandes.  
  
12. Accédez au répertoire qui contient le *.exe* fichier.  
  
13. Signe le *.exe* fichier avec la commande suivante :  
  
    ```cmd  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Par exemple, pour signer le programme d'installation, utilisez l'une des commandes suivantes :  
  
    ```cmd  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : signer à nouveau les manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
