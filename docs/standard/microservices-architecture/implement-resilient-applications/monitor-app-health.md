---
title: Supervision de l’intégrité
description: Explorez un moyen d’implémenter la supervision de l’intégrité.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 666b55608ca4e5d18448e1a0b4a1735f3e856474
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362481"
---
# <a name="health-monitoring"></a>Supervision de l’intégrité

La supervision de l’intégrité fournit des informations quasiment en temps réel sur l’état de vos conteneurs et microservices. La supervision de l’intégrité est primordiale pour de multiples aspects du fonctionnement des microservices. Elle est particulièrement importante quand des orchestrateurs effectuent des mises à niveau d’application partielles par étapes, comme nous l’expliquerons plus tard.

Les applications basées sur des microservices utilisent souvent des pulsations ou des vérifications d’intégrité pour permettre à leurs analyseurs de performances, planificateurs et orchestrateurs d’assurer le suivi des divers services. Si les services n’ont pas le moyen d’envoyer un signal de type « Je suis actif », à la demande ou selon une planification établie, votre application risque de connaître des problèmes quand vous déployez des mises à jour, ou elle risque simplement de détecter les défaillances trop tard et de ne pas être en mesure d’arrêter les défaillances en cascade, susceptibles au final d’entraîner des pannes majeures.

Dans le modèle standard, les services envoient des rapports sur leur état, et ces informations sont agrégées pour fournir une vue d’ensemble de l’état d’intégrité de votre application. Si vous utilisez un orchestrateur, vous pouvez envoyer des informations d’intégrité au cluster de l’orchestrateur, afin que le cluster sache quelles actions exécuter. Si vous optez pour des rapports d’intégrité complets et personnalisés pour votre application, vous pouvez détecter et résoudre les problèmes de votre application en cours d’exécution beaucoup plus facilement.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Implémenter des vérifications d’intégrité dans les services ASP.NET Core

Quand vous développez un microservice ou une application web ASP.NET Core, vous pouvez utiliser une bibliothèque hors bande expérimentale (non officiellement intégrée à ASP.NET Core et désormais déprécié) nommée *HealthChecks*, fournie par l’équipe d’ASP.NET. Elle est disponible dans ce [dépôt GitHub dotnet-architecture](https://github.com/dotnet-architecture/HealthChecks). Toutefois, la version officielle de *HealthChecks* [sera publiée dans ASP.NET Core 2.2](https://github.com/aspnet/Announcements/issues/307) (publication officielle prévue d’ici la fin de l’année 2018).

Cette bibliothèque est simple d’emploi. Ses fonctionnalités vous permettent de vérifier le bon fonctionnement de chaque ressource externe spécifique nécessaire pour votre application (par exemple, une base de données SQL Server ou une API distante). Avec cette bibliothèque, vous pouvez également déterminer à quel moment une ressource est considérée comme intègre, comme nous l’expliquerons plus tard.

Pour pouvoir utiliser cette bibliothèque, vous devez d’abord utiliser la bibliothèque dans vos microservices. Ensuite, vous avez besoin d’une application front-end qui demande des rapports d’intégrité. Cette application front-end peut être une application de création de rapports personnalisée, ou un orchestrateur qui adapte ses actions en fonction des états d’intégrité retournés.

### <a name="use-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>Utiliser la bibliothèque HealthChecks dans vos microservices ASP.NET back-end

Vous pouvez voir de quelle façon la bibliothèque HealthChecks est utilisée dans l’exemple d’application eShopOnContainers. Pour commencer, vous devez définir ce qui constitue un état intègre pour chaque microservice. Dans l’exemple d’application, les microservices sont intègres si l’API du microservice est accessible via HTTP et si sa base de données SQL Server associée est également disponible.

Ultérieurement, vous pourrez installer la bibliothèque HealthChecks sous forme de package NuGet. Mais à ce jour, vous devez télécharger et compiler le code au sein de votre solution. Clonez le code disponible sur <https://github.com/dotnet-architecture/HealthChecks> et copiez les dossiers suivants dans votre solution :

- src/common
- src/Microsoft.AspNetCore.HealthChecks
- src/Microsoft.Extensions.HealthChecks
- src/Microsoft.Extensions.HealthChecks.SqlServer

Vous pourriez également ajouter des vérifications supplémentaires telles que celles pour Azure (Microsoft.Extensions.HealthChecks.AzureStorage), mais étant donné que cette version d’eShopOnContainers n’a pas de dépendance sur Azure, cela est inutile. Vous n’avez pas besoin des vérifications d’intégrité ASP.NET, car l’application eShopOnContainers est basée sur ASP.NET Core.

La Figure 8-7 illustre la bibliothèque HealthChecks dans Visual Studio, qui peut être utilisée directement comme composant par les microservices.

![Vue du dossier HealthChecks dans l’Explorateur de solutions, montrant les trois projets.](./media/image6.png)

**Figure 8-7**. Code source de la bibliothèque HealthChecks ASP.NET Core dans une solution Visual Studio

Comme nous l’avons dit précédemment, la première chose à faire dans chaque projet de microservice est d’ajouter une référence aux trois bibliothèques HealthChecks. Après cela, vous ajoutez les actions de vérification d’intégrité que vous souhaitez effectuer dans ce microservice. Ces actions sont essentiellement des dépendances sur d’autres microservices (HttpUrlCheck) ou bases de données (SqlCheck\* pour les bases de données SQL Server). Vous ajoutez l’action au sein de la classe Startup de chaque microservice ASP.NET ou application web ASP.NET.

Vous devez configurer chaque service ou application web en ajoutant toutes leurs dépendances HTTP ou de base de données en tant que méthode AddHealthCheck unique. Par exemple, pour l’application web MVC d’eShopOnContainers qui dépend de nombreux services, plusieurs méthodes AddCheck sont ajoutées aux vérifications d’intégrité.

Par exemple, le code (simplifié) suivant montre de quelle façon le microservice Catalog ajoute une dépendance envers sa base de données SQL Server.

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

Toutefois, l’application web MVC d’eShopOnContainers a de multiples dépendances sur les autres microservices. Par conséquent, elle appelle une méthode AddUrlCheck pour chaque microservice, comme illustré dans l’exemple (simplifié) suivant :

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

Un microservice ne présente donc pas l’état « intègre » si toutes ses vérifications ne sont pas également intègres.

Si le microservice n’a pas de dépendance sur un service ou sur SQL Server, vous devez simplement ajouter une vérification Healthy("Ok"). Le code suivant provient du microservice `basket.api` d’eShopOnContainers. (Le microservice basket utilise le cache Redis, mais la bibliothèque ne contient pas encore de fournisseur de vérification d’intégrité Redis.)

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

Pour permettre à un service ou une application web d’exposer le point de terminaison de la vérification d’intégrité, il faut activer la méthode d’extension `UseHealthChecks([*url_for_health_checks*])`. Cette méthode est spécifiée au niveau de `WebHostBuilder` dans la méthode principale de la classe `Program` de votre service ou application web ASP.NET Core, juste après <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder>, comme indiqué dans le code (simplifié) suivant :

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = WebHost.CreateDefaultBuilder(args)
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseStartup<Startup>()
                .Build();

            host.Run();
        }
    }
}
```

Le processus est le suivant : chaque microservice expose le point de terminaison /hc. Ce point de terminaison est créé par le middleware de la bibliothèque HealthChecks ASP.NET Core. Quand ce point de terminaison est appelé, il exécute toutes les vérifications d’intégrité qui sont configurées dans la méthode AddHealthChecks de la classe Startup.

La méthode UseHealthChecks attend un port ou un chemin. Ce port ou chemin est le point de terminaison à utiliser pour vérifier l’état d’intégrité du service. Par exemple, le microservice Catalog utilise le chemin /hc.

### <a name="cache-health-check-responses"></a>Mettre en cache les réponses de la vérification d’intégrité

Pour éviter de provoquer un déni de service (DoS) dans vos services ou tout simplement pour ne pas impacter les performances des services en vérifiant les ressources trop souvent, vous pouvez mettre en cache les informations retournées et configurer une durée de cache pour chaque vérification d’intégrité.

Par défaut, la durée de cache définie en interne est de 5 minutes, mais vous pouvez la modifier pour chaque vérification d’intégrité, comme dans le code suivant :

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Interroger vos microservices pour connaître leur état d’intégrité

Quand vous avez configuré les vérifications d’intégrité décrites dans cet article et que le microservice est en cours d’exécution dans Docker, vous pouvez directement vérifier son intégrité à partir d’un navigateur.

Vous devez publier le port du conteneur dans l’hôte Docker, afin de pouvoir accéder au conteneur par le biais de `localhost` ou de l’adresse IP d’hôte Docker externe, comme illustré par la Figure 8-8.

![Affichage dans le navigateur de la réponse JSON retournée par une vérification d’intégrité](./media/image7.png)

**Figure 8-8**. Vérification de l’état d’intégrité d’un service à partir d’un navigateur

Dans ce test, vous pouvez voir que le microservice catalog.api (exécuté sur le port 5101) est intègre, et qu’il retourne l’état HTTP 200 et les informations d’état dans JSON. Cela signifie aussi qu’en interne le service a également vérifié l’intégrité de sa dépendance à la base de données SQL Server et que la vérification d’intégrité l’a elle-même considérée comme intègre.

## <a name="use-watchdogs"></a>Utiliser des pilotes de surveillance

Un pilote de surveillance est un service distinct qui peut surveiller l’intégrité et la charge parmi les services, et fournir des informations sur l’intégrité des microservices en interrogeant la bibliothèque `HealthChecks` présentée plus haut. Cela peut vous aider à éviter des erreurs qui ne sont pas détectées dans l’affichage d’un seul service. Les pilotes de surveillance sont également un bon emplacement de stockage pour le code qui peut effectuer des actions de correction dans des conditions connues sans intervention de l’utilisateur.

L’exemple eShopOnContainers contient une page web qui affiche des exemples de rapports de vérification d’intégrité, comme illustré à la Figure 8-9. Il s’agit du pilote de surveillance le plus simple que vous pouvez avoir, car il ne fait qu’afficher l’état des microservices et des applications web dans eShopOnContainers. En règle générale, un pilote de surveillance exécute aussi certaines actions quand il détecte des états non intègres.

![Affichage dans le navigateur de l’application WebStatus, montrant l’état d’intégrité de cinq microservices d’eShopOnContainers](./media/image8.png)

**Figure 8-9**. Exemple de rapport de vérification d’intégrité dans eShopOnContainers

En résumé, le middleware ASP.NET de la bibliothèque HealthChecks ASP.NET Core fournit un point de terminaison de vérification d’intégrité unique pour chaque microservice. Ce point de terminaison exécute toutes les vérifications d’intégrité définies et retourne un état d’intégrité général si toutes ces vérifications sont intègres.

La bibliothèque HealthChecks est extensible et contiendra de nouvelles vérifications d’intégrité des ressources externes dans le futur. Par exemple, nous prévoyons à l’avenir d’ajouter à la bibliothèque des vérifications d’intégrité pour le cache Redis et d’autres bases de données. La bibliothèque permet la création de rapports d’intégrité par plusieurs dépendances de service ou d’application. Vous pouvez ensuite prendre les actions requises en fonction des résultats de ces vérifications d’intégrité.

## <a name="health-checks-when-using-orchestrators"></a>Vérifications d’intégrité avec des orchestrateurs

Pour superviser la disponibilité de vos microservices, les orchestrateurs tels que Kubernetes et Service Fabric effectuent régulièrement des vérifications d’intégrité en envoyant des requêtes pour tester les microservices. Quand un orchestrateur détermine qu’un service ou conteneur n’est pas intègre, il arrête le routage des requêtes vers cette instance. Généralement, il crée aussi une autre instance de ce conteneur.

Par exemple, la plupart des orchestrateurs peuvent utiliser des vérifications d’intégrité pour gérer les déploiements sans temps d’arrêt. L’orchestrateur démarre le routage du trafic vers les instances d’un service ou conteneur uniquement quand l’état du service ou conteneur est de nouveau intègre.

La surveillance de l’intégrité est particulièrement importante quand un orchestrateur effectue une mise à niveau d’application. Certains orchestrateurs (comme Azure Service Fabric) mettent à jour les services par étapes. Par exemple, ils peuvent mettre à jour un cinquième de la surface du cluster pour chaque mise à niveau d’application. L’ensemble de nœuds mis à niveau en même temps est appelé *domaine de mise à niveau*. Une fois que chaque domaine de mise à niveau a été mis à niveau et est disponible pour les utilisateurs, le domaine doit passer les vérifications d’intégrité avant que le déploiement continue dans le domaine de mise à niveau suivant.

Un autre aspect de l’intégrité des services est la création de rapports de métriques à partir d’un service. Il s’agit d’une fonctionnalité avancée du modèle d’intégrité de certains orchestrateurs, comme Service Fabric. Les métriques sont importantes quand vous utilisez un orchestrateur, car elles aident à équilibrer l’utilisation des ressources. Elles sont également un indicateur de l’intégrité du système. Par exemple, une application inclut de nombreux microservices et chaque instance fournit une métrique de demandes par seconde (RPS). Si un service utilise davantage de ressources (mémoire, processeur, etc.) qu’un autre service, l’orchestrateur peut déplacer des instances du service dans le cluster pour mieux équilibrer l’utilisation des ressources entre les services.

Notez qu’Azure Service Fabric fournit son propre [modèle de vérification d’intégrité](/azure/service-fabric/service-fabric-health-introduction), qui est plus performant que les vérifications d’intégrité simples.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Surveillance avancée : visualisation, analyse et alertes

La dernière partie de la surveillance est la visualisation du flux d’événements, la création de rapports sur les performances des services et l’envoi d’alertes quand un problème est détecté. Différentes solutions sont disponibles pour cet aspect de la surveillance.

Vous pouvez utiliser des applications personnalisées simples qui affichent l’état de vos services. C’est le cas de la page personnalisée présentée dans la section sur [ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks). Ou vous pouvez utiliser des outils plus avancés, comme Azure Application Insights, pour déclencher des alertes en fonction du flux d’événements.

Pour finir, si vous stockez tous les flux d’événements, vous pouvez utiliser Microsoft Power BI ou d’autres solutions comme Kibana ou Splunk pour visualiser les données.

## <a name="additional-resources"></a>Ressources supplémentaires

- **ASP.NET Core HealthChecks** (version expérimentale)\
  [*https://github.com/dotnet-architecture/HealthChecks/*](https://github.com/dotnet-architecture/HealthChecks/)

- **Présentation de la supervision de l’intégrité de Service Fabric**\
  [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Application Insights**\
  [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

- **Microsoft Operations Management Suite**\
  [*https://www.microsoft.com/cloud-platform/operations-management-suite*](https://www.microsoft.com/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
>[Précédent](implement-circuit-breaker-pattern.md)
>[Suivant](../secure-net-microservices-web-applications/index.md)