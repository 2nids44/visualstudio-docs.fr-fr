---
title: "Erreur&#160;: L&#39;ex&#233;cution de Transact-SQL s&#39;est termin&#233;e sans d&#233;bogage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_sql_executed_but_not_debugged"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "SQL"
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Erreur&#160;: L&#39;ex&#233;cution de Transact-SQL s&#39;est termin&#233;e sans d&#233;bogage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette erreur se produit lorsque vous essayez de déboguer une procédure Transact\-SQL ou SQLCLR et que le débogueur ne reçoit pas de messages de débogage de SQL Server.  
  
 Cela peut être dû à des problèmes liés au réseau ou à SQL Server, mais plus probablement à un problème d'autorisation.  
  
 Deux comptes sont concernés :  
  
-   Le compte d'application est le compte utilisateur qu'utilise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour s'exécuter.  
  
-   Le compte de connexion est l'identité utilisée pour établir la connexion à SQL Server.  Il ne s'agit pas nécessairement du compte sous lequel Visual Studio est exécuté si la connexion utilise l'authentification SQL.  
  
 Le débogage SQL requiert que le compte d'application corresponde au compte de connexion ou soit administrateur système.  
  
 Si vous utilisez un nom d'utilisateur SQL comme sa, le compte d'application doit être configuré sur le SQL Server comme un administrateur système.  Par défaut, les administrateurs de l'ordinateur sur lequel SQL Server est exécuté sont des administrateurs système SQL Server.  
  
 Pour corriger cette erreur, vous pouvez avoir besoin de :  
  
-   Vérifier vos paramètres d'autorisation.  Pour plus d'informations, consultez [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/fr-fr/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Vérifier que le débogage SQL est correctement configuré.  
  
-   Consulter votre administrateur réseau ou de base de données.  
  
## Voir aussi  
 [Setting Up SQL Debugging](http://msdn.microsoft.com/fr-fr/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/fr-fr/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)   
 [Débogage distant](../debugger/remote-debugging.md)