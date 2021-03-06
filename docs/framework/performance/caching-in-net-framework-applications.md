---
title: Mise en cache dans les applications .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
author: tdykstra
ms.openlocfilehash: 9fc63f860bad96d7dd304de31dd6e9b6626c90b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721074"
---
# <a name="caching-in-net-framework-applications"></a>Mise en cache dans les applications .NET Framework
La mise en cache vous permet de stocker des données en mémoire pour y accéder rapidement. Quand vous accédez à nouveau aux données, les applications peuvent obtenir les données à partir du cache au lieu de devoir les récupérer à partir de la source d’origine. Cela peut améliorer les performances et la scalabilité. La mise en cache rend également les données disponibles quand la source de données est temporairement indisponible.  
  
 Le .NET Framework fournit des fonctionnalités de mise en cache que vous pouvez utiliser pour améliorer les performances et la scalabilité des applications clientes et de serveur Windows, notamment ASP.NET.  
  
> [!NOTE]
>  Dans le [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et versions antérieures, ASP.NET fournissait une implémentation du cache en mémoire dans l’espace de noms <xref:System.Web.Caching>. Dans les versions précédentes du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], la mise en cache était disponible uniquement dans l’espace de noms <xref:System.Web> et nécessitait donc une dépendance vis-à-vis des classes ASP.NET. Dans le .NET Framework 4, l’espace de noms <xref:System.Runtime.Caching> contient des API conçues pour les applications web et non-web.  
  
## <a name="caching-data"></a>Mise en cache des données  
 Vous pouvez mettre en cache des informations à l’aide des classes de l’espace de noms <xref:System.Runtime.Caching>. Les classes de mise en cache dans cet espace de noms fournissent les fonctionnalités suivantes :  
  
-   Des types abstraits qui fournissent la base pour la création d’implémentations de cache personnalisées  
  
-   Une implémentation de cache d’objets en mémoire concrète  
  
 La classe de mise en cache de base abstraite (<xref:System.Runtime.Caching.ObjectCache>) définit les tâches de mise en cache suivantes :  
  
-   Création et gestion des entrées de cache  
  
-   Spécification des informations d’expiration et d’éviction  
  
-   Événements déclenchés en réponse aux modifications apportées aux entrées de cache  
  
 La classe <xref:System.Runtime.Caching.MemoryCache> est une implémentation de cache d’objets en mémoire de la classe <xref:System.Runtime.Caching.ObjectCache>. Vous pouvez utiliser la classe <xref:System.Runtime.Caching.MemoryCache> pour la plupart des tâches de mise en cache.  
  
> [!NOTE]
>  La classe <xref:System.Runtime.Caching.MemoryCache> est modélisée sur l’objet de cache ASP.NET qui est défini dans l’espace de noms <xref:System.Web.Caching>. Par conséquent, la logique de mise en cache interne est similaire à la logique fournie dans les versions antérieures d’ASP.NET.  
  
 Pour obtenir un exemple montrant comment utiliser la mise en cache dans une application WPF, consultez [procédure pas à pas : La mise en cache des données d’Application dans une Application WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## <a name="caching-in-aspnet-applications"></a>Mise en cache dans les applications ASP.NET  
 Les classes de mise en cache dans l’espace de noms <xref:System.Runtime.Caching> fournissent la fonctionnalité de mise en cache des données dans ASP.NET.  
  
> [!NOTE]
>  Si votre application cible le [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ou antérieur, vous devez utiliser les classes de mise en cache définies dans l’espace de noms <xref:System.Web.Caching>. Pour plus d’informations, consultez [Vue d’ensemble de la mise en cache ASP.NET](https://msdn.microsoft.com/library/5ec28012-4972-4dc3-b3e8-9d20401fe11d).  
  
> [!NOTE]
>  Quand vous développez de nouvelles applications, nous vous recommandons d’utiliser la classe <xref:System.Runtime.Caching.MemoryCache>. L’API fournie dans l’espace de noms <xref:System.Runtime.Caching> est semblable à celle fournie dans l’espace de noms <xref:System.Web.Caching.Cache>. Ainsi, elle vous sera familière si vous utilisiez la mise en cache dans les versions antérieures d’ASP.NET. Pour obtenir un exemple montrant comment utiliser la mise en cache dans les applications ASP.NET, consultez [procédure pas à pas : La mise en cache des données d’Application dans ASP.NET](https://msdn.microsoft.com/library/942236f6-0138-4aaf-af71-a5ea451a1e23).  
  
### <a name="output-caching"></a>Mise en cache de sortie  
 Pour mettre manuellement en cache les données d’application, vous pouvez utiliser la classe <xref:System.Runtime.Caching.MemoryCache> dans ASP.NET. ASP.NET prend également en charge la mise en cache de sortie, qui stocke la sortie générée des pages, des contrôles et des réponses HTTP en mémoire. Vous pouvez configurer la mise en cache de sortie de façon déclarative dans une page web ASP.NET ou à l’aide de paramètres dans le fichier Web.config. Pour plus d’informations, consultez [outputCache, élément de caching (Schéma des paramètres ASP.NET)](https://msdn.microsoft.com/library/47cd2b47-316f-4dfd-bbf8-539be3066fee).  
  
 ASP.NET vous permet d’étendre la mise en cache de sortie en créant des fournisseurs de cache de sortie personnalisés. Grâce aux fournisseurs personnalisés, vous pouvez stocker le contenu mis en cache à l’aide d’autres dispositifs de stockage tels que des disques, le stockage cloud et des moteurs de cache distribué. Pour créer un fournisseur de cache de sortie personnalisé, vous devez créer une classe qui dérive de la classe <xref:System.Web.Caching.OutputCacheProvider> et configurer l’application pour qu’elle utilise le fournisseur de cache de sortie personnalisé.  
  
## <a name="caching-in-wcf-rest-services"></a>Mise en cache dans les services REST WCF  
 Pour les services REST WCF, le .NET Framework vous permet de tirer parti de la mise en cache de sortie déclarative disponible dans ASP.NET. Cela vous permet de mettre en cache les réponses provenant de vos opérations de service REST WCF. Quand un utilisateur envoie une requête HTTP GET à un service configuré pour la mise en cache, ASP.NET renvoie la réponse mise en cache et la méthode de service n’est pas appelée. Une fois le cache expiré, au prochain envoi d’une requête HTTP GET par un utilisateur, votre méthode de service est appelée et la réponse est à nouveau mise en cache.  
  
 Le .NET Framework vous permet également d’implémenter une mise en cache HTTP GET conditionnelle. Dans les scénarios REST, une requête HTTP GET conditionnelle est souvent utilisée par les services pour implémenter une mise en cache HTTP intelligente, comme décrit dans [HTTP Specification](https://go.microsoft.com/fwlink/?LinkId=165800). Pour plus d’informations, consultez [Prise en charge de la mise en cache pour les services HTTP Web WCF](https://go.microsoft.com/fwlink/?LinkId=184598).  
  
## <a name="extending-caching-in-the-net-framework"></a>Extension de la mise en cache dans le .NET Framework  
 La mise en cache dans le .NET Framework est conçue pour être extensible. La classe <xref:System.Runtime.Caching.ObjectCache> vous permet de créer une implémentation de cache personnalisée. Cette classe fournit des membres accessibles à toutes les applications managées, notamment Windows Forms, Windows Presentation Foundation (WPF) et Windows Communication Foundation (WCF). Vous pouvez ainsi créer une classe de cache qui utilise un mécanisme de stockage différent, ou obtenir un contrôle précis des opérations de cache.  
  
 Pour étendre la mise en cache, vous pouvez effectuer les étapes ci-dessous :  
  
-   Créer une classe personnalisée qui dérive de la classe <xref:System.Runtime.Caching.ObjectCache>, puis fournir une implémentation de cache personnalisée dans la classe dérivée.  
  
-   Créer une classe qui dérive de la classe <xref:System.Runtime.Caching.MemoryCache> et personnaliser et étendre la classe dérivée. Pour obtenir un exemple illustrant comment procéder, consultez [Caching Application Data by Using Multiple Cache Objects in an ASP.NET Application](https://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx).  
  
-   Créer une classe qui dérive de la classe <xref:System.Web.Caching.OutputCacheProvider> et configurer l’application pour qu’elle utilise le fournisseur de cache de sortie personnalisé.  
  
 Pour plus d’informations, consultez l’entrée [Extensible Output Caching with ASP.NET 4 (VS 2010 and .NET 4.0 Series)](https://go.microsoft.com/fwlink/?LinkId=185772) sur le blog de Scott Guthrie.  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching.MemoryCache>
- [Procédure pas à pas : La mise en cache des données d’Application dans une Application WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
- [Procédure pas à pas : La mise en cache des données d’Application dans ASP.NET](https://msdn.microsoft.com/library/942236f6-0138-4aaf-af71-a5ea451a1e23)
