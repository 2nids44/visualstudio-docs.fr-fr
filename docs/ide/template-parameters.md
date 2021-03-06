---
title: Paramètres de modèle de projet et d’élément Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4c76eaf68f63b4f3b8a5713d0b206b395ee7c9f1
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178632"
---
# <a name="template-parameters"></a>Paramètres de modèle

Vous pouvez remplacer des valeurs dans votre modèle quand ce dernier est instancié. Pour configurer cette fonctionnalité, utilisez des *paramètres de modèle*. Les paramètres de modèle peuvent être utilisés pour remplacer des valeurs, comme les noms de classes et les espaces de noms, dans le modèle. L’Assistant Modèle, qui s’exécute en arrière-plan quand un utilisateur ajoute un nouvel élément ou un nouveau projet, remplace ces paramètres.

## <a name="declaring-and-enabling-template-parameters"></a>Déclaration et activation des paramètres de modèle

Les paramètres de modèle sont déclarés au format $*paramètre*$. Exemple :

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="to-enable-parameter-substitution-in-templates"></a>Pour activer la substitution des paramètres dans les modèles

1. Dans le fichier *.vstemplate* du modèle, localisez l’élément `ProjectItem` qui correspond à l’élément pour lequel vous souhaitez activer le remplacement des paramètres.

1. Affectez à l'attribut `ReplaceParameters` de l'élément `ProjectItem` la valeur `true`.

1. Dans le fichier de code de l’élément de projet, ajoutez les paramètres quand cela est approprié. Par exemple, le paramètre suivant spécifie que le nom du projet sécurisé est utilisé pour désigner l’espace de noms dans un fichier :

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Paramètres de modèle réservés

Le tableau suivant liste les paramètres de modèle réservés qui peuvent être utilisés par n’importe quel modèle.

|Paramètre|Description|
|---------------|-----------------|
|clrversion|Version actuelle du Common Language Runtime (CLR).|
|guid[1-10]|GUID utilisé pour remplacer le GUID du projet dans un fichier projet. Vous pouvez spécifier jusqu’à 10 GUID uniques (par exemple, `guid1`).|
|itemname|Nom fourni par l’utilisateur dans la boîte de dialogue **Ajouter un nouvel élément**.|
|machinename|Nom de l’ordinateur actuel (par exemple, Ordi01).|
|projectname|Nom fourni par l’utilisateur dans la boîte de dialogue **Nouveau projet**.|
|registeredorganization|Valeur de clé de Registre provenant de HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|rootnamespace|Espace de noms racine du projet actuel. Ce paramètre s’applique uniquement aux modèles d’élément.|
|safeitemname|Nom fourni par l’utilisateur dans la boîte de dialogue **Ajouter un nouvel élément**, dont tous les caractères et espaces potentiellement dangereux ont été supprimés.|
|safeprojectname|Nom fourni par l’utilisateur dans la boîte de dialogue **Nouveau projet**, dont tous les caractères et espaces potentiellement dangereux ont été supprimés.|
|heure|Date et heure actuelles au format JJ/MM/AAAA 00:00:00.|
|SpecificSolutionName|Nom du fichier solution. Quand l’option "créer le répertoire de la solution" est cochée, `SpecificSolutionName` porte le nom de la solution. Quand l’option "créer le répertoire de solution" n’est pas cochée, `SpecificSolutionName` est vide.|
|userdomain|Domaine de l’utilisateur actuel.|
|Nom d’utilisateur|Nom de l’utilisateur actuel.|
|webnamespace|Nom du site web actuel. Ce paramètre est utilisé dans le modèle de formulaire web pour garantir des noms de classes uniques. Si le site web se trouve dans le répertoire racine du serveur web, ce paramètre de modèle correspond à ce répertoire racine.|
|année|Année actuelle au format AAAA.|

> [!NOTE]
> Les paramètres de modèle respectent la casse.

## <a name="custom-template-parameters"></a>Paramètres de modèle personnalisés

Vous pouvez spécifier vos propres paramètres et valeurs de modèle, en plus des paramètres de modèle réservés par défaut utilisés lors du remplacement de paramètres. Pour plus d’informations, consultez [CustomParameters, élément (modèles Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Exemple : utilisation du nom du projet comme nom de fichier

Vous pouvez spécifier des noms de fichiers de variables pour les éléments de projet à l’aide d’un paramètre dans l’attribut `TargetFileName`.

L’exemple suivant spécifie que le nom d’un fichier exécutable utilise le nom du projet, spécifié par `$projectname$`.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Exemple : utilisation du nom du projet sécurisé comme nom de l’espace de noms

Pour utiliser le nom du projet sécurisé pour l’espace de noms dans un fichier de classe C#, utilisez la syntaxe suivante :

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

Dans le fichier *.vstemplate* du modèle de projet, ajoutez l’attribut `ReplaceParameters="true"` quand vous référencez le fichier :

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Voir aussi

- [Personnaliser les modèles](../ide/customizing-project-and-item-templates.md)
- [Guide pratique pour créer des modèles de projet](../ide/how-to-create-project-templates.md)
- [Informations de référence sur les schémas de modèles](../extensibility/visual-studio-template-schema-reference.md)
