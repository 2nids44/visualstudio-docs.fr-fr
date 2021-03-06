---
title: Application Lifecycle Management (ALM) avec les applications Unity | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: eca67ab58611d9a070114bebdd3594ec66580714
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232330"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Application Lifecycle Management (ALM) avec les applications Unity

Le développement d'applications pour des plateformes modernes implique de nombreuses activités qui vont bien au-delà de la simple écriture de code. Ces activités, appelées DevOps (développement + opérations), couvrent le cycle de vie complet de l’application et incluent la planification et le suivi du travail, la conception et l’implémentation du code, la gestion d’un dépôt de code source, l’exécution des builds, la gestion des intégrations continues et des déploiements continus, les tests (notamment les tests unitaires et les tests d’IU), l’exécution de différentes formes de diagnostics dans les environnements de développement et de production, ainsi que la surveillance en temps réel des performances des applications et des comportements des utilisateurs par le biais de la télémétrie et l’analyse.

 Visual Studio, Visual Studio Team Services et Team Foundation Server fournissent de nombreuses fonctionnalités DevOps, également appelées fonctionnalités Application Lifecycle Management (ALM). Beaucoup d’entre elles sont applicables aux projets multiplateformes, notamment les jeux et les applications graphiques immersives créés avec Unity, en particulier quand C# est utilisé comme langage de script. Toutefois, comme Unity possède son propre environnement de développement et son propre moteur d'exécution, plusieurs fonctionnalités ALM ne s'appliquent pas comme elles le feraient pour d'autres types de projets créés dans Visual Studio.

 Les tableaux ci-dessous identifient la façon dont les fonctionnalités ALM de Visual Studio s’appliquent ou ne s’appliquent pas quand vous utilisez Unity. Pour plus d'informations sur les fonctionnalités, cliquez sur les liens correspondants.

## <a name="agile-tools"></a>Outils agiles

Lien de référence : [À propos des outils agiles et de la gestion de projet agile](/vsts/work/backlogs/overview?view=vsts) (avec Visual Studio Team Services ou TFS, notamment Team Explorer Everywhere)

Commentaire général : toutes les fonctionnalités de planification et de suivi sont indépendantes du type de projet et des langages de codage.

|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|
|-------------|--------------------------|-------------------------|
|Gérer les backlogs et les sprints|Oui||
|Suivi du travail|Oui||
|Collaboration dans la salle d'équipe|Oui||
|Tableaux kanban|Oui||
|Créer des rapports sur la progression et la visualiser|Oui||

## <a name="modeling"></a>Modélisation

Lien de référence : **[Analyser et modéliser l’architecture](../modeling/analyze-and-model-your-architecture.md)**

Commentaire général : bien que ces fonctionnalités de conception soient indépendantes du langage de codage ou qu’elles utilisent des langages .NET tels que C#, elles opèrent selon un modèle d’application traditionnel avec des hiérarchies d’objets et des relations de classes. La conception d'un jeu dans Unity implique un modèle entièrement différent, à savoir des relations d'objets graphiques, de sons, de nuanceurs, de scripts, etc. Pour cette raison, les outils de diagramme de modélisation Visual Studio ne sont pas particulièrement pertinents pour l'ensemble d'un projet Unity. Ils peuvent être utilisés pour gérer les relations au sein des scripts C#, mais ce n'est qu'une partie de l'ensemble.

|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|
|-------------|--------------------------|-------------------------|
|Diagrammes de séquence|Non||
|Graphiques de dépendance|Non||
|Hiérarchie d'appels|Non||
|Concepteur de classes|Non||
|Navigateur de l'architecture|Non||
|Diagrammes UML (cas d'usage, activité, classe, composant, séquence et DSL)|Non||
|Diagrammes de couche|Non||
|Validation de couche|Non||

## <a name="code"></a>Code

|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|
|-------------|--------------------------|-------------------------|
|[Utiliser Team Foundation Version Control](/vsts/tfvc/overview?view=vsts) ou Visual Studio Team Services|Oui|Les projets Unity se résument à une collection de fichiers qui peuvent être placés dans des systèmes de gestion de version comme n’importe quel autre projet. Toutefois, vous devez prendre en compte certaines considérations particulières décrites après le tableau ci-dessous.|
|[Bien démarrer avec Git dans Team Services](/vsts/git/gitquickstart?view=vsts&tabs=visual-studio)|Oui|Consultez les remarques après le tableau.|
|[Améliorer la qualité du code](../test/improve-code-quality.md)|Oui||
|[Rechercher les modifications de code et d’autres historiques](../ide/find-code-changes-and-other-history-with-codelens.md)|Oui||
|[Utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)|Oui||

 Considérations particulières sur la gestion de version avec Unity :

1.  Unity assure le suivi des métadonnées relatives aux ressources de jeu dans une bibliothèque opaque unique qui est masquée par défaut. Pour maintenir la synchronisation des fichiers et des métadonnées, il est nécessaire de rendre visibles les métadonnées et de les stocker dans des segments plus gérables. Pour plus d’informations, consultez [Utilisation des systèmes de gestion de version externes avec Unity](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (documentation Unity).

2.  Tous les fichiers et dossiers figurant dans un projet Unity ne sont pas appropriés pour le contrôle de code source, comme cela est également décrit dans le lien ci-dessus. Les dossiers Assets et ProjectSettings doivent être ajoutés, contrairement aux dossiers Library et Temp. Pour obtenir une liste supplémentaire de fichiers générés qui ne sont pas traités par le contrôle de code source, consultez la discussion [How to use Git for Unity3D source control?](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) sur StackOverflow. De leur côté, de nombreux développeurs ont également blogué sur ce sujet.

3.  Les ressources binaires d'un projet Unity, telles que les textures et les fichiers audio, peuvent occuper une grande quantité de stockage. Des systèmes de contrôle de code source tels que Git stockent une copie unique d'un fichier pour chaque modification effectuée, même si la modification affecte uniquement une petite partie du fichier. Cette opération peut provoquer la saturation du référentiel Git. Pour résoudre ce problème, les développeurs Unity choisissent souvent de n'ajouter que les ressources finales à leur référentiel et d'utiliser un autre moyen de conserver un historique de l'utilisation de leurs ressources, telles que OneDrive, DropBox ou git-annex. Cette approche fonctionne, car il n’est généralement pas nécessaire de gérer les versions de ce type de ressources avec les modifications du code source. Généralement, les développeurs définissent aussi le mode de sérialisation de ressources de l’éditeur du projet sur Forcer le texte pour stocker les fichiers de séquence dans du texte plutôt que dans un format binaire, ce qui permet des fusions dans le contrôle de code source. Pour plus d’informations, consultez [Paramètres de l’éditeur](http://docs.unity3d.com/Manual/class-EditorManager.html) (documentation Unity).

## <a name="build"></a>Générer
 Lien de référence : **[Build et mise en production](/vsts/build-release/index)**

|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|
|-------------|--------------------------|-------------------------|
|Serveur TFS local|Possible|Les projets Unity sont créés via l'environnement Unity et non via le système de génération de Visual Studio (la génération dans Visual Studio Tools pour Unity entraîne la compilation des scripts, mais ne produit pas de fichier exécutable). Comme il est possible de [générer des projets Unity à partir de la ligne de commande](http://docs.unity3d.com/Manual/CommandLineArguments.html) (documentation Unity), il est possible de configurer un processus MSBuild sur un serveur TFS pour exécuter les commandes Unity appropriées, à condition que Unity lui-même soit installé sur cet ordinateur.<br /><br /> Unity propose également [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), qui surveille un dépôt Git ou SVN, et exécute des builds périodiques. Actuellement, il ne fonctionne pas avec Team Foundation Version Control, ni avec Visual Studio Team Services.|
|Serveur de builds local lié à Visual Studio Team Services|Possible|Dans les mêmes conditions que ci-dessus, il est également possible de diriger des builds déclenchées via Visual Studio Team Services pour utiliser un ordinateur TFS local.  Pour obtenir des instructions, consultez [Agents de build et de mise en production](/vsts/build-release/concepts/agents/agents).|
|Service de contrôleur hébergé de Visual Studio Team Services|Non|Les builds Unity ne sont pas prises en charge.|
|Définitions de builds avec des pré-scripts et des post-scripts|Oui|Une définition de build personnalisée qui utilise la ligne de commande Unity pour exécuter une build peut également être configurée pour des scripts de pré- ou post-compilation.|
|Intégration continue, y compris les archivages contrôlés|Oui|Archivages contrôlés pour TFVC uniquement si Git utilise un modèle de requête d'extraction plutôt que des archivages.|

## <a name="testing"></a>Test

|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|
|-------------|--------------------------|-------------------------|
|Planification de tests, création de cas de test et organisation de suites de tests|Oui||
|Test manuel|Oui||
|Gestionnaire de tests (enregistrer et rejouer des tests)|Appareils Windows et émulateurs Android uniquement||
|Couverture du code|N/A|Non applicable car le test unitaire se produit dans Unity et non dans Visual Studio. Voir ci-dessous.|
|[Tests unitaires sur votre code](../test/unit-test-your-code.md)|Dans Unity, mais pas dans Visual Studio|Unity fournit son propre framework de tests unitaires dans les [Outils de test Unity](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity Asset Store). Les résultats des tests unitaires sont signalés dans Unity et ne seront pas visibles dans Visual Studio.|
|[Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md)|Non|Les tests codés de l’interface utilisateur s’appuient sur des contrôles lisibles dans l’interface utilisateur de l’application. Les applications Unity sont graphiques par nature et le contenu n’est donc pas lisible par les outils de test codés de l’interface utilisateur.|

## <a name="improve-code-quality"></a>Améliorer la qualité du code

Lien de référence : **[Améliorer la qualité du code](../test/improve-code-quality.md)**

|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|
|-------------|--------------------------|-------------------------|
|[Analyser la qualité du code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Oui|Permet d’analyser le code de script C# dans Visual Studio.|
|[Rechercher du code dupliqué à l’aide de la détection de clone de code](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Oui|Permet d’analyser le code de script C# dans Visual Studio.|
|[Mesurer la complexité et la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Oui|Permet d’analyser le code de script C# dans Visual Studio.|
|[Explorateur de performances](../profiling/performance-explorer.md)|Non|Utilisez le [profileur Unity](http://docs.unity3d.com/Manual/Profiler.html) (site web Unity).|
|[Analyser les problèmes de mémoire liés au .NET Framework](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|Non|Visual Studio Tools n’a pas de hook au framework Mono (tels qu'ils sont utilisés par Unity) pour le profilage. Utilisez le [profileur Unity](http://docs.unity3d.com/Manual/Profiler.html) (documentation Unity).|

## <a name="release-management"></a>Gestion des versions

Lien de référence : [Vue d’ensemble de build et mise en production](/vsts/pipelines/overview?view=vsts)

|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|
|-------------|--------------------------|-------------------------|
|Gérer les processus de publication des versions|Oui||
|Déploiement sur des serveurs pour le chargement de version test via des scripts|Oui||
|Télécharger vers le magasin d'applications|Partial|Il existe des extensions qui peuvent automatiser ce processus pour certains magasins d’applications.  Consultez [Extensions pour Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), par exemple l’[extension pour Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Analyser avec HockeyApp

Lien de référence : **[Analyser avec HockeyApp](https://www.hockeyapp.net/features/)**

|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|
|-------------|--------------------------|-------------------------|
|Analyse des incidents, télémétrie et distribution des bêta|Oui|HockeyApp est particulièrement utile pour gérer la distribution des bêta et obtenir des rapports d’incidents.<br /><br /> Pour la télémétrie des scripts C#, il est possible d’utiliser n’importe quel framework d’analytique à condition qu’il s’exécute sur la version de .NET utilisée par Unity. Toutefois, cette solution permet l'analyse seulement dans les scripts de jeu et pas plus profondément dans le moteur Unity. Il n’existe aucun plug-in pour Application Insights, mais des plug-ins sont disponibles pour d’autres solutions d’analyse, par exemple [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) et [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Les services tels que Unity Analytics qui comprennent la nature d'un projet Unity fournissent bien entendu une analyse beaucoup plus explicite que les frameworks génériques.|