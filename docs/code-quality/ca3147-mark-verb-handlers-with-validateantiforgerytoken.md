---
title: 'CA3147 : Marquer les gestionnaires de verbe avec ValidateAntiForgeryToken'
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: da15a441a10f3ad3f3f84ee0cc76eeed8e4127e4
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42623810"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147 : Marquer les gestionnaires de verbe avec ValidateAntiForgeryToken

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode d’action de contrôleur ASP.NET MVC n’est pas marquée avec [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118)), ou un attribut spécifiant le verbe HTTP, tel que [HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993(v%3dvs.118)) ou [ AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29).

## <a name="rule-description"></a>Description de la règle

Lorsque vous concevez un contrôleur ASP.NET MVC, tenez compte des attaques par falsification de requête intersites. Une attaque de falsification de requête intersites peut envoyer des requêtes malveillantes à partir d’un utilisateur authentifié à votre contrôleur ASP.NET MVC. Pour plus d’informations, consultez [prévention de XSRF/CSRF dans ASP.NET MVC et web pages](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Cette règle vérifie ce contrôleur ASP.NET MVC méthodes d’action soit :

- Avoir la [ValidateAntiforgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108%28v%3dvs.118%29) et spécifier les verbes HTTP autorisés, ne pas y compris HTTP GET.

- Spécifiez la commande HTTP GET comme un verbe autorisé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Pour les actions de contrôleur d’ASP.NET MVC qui gèrent les demandes HTTP GET et n’ont des effets secondaires potentiellement dangereux, ajouter un [HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993%28v%3dvs.118%29) à la méthode.

   Si vous avez un ASP.NET MVC action du contrôleur qui gère HTTP GET demande et a des effets secondaires potentiellement dangereuses telles que la modification des données sensibles, votre application est vulnérable aux attaques par falsification de requête intersites.  Vous aurez besoin de reconcevoir votre application afin que seules les requêtes HTTP POST, PUT ou DELETE effectuer des opérations sensibles.

- Pour les actions de contrôleur d’ASP.NET MVC qui gèrent HTTP POST, PUT ou ajouter des requêtes DELETE, [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118)) et attributs spécifiant les verbes HTTP autorisés ([AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29) [HttpPostAttribute](/previous-versions/aspnet/web-frameworks/ee264023%28v%3dvs.118%29), [HttpPutAttribute](/previous-versions/aspnet/web-frameworks/ee470909%28v%3dvs.118%29), ou [HttpDeleteAttribute](/previous-versions/aspnet/web-frameworks/ee470917%28v%3dvs.118%29)). En outre, vous devez appeler le [HtmlHelper.AntiForgeryToken()](/previous-versions/aspnet/web-frameworks/dd504812%28v%3dvs.118%29) méthode votre vue MVC ou la page web de Razor. Pour obtenir un exemple, consultez [examen des méthodes de modification et de modifier la vue](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si :

- L’action du contrôleur ASP.NET MVC n’a aucun effets nuisibles.

- L’application valide le jeton anti-contrefaçon d’une manière différente.

## <a name="validateantiforgerytoken-attribute-example"></a>Exemple d’attribut ValidateAntiForgeryToken

### <a name="violation"></a>Violation

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>Solution

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>Exemple d’attribut HttpGet

### <a name="violation"></a>Violation

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>Solution

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
