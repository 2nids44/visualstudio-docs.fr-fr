---
title: Développement piloté par les tests avec l’Explorateur de tests dans Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c2988bb821a91ec1bc5f37955bef8a61897f2c4d
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382088"
---
# <a name="quickstart-test-driven-development-with-test-explorer"></a>Démarrage rapide : développement piloté par les tests avec l’Explorateur de tests

Nous vous recommandons de créer des tests unitaires pour que votre code continue à s'exécuter correctement dans de nombreuses étapes incrémentielles de développement. Vous pouvez utiliser plusieurs Infrastructures pour écrire des tests unitaires, y compris ceux développés par des tiers. Il existe des frameworks de tests qui sont spécialisés dans les tests avec certains langages ou certaines plateformes. L'explorateur de tests fournit une interface unique pour les tests unitaires dans l'une de ces infrastructures. Les adaptateurs sont disponibles pour les infrastructures les plus couramment utilisées, et vous pouvez écrire vos propres adaptateurs pour d'autres frameworks.

 L'Explorateur de tests remplace les fenêtres de test unitaire trouvées dans les éditions antérieures de Visual Studio. Ses avantages incluent :

-   Exécution du .NET, de code non managé, de code de base de données et d'autres sortes de tests à l'aide d'une interface unique.

-   Utilisation du framework de tests unitaires de votre choix, par exemple NUnit ou MSTest.

-   Consultez dans une seule fenêtre toutes les informations dont vous avez besoin.

## <a name="use-test-explorer"></a>Utiliser l’Explorateur de tests
 ![Explorateur de tests unitaires indiquant le bouton Exécuter tout](../test/media/unittestexplorer-beta-.png)

### <a name="to-run-unit-tests-by-using-test-explorer"></a>Pour exécuter des tests unitaires à l’aide de l’Explorateur de tests

1.  Créez des tests unitaires qui utilisent les frameworks de test de votre choix.

     Par exemple, pour créer un test qui utilise le framework MSTest :

    1.  Créez un projet de test.

         Dans la boîte de dialogue **Nouveau projet**, développez **Visual Basic** > **Visual C#** ou **Visual C++**, puis choisissez **Test**.

         Sélectionnez **Projet de test unitaire**.

    2.  Écrivez chaque test unitaire sous forme de méthode. Ajoutez devant chaque méthode de test l'attribut `[TestMethod]` .

2.  Si les tests individuels n’ont aucune dépendance qui les empêche d’être exécutés dans n’importe quel ordre, activez l’exécution parallèle des tests avec le bouton bascule ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) dans la barre d’outils. Cela peut réduire sensiblement le temps nécessaire pour exécuter tous les tests.

3.  Dans la barre de menus, sélectionnez **Test** > **Exécuter les tests unitaires** > **Tous les tests**.

     La solution se génère et les tests s'exécutent.

     L'Explorateur de tests ouvre et affiche un résumé des résultats.

 **Pour afficher une liste complète des tests :** Choisissez **Afficher tout** dans une catégorie.

 **Pour afficher les détails d'un résultat de test :** Sélectionnez le test dans l'Explorateur de tests pour afficher des détails tels que les messages d'exception dans le volet d'informations.

 **Pour accéder au code d'un test :** Double-cliquez sur le test dans l'Explorateur de tests ou choisissez **Ouvrir un test** dans le menu contextuel.

 **Pour déboguer un test :** Ouvrez le menu contextuel d'un ou de plusieurs tests, puis choisissez **Déboguer les tests sélectionnés**.

> [!IMPORTANT]
> Les résultats affichés concernent la série la plus récente. La barre de résultats colorée montre uniquement les résultats des tests qui ont été exécutés. Par exemple, si vous exécutez plusieurs tests et que certains d'entre eux échouent puis que vous n'exécutez que les tests réussis, la barre de résultats affiche tout en vert.


> [!NOTE]
> Si aucun test n'apparaît, vérifiez que vous avez installé un adaptateur pour connecter l'Explorateur de tests à l'infrastructure de test que vous utilisez. Pour plus d’informations, consultez [Installer des frameworks de tests unitaires de tiers](install-third-party-unit-test-frameworks.md).


##  <a name="walkthrough-using-unit-tests-to-develop-a-method"></a>Procédure pas à pas : Utilisation de tests unitaires pour développer une méthode
 Cette procédure pas-à-pas montre comment développer une méthode testée en C# à l'aide de l'infrastructure des tests unitaires Microsoft. Vous pouvez facilement l'adapter à d'autres langages et utiliser d'autres infrastructures de tests comme NUnit. Pour plus d’informations, consultez [Installer des frameworks de tests unitaires de tiers](install-third-party-unit-test-frameworks.md).

### <a name="create-the-test-and-method"></a>Créer le test et la méthode

1.  Créez un projet de bibliothèque de classes Visual C#. Ce projet contiendra le code que nous voulons fournir. Dans cet exemple, cela est nommé `MyMath`.

2.  Créez un projet de test.

    -   Dans la boîte de dialogue **Nouveau projet**, choisissez **Visual C#** > **Test**, puis **Projet de test unitaire**.

         ![Nouveaux codes et projets de test](../test/media/unittestexplorerwalk1.png)

3.  Écrivez une méthode de test de base. Vérifiez le résultat obtenu pour une entrée spécifique :

    ```csharp

    [TestMethod]
    public void BasicRooterTest()
    {
      // Create an instance to test:
      Rooter rooter = new Rooter();
      // Define a test input and output value:
      double expectedResult = 2.0;
      double input = expectedResult * expectedResult;
      // Run the method under test:
      double actualResult = rooter.SquareRoot(input);
      // Verify the result:
      Assert.AreEqual(expectedResult, actualResult,
          delta: expectedResult / 100);
    }
    ```

4.  Générez la méthode à partir du test.

    1.  Placez le curseur sur `Rooter`, puis dans le menu contextuel, choisissez **Générer** > **Nouveau type**.

    2.  Dans la boîte de dialogue **Générer un nouveau type** , définissez **Projet** sur le projet de bibliothèque de classes. Dans cet exemple, il s’agit de `MyMath`.

    3.  Placez le curseur sur `SquareRoot`, puis dans le menu contextuel, choisissez **Générer** > **Stub de méthode**.

5.  Exécutez le test unitaire.

    1.  Dans le menu **Test**, choisissez **Exécuter les tests unitaires** > **Tous les tests**.

         La solution se génère et s'exécute.

         L'Explorateur de tests ouvre et affiche les résultats.

         Le test s'affiche sous **Échec de tests**.

6.  Sélectionnez le nom du test.

     Les détails du test s'affichent dans la partie inférieure de l'Explorateur de tests.

7.  Sélectionnez les éléments sous **Trace de la pile** pour voir où le test a échoué.

 ![Explorateur de tests unitaires indiquant un échec de test.](../test/media/unittestexplorerwalkthrough2.png)

 À ce stade, vous avez créé un test et un stub que vous avez modifié afin que le test réussisse.

#### <a name="after-every-change-make-all-the-tests-pass"></a>Après chaque modification, faites en sorte que tous les tests réussissent

1.  Dans *MyMath\Rooter.cs*, améliorez le code de `SquareRoot` :

    ```csharp
    public double SquareRoot(double input)
     {
       return input / 2;
     }
    ```

2.  Dans l'Explorateur de tests, choisissez **Exécuter tout**.

     Le code se génère et le test s'exécute.

     Le test est réussi.

     ![Explorateur de tests unitaires indiquant un test réussi.](../test/media/unittestexplorerwalkthrough3.png)

#### <a name="add-tests-to-extend-the-range-of-inputs"></a>Ajouter des tests pour étendre la plage d'entrées

1.  Pour renforcer votre confiance dans le fonctionnement de votre code dans tous les cas, ajoutez des tests qui essaient un plus grand nombre de valeurs d'entrée.

    > [!TIP]
    > Évitez de modifier les tests existants qui réussissent. Au lieu de cela, ajoutez de nouveaux tests. Modifiez les tests existants uniquement lorsque les besoins des utilisateurs changent. Cette stratégie permet de garantir que vous ne perdez pas de fonctionnalités existantes quand vous travaillez pour étendre le code.

     Dans votre classe de test, ajoutez le test suivant, qui essaie une plage de valeurs d'entrée :

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
      // Create an instance to test:
      Rooter rooter = new Rooter();
      // Try a range of values:
      for (double expectedResult = 1e-8;
          expectedResult < 1e+8;
          expectedResult = expectedResult * 3.2)
      {
        RooterOneValue(rooter, expectedResult);
      }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
      double input = expectedResult * expectedResult;
      double actualResult = rooter.SquareRoot(input);
      Assert.AreEqual(expectedResult, actualResult,
          delta: expectedResult / 1000);
    }
    ```

2.  Dans l'Explorateur de tests, choisissez **Exécuter tout**.

     Le nouveau test échoue bien que le premier test réussisse toujours.

     Pour rechercher le point de défaillance, sélectionnez le test qui a échoué, puis dans la partie inférieure de l'Explorateur de tests, sélectionnez l'élément supérieur de la **Trace de la pile**.

3.  Examinez la méthode de test pour voir ce qui peut être erroné. Dans la classe `MyMath.Rooter` , réécrivez le code :

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4.  Dans l'Explorateur de tests, choisissez **Exécuter tout**.

     Les deux tests ont réussi maintenant.

#### <a name="add-tests-for-exceptional-cases"></a>Ajouter des tests pour des cas exceptionnels

1.  Ajouter un test pour les entrées négatives :

    ```csharp
    [TestMethod]
     public void RooterTestNegativeInputx()
     {
         Rooter rooter = new Rooter();
         try
         {
             rooter.SquareRoot(-10);
         }
         catch (ArgumentOutOfRangeException e)
         {
             return;
         }
         Assert.Fail();
     }
    ```

2.  Dans l'Explorateur de tests, choisissez **Exécuter tout**.

     La méthode testée s'exécute en boucle et doit être annulée manuellement.

3.  Sélectionnez **Annuler**.

     Le test s'arrête au bout de 10 secondes.

4.  Corrigez le code de la méthode :

    ```csharp

    public double SquareRoot(double input)
    {
      if (input <= 0.0)
      {
        throw new ArgumentOutOfRangeException();
      }
    ...
    ```

5.  Dans l'Explorateur de tests, choisissez **Exécuter tout**.

     Tous les tests réussissent.

#### <a name="refactor-without-changing-tests"></a>Refactoriser sans modifier les tests

1.  Simplifiez le code, mais ne modifiez pas les tests.

    > [!TIP]
    > La *refactorisation* est une modification destinée à améliorer les performances du code ou à en simplifier la compréhension. Elle n'est pas destinée à modifier le comportement du code. Les tests ne sont donc pas modifiés.
    >
    > Nous vous recommandons de séparer les étapes de refactorisation des étapes qui étendent les fonctionnalités. En ne modifiant pas les tests, vous pouvez être sûr que vous n'avez pas introduit par erreur des bogues lors de la refactorisation.

    ```csharp
    public class Rooter
    {
      public double SquareRoot(double input)
      {
        if (input <= 0.0)
        {
          throw new ArgumentOutOfRangeException();
        }
        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
          previousResult = result;
          result = (result + input / result) / 2;
          //was: result = result - (result * result - input) / (2*result);
        }
        return result;
      }
    }
    ```

2.  Choisissez **Exécuter tout**.

     Tous les tests réussissent encore.

     ![Explorateur de tests unitaires indiquant 3 tests réussis.](../test/media/unittestexplorerwalkthrough4.png)
