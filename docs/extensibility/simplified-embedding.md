---
title: Simplifié incorporation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 01b06a0a63059c39035d15221feb201d3674d4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142930"
---
# <a name="simplified-embedding"></a>Simplifié incorporation
Incorporation simplifiée est activée dans un éditeur lorsque son objet de vue de document est apparenté à (autrement dit, un enfant de) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface est implémentée pour gérer ses commandes de fenêtre. Éditeurs incorporation simplifiés ne peut héberger des contrôles actifs. Les objets utilisés pour créer un éditeur avec incorporation simplifié sont affichés dans l’illustration suivante.  
  
 ![Graphique de l’éditeur d’incorporation simplifié](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Éditeur d’incorporation simplifié  
  
> [!NOTE]
>  Des objets dans cette illustration, uniquement le `CYourEditorFactory` objet est requis pour créer un éditeur de fichier standard. Si vous créez un éditeur personnalisé, vous ne devez pas implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, car votre éditeur possède probablement son propre mécanisme privé de persistance. Pour les éditeurs non-custom, toutefois, vous devez le faire.  
  
 Toutes les interfaces implémentées pour créer un éditeur avec incorporation simplifié sont contenus dans le `CYourEditorDocument` objet. Toutefois, pour prendre en charge plusieurs vues de données de document, diviser les interfaces sur des objets distincts de données et la vue comme indiqué dans le tableau suivant.  
  
|Interface|Emplacement de l’interface|Utilisez|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Vue|Fournit la connexion à la fenêtre parente.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Vue|Gère les commandes.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Vue|Permet la mise à jour de la barre d’état.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Vue|Permet de **boîte à outils** éléments.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Données|Envoie des notifications lorsque le fichier change.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Données|Active la fonctionnalité Enregistrer en tant que pour un type de fichier.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Données|Active la persistance pour le document.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Données|Permet la suppression des événements de changement de fichier, telles que le rechargement de déclenchement.|