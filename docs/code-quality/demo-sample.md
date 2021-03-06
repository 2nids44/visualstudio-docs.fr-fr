---
title: Exemple de projet C++ pour l’analyse du code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: aafbaaf682852adaea8f20a1373ea1ae4b025fad
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704861"
---
# <a name="sample-c-project-for-code-analysis"></a>Exemple de projet C++ pour l’analyse du code

Procédures suivantes vous indiquent comment créer l’exemple pour [procédure pas à pas : code C/C++ analyser pour les erreurs](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Les procédures de créent :

- Une solution Visual Studio nommée CppDemo.

- Un projet de bibliothèque statique nommé CodeDefects.

- Un projet de bibliothèque statique nommé Annotations.

Les procédures fournissent également le code pour l’en-tête et *.cpp* fichiers pour les bibliothèques statiques.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Créer la solution CppDemo et le projet CodeDefects

1. Cliquez sur le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **nouveau projet**.

2. Dans le **types de projet** liste d’arborescence, si Visual C++ n’est pas votre langue par défaut dans Visual Studio, développez **autres langages**.

3. Développez **Visual C++**, puis cliquez sur **général**.

4. Dans **modèles**, cliquez sur **projet vide**.

5. Dans le **nom** zone de texte, tapez **CodeDefects**.

6. Sélectionnez le **créer le répertoire pour la solution** case à cocher.

7. Dans le **nom de la Solution** zone de texte, tapez **CppDemo**.

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurer le projet CodeDefects comme bibliothèque statique

1. Dans l’Explorateur de solutions, cliquez sur **CodeDefects** puis cliquez sur **propriétés**.

2. Développez **propriétés de Configuration** puis cliquez sur **général**.

3. Dans le **général** , sélectionnez le texte dans la colonne à côté **Extension cible**, puis tapez **.lib**.

4. Dans **projet par défaut est**, cliquez sur la colonne en regard **Configuration Type**, puis cliquez sur **bibliothèque statique (.lib)**.

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Ajouter le fichier d’en-tête et source pour le projet CodeDefects

1. Dans l’Explorateur de solutions, développez **CodeDefects**, avec le bouton droit **fichiers d’en-tête**, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**.

2. Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **Code**, puis cliquez sur **fichier d’en-tête (.h)**.

3. Dans le **nom** , tapez **Bug.h** puis cliquez sur **ajouter**.

4. Copiez le code suivant et collez-le dans le *Bug.h* fichier dans l’éditeur Visual Studio.

    ```cpp
    #include <windows.h>

    //
    //These 3 functions are consumed by the sample
    //  but are not defined. This project cannot be linked!
    //

    bool CheckDomain( LPCSTR );
    HRESULT ReadUserAccount();

    //
    //These constants define the common sizes of the
    //  user account information throughout the program
    //

    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

5. Dans l’Explorateur de solutions, cliquez sur **fichiers sources**, pointez sur **nouveau**, puis cliquez sur **un nouvel élément**.

6. Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **fichier C++ (.cpp)**

7. Dans le **nom** , tapez **Bug.cpp** puis cliquez sur **ajouter**.

8. Copiez le code suivant et collez-le dans le *Bug.cpp* fichier dans l’éditeur Visual Studio.

    ```cpp
    #include <stdlib.h>
    #include "Bug.h"

    // the user account
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";
    int len = 0;

    bool ProcessDomain()
    {
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount() )
        {

            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )
            {
                if ( g_userAccount[len] == '\\' )
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete [] domain;
                return false;
            }
            else
            {
                domain[len]='\0';
            }
            // Process domain string
            bool result = CheckDomain( domain );

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i+j;
    }
    ```

9. Cliquez sur le **fichier** menu, puis sur **Enregistrer tout**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Ajouter le projet Annotations et le configurer comme bibliothèque statique

1. Dans l’Explorateur de solutions, cliquez sur **CppDemo**, pointez sur **ajouter**, puis cliquez sur **nouveau projet**.

2. Dans le **ajouter un nouveau projet** boîte de dialogue, développez Visual C++, cliquez sur **général**, puis cliquez sur **projet vide**.

3. Dans le **nom** zone de texte, tapez **Annotations**, puis cliquez sur **ajouter**.

4. Dans l’Explorateur de solutions, cliquez sur **Annotations** puis cliquez sur **propriétés**.

5. Développez **propriétés de Configuration** puis cliquez sur **général**.

6. Dans le **général** , sélectionnez le texte dans la colonne à côté **Extension cible**, puis tapez **.lib**.

7. Dans **projet par défaut est**, cliquez sur la colonne en regard **Configuration Type**, puis cliquez sur **bibliothèque statique (.lib)**.

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Ajoutez le fichier d’en-tête et le fichier source au projet Annotations

1. Dans l’Explorateur de solutions, développez **Annotations**, avec le bouton droit **fichiers d’en-tête**, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**.

2. Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **fichier d’en-tête (.h)**.

3. Dans le **nom** , tapez **annotations.h** puis cliquez sur **ajouter**.

4. Copiez le code suivant et collez-le dans le *annotations.h* fichier dans l’éditeur Visual Studio.

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();

    ```

5. Dans l’Explorateur de solutions, cliquez sur **fichiers sources**, pointez sur **nouveau**, puis cliquez sur **un nouvel élément**.

6. Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **Code** puis cliquez sur **fichier C++ (.cpp)**

7. Dans le **nom** , tapez **annotations.cpp** puis cliquez sur **ajouter**.

8. Copiez le code suivant et collez-le dans le *annotations.cpp* fichier dans l’éditeur Visual Studio.

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>
    #include <windows.h>
    #include <stdlib.h>
    #include "annotations.h"

    LinkedList* AddTail( LinkedList *node, int value )
    {
        LinkedList *newNode = NULL;

        // finds the last node
        while ( node->next != NULL )
        {
            node = node->next;
        }

        // appends the new node
        newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }

    ```

9. Cliquez sur le **fichier** menu, puis sur **Enregistrer tout**.
