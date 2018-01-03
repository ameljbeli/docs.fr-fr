---
title: Architecturer des applications web modernes avec ASP.NET Core et Azure
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Introduction
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 93a74bb7ba537d3c7c0291f7903112dc470133a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="90900-103">Architecturer des applications web modernes avec ASP.NET Core et Azure</span><span class="sxs-lookup"><span data-stu-id="90900-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

<span data-ttu-id="90900-104">.NET Core et ASP.NET Core offrent plusieurs avantages par rapport au développement .NET classique.</span><span class="sxs-lookup"><span data-stu-id="90900-104">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="90900-105">Il est recommandé d’utiliser .NET Core pour vos applications serveur si tout ou partie des éléments suivants sont importants pour la réussite de votre application :</span><span class="sxs-lookup"><span data-stu-id="90900-105">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

-   <span data-ttu-id="90900-106">Prise en charge multiplateforme</span><span class="sxs-lookup"><span data-stu-id="90900-106">Cross-platform support</span></span>

-   <span data-ttu-id="90900-107">Utilisation de microservices</span><span class="sxs-lookup"><span data-stu-id="90900-107">Use of microservices</span></span>

-   <span data-ttu-id="90900-108">Utilisation de conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="90900-108">Use of Docker containers</span></span>

-   <span data-ttu-id="90900-109">Nécessité de hautes performances et de scalabilité</span><span class="sxs-lookup"><span data-stu-id="90900-109">High performance and scalability requirements</span></span>

-   <span data-ttu-id="90900-110">Gestion des versions côte à côte des versions de .NET par application sur le même serveur</span><span class="sxs-lookup"><span data-stu-id="90900-110">Side-by-side versioning of .NET versions by application on the same server</span></span>

<span data-ttu-id="90900-111">Les applications .NET classiques prennent en charge ces spécifications, mais ASP.NET Core et .NET Core ont été optimisés pour offrir une prise en charge améliorée des scénarios ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="90900-111">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="90900-112">De plus en plus d’organisations choisissent d’héberger leurs applications web dans le cloud en utilisant des services comme Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="90900-112">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="90900-113">Envisagez d’héberger votre application dans le cloud si les points suivants sont importants pour votre application ou votre organisation :</span><span class="sxs-lookup"><span data-stu-id="90900-113">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

-   <span data-ttu-id="90900-114">Réduction des investissements dans les coûts des centres de données (matériel, logiciel, espace, utilitaires, etc.)</span><span class="sxs-lookup"><span data-stu-id="90900-114">Reduced investment in data center costs (hardware, software, space, utilities, etc)</span></span>

-   <span data-ttu-id="90900-115">Tarification flexible (paiement basé sur l’utilisation et non pas pour une capacité inactive)</span><span class="sxs-lookup"><span data-stu-id="90900-115">Flexible pricing (pay based on usage, not for idle capacity)</span></span>

-   <span data-ttu-id="90900-116">Extrême fiabilité</span><span class="sxs-lookup"><span data-stu-id="90900-116">Extreme reliability</span></span>

-   <span data-ttu-id="90900-117">Mobilité accrue de l’application ; changement facile de l’endroit et de la façon dont votre application est déployée</span><span class="sxs-lookup"><span data-stu-id="90900-117">Improved app mobility; easily change where and how your app is deployed</span></span>

-   <span data-ttu-id="90900-118">Capacité flexible ; montée ou descente en puissance en fonction des besoins réels</span><span class="sxs-lookup"><span data-stu-id="90900-118">Flexible capacity; scale up or down based on actual needs</span></span>

<span data-ttu-id="90900-119">La création d’applications web avec ASP.NET Core, hébergées dans Microsoft Azure, offre de nombreux avantages concurrentiels par rapport aux alternatives classiques.</span><span class="sxs-lookup"><span data-stu-id="90900-119">Building web applications with ASP.NET Core, hosted in Microsoft Azure, offers numerous competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="90900-120">ASP.NET Core est optimisé pour les pratiques de développement d’applications web modernes et les scénarios d’hébergement cloud.</span><span class="sxs-lookup"><span data-stu-id="90900-120">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="90900-121">Dans ce guide, vous découvrez comment architecturer vos applications ASP.NET Core pour tirer le meilleur parti de ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="90900-121">In this guide, you will learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="90900-122">Objectif</span><span class="sxs-lookup"><span data-stu-id="90900-122">Purpose</span></span>

<span data-ttu-id="90900-123">Ce guide fournit une aide de bout en bout sur la création d’applications web monolithiques avec ASP.NET Core et Azure.</span><span class="sxs-lookup"><span data-stu-id="90900-123">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="90900-124">Ce guide vient en complément de « *Architecting and Developing Containerized and Microservice-based Applications with .NET* », qui est davantage consacré à Docker, aux microservices et au déploiement de conteneurs pour héberger des applications d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="90900-124">This guide is complementary to the "*Architecting and Developing Containerized and Microservice-based Applications with .NET*" which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a><span data-ttu-id="90900-125">Architecture et développement d’applications basées sur des microservices en conteneur dans .NET</span><span class="sxs-lookup"><span data-stu-id="90900-125">Architecting and Developing Containerized Microservice Based Apps in .NET</span></span>
> - <span data-ttu-id="90900-126">**Livre électronique**</span><span class="sxs-lookup"><span data-stu-id="90900-126">**e-book**</span></span>  
> <span data-ttu-id="90900-127"><http://aka.ms/MicroservicesEbook></span><span class="sxs-lookup"><span data-stu-id="90900-127"><http://aka.ms/MicroservicesEbook></span></span>
> - <span data-ttu-id="90900-128">**Exemple d’application**</span><span class="sxs-lookup"><span data-stu-id="90900-128">**Sample Application**</span></span>  
> <span data-ttu-id="90900-129"><http://aka.ms/microservicesarchitecture></span><span class="sxs-lookup"><span data-stu-id="90900-129"><http://aka.ms/microservicesarchitecture></span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="90900-130">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="90900-130">Who should use this guide</span></span>

<span data-ttu-id="90900-131">Le public visé par ce guide est principalement constitué de développeurs, de responsables du développement et d’architectes qui sont intéressés par la création d’applications web modernes avec des technologies et des services Microsoft dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="90900-131">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="90900-132">Il s’adresse aussi aux décideurs techniques qui connaissent déjà ASP.NET et/ou Azure, et qui recherchent des informations sur la pertinence d’un passage à ASP.NET Core pour des projets nouveaux ou existants.</span><span class="sxs-lookup"><span data-stu-id="90900-132">A secondary audience is technical decision makers who are already familiar ASP.NET and/or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="90900-133">Utilisation de ce guide</span><span class="sxs-lookup"><span data-stu-id="90900-133">How you can use this guide</span></span>

<span data-ttu-id="90900-134">Ce guide a été condensé en un document relativement court, qui est consacré à la création d’applications web avec des technologies .NET modernes et Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="90900-134">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="90900-135">Il peut ainsi être lu dans sa totalité, et permet de comprendre ces applications et les considérations techniques qui s’y rattachent.</span><span class="sxs-lookup"><span data-stu-id="90900-135">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="90900-136">Le guide, ainsi que son exemple d’application, peut aussi servir de point de départ ou de référence.</span><span class="sxs-lookup"><span data-stu-id="90900-136">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="90900-137">Utilisez l’exemple d’application associé comme modèle pour vos propres applications, ou pour voir comment organiser les composants de votre application.</span><span class="sxs-lookup"><span data-stu-id="90900-137">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="90900-138">Reportez-vous aux principes exposés dans le guide, à la couverture des options d’architecture et de technologie, et aux considérations sur les décisions à prendre quand vous évaluez ces choix pour votre propre application.</span><span class="sxs-lookup"><span data-stu-id="90900-138">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when weighing these choices for your own application.</span></span>

<span data-ttu-id="90900-139">N’hésitez pas à faire connaître ce guide pour favoriser une compréhension partagée de ces considérations et de ces opportunités.</span><span class="sxs-lookup"><span data-stu-id="90900-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="90900-140">Le fait que chacun utilise un même ensemble de terminologie et de principes sous-jacents permet d’obtenir plus facilement une application cohérente des modèles et des pratiques en matière d’architecture.</span><span class="sxs-lookup"><span data-stu-id="90900-140">Having everybody working from a common set of terminology and underlying principles will help ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="90900-141">Références</span><span class="sxs-lookup"><span data-stu-id="90900-141">References</span></span>
- <span data-ttu-id="90900-142">**Choix entre .NET Core et .NET Framework pour les applications serveur**</span><span class="sxs-lookup"><span data-stu-id="90900-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
<span data-ttu-id="90900-143"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="90900-143"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="90900-144">[Suivant] (modern-web-applications-characteristics.md)</span><span class="sxs-lookup"><span data-stu-id="90900-144">[Next] (modern-web-applications-characteristics.md)</span></span>