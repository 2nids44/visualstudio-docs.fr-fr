---
title: "Project, élément (modèles Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f2995f6486ebb8d3e305c70c03fb543fab04b67a
ms.lasthandoff: 02/22/2017

---
# <a name="project-element-visual-studio-templates"></a>Project, élément (modèles Visual Studio)
Spécifie les fichiers ou répertoires à ajouter au projet.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`File`|Attribut requis.<br /><br /> Spécifie le nom du fichier projet dans le fichier .zip du modèle.|  
|`ReplaceParameters`|Attribut facultatif.<br /><br /> Valeur booléenne qui spécifie si le fichier de projet contient des valeurs de paramètre doivent être remplacées lorsqu’un projet est créé à partir du modèle. La valeur par défaut est `false`.|  
|`TargetFileName`|Attribut facultatif.<br /><br /> Spécifie le nom du fichier projet lorsqu’un projet est créé à partir du modèle.|  
|`IgnoreProjectParameter`|Attribut facultatif.<br /><br /> Spécifie si le projet doit être ajouté à la solution actuelle. Si la valeur de paramètre personnalisé, « $*myCustomParameter*$» existe dans le fichier de remplacement de paramètre, le projet est créé, mais pas ajouté en tant que partie de la solution actuellement ouverte.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Dossier](../extensibility/folder-element-visual-studio-project-templates.md)|Élément facultatif.<br /><br /> Spécifie un dossier à ajouter au projet.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Élément facultatif.<br /><br /> Spécifie un fichier à ajouter à un projet.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Élément requis.|  
  
## <a name="remarks"></a>Notes  
 `Project` est un élément enfant facultatif de `TemplateContent`.  
  
 Le `Project` élément est utilisée pour spécifier si un projet et par conséquent, est uniquement valide dans les modèles de projet.  
  
 `Project`les éléments peuvent avoir [dossier](../extensibility/folder-element-visual-studio-project-templates.md) éléments enfants ou [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) éléments enfants, mais pas un mélange des deux `Folder` et `ProjectItem` les éléments enfants.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]renomme automatiquement le nom du fichier projet basé sur le nom entré par l’utilisateur dans le **nouveau projet** boîte de dialogue. Utilisez le `TargetFileName` si vous souhaitez fournir un autre nom de fichier pour les fichiers de projet créés avec le modèle d’attribut.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant affiche les métadonnées d’un modèle de projet pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] application.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de projet et modèles d’élément](../ide/creating-project-and-item-templates.md)   
 [ProjectItem, élément (modèles de projet Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder, élément (modèles de projet Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)