---
title: 'Comment : envoyer des messages électroniques par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3ee656a8a4965f01969bad19d66d0ea6215bcbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-send-e-mail"></a>Comment : envoyer des messages électroniques par programmation  
  Cet exemple envoie un message électronique à des contacts dont le nom de domaine **example.com** dans leurs adresses de messagerie.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Contacts dont le nom de domaine **example.com** dans leurs adresses de messagerie.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Ne supprimez pas le code de filtre qui recherche le nom de domaine **example.com**. Votre solution envoyer des messages électroniques à l’ensemble de vos contacts si vous supprimez le filtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des éléments de messagerie](../vsto/working-with-mail-items.md)   
 [Comment : créer par programme un élément de messagerie](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Comment : accéder par programmation à des Contacts Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Guide pratique pour exécuter des actions lors de la réception d’un message électronique par programmation](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  