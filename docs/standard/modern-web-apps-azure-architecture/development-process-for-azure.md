---
title: "Processus de développement pour Azure"
description: "Architecture des Applications Web avec ASP.NET Core et Azure | Processus de développement pour Azure"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: e676c1225f7d11381808040cf101e897e0726ad4
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="development-process-for-azure"></a><span data-ttu-id="aa223-103">Processus de développement pour Azure</span><span class="sxs-lookup"><span data-stu-id="aa223-103">Development process for Azure</span></span>

> <span data-ttu-id="aa223-104">_« Avec le cloud, particuliers et petites entreprises peuvent aligner leurs doigts et configurer instantanément les services d’entreprise. »_</span><span class="sxs-lookup"><span data-stu-id="aa223-104">_"With the cloud, individuals and small businesses can snap their fingers and instantly set up enterprise-class services."_</span></span>  
> <span data-ttu-id="aa223-105">_-Roy Stephan_</span><span class="sxs-lookup"><span data-stu-id="aa223-105">_- Roy Stephan_</span></span>

 ## <a name="vision"></a><span data-ttu-id="aa223-106">Vision</span><span class="sxs-lookup"><span data-stu-id="aa223-106">Vision</span></span>

> <span data-ttu-id="aa223-107">*Développer des applications ASP .NET Core bien conçues comme vous le souhaitez, à l’aide de Visual Studio ou l’interface CLI dotnet et Visual Studio Code ou éditeur de votre choix.*</span><span class="sxs-lookup"><span data-stu-id="aa223-107">*Develop well-designed ASP .NET Core applications the way you like, using Visual Studio or the dotnet CLI and Visual Studio Code or your editor of choice.*</span></span>

## <a name="development-environment-for-aspnet-core-apps"></a><span data-ttu-id="aa223-108">Environnement de développement pour les applications ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aa223-108">Development environment for ASP.NET Core apps</span></span>

### <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="aa223-109">Choix d’outils de développement : IDE ou éditeur</span><span class="sxs-lookup"><span data-stu-id="aa223-109">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="aa223-110">Si vous préférez un IDE complet et puissant ou un éditeur léger et agile, Microsoft a vous couvert lors du développement d’applications de base de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="aa223-110">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when developing ASP.NET Core applications.</span></span>

<span data-ttu-id="aa223-111">**Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="aa223-111">**Visual Studio 2017.**</span></span> <span data-ttu-id="aa223-112">Si vous utilisez *Visual Studio 2017* vous pouvez générer ASP.NET Core des applications, que vous avez le *.NET Core le développement multiplateforme* installé la charge de travail.</span><span class="sxs-lookup"><span data-stu-id="aa223-112">If you're using *Visual Studio 2017* you can build ASP.NET Core applications as long as you have the *.NET Core cross-platform development* workload installed.</span></span> <span data-ttu-id="aa223-113">Figure 10-1 indique la charge de travail requis dans la boîte de dialogue de programme d’installation de Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="aa223-113">Figure 10-1 shows the required workload in the Visual Studio 2017 setup dialog.</span></span>

![](./media/image10-1.png)

<span data-ttu-id="aa223-114">**Figure 10-1.**</span><span class="sxs-lookup"><span data-stu-id="aa223-114">**Figure 10-1.**</span></span> <span data-ttu-id="aa223-115">Installation de la charge de travail .NET Core dans Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="aa223-115">Installing the .NET Core workload in Visual Studio 2017.</span></span>

[<span data-ttu-id="aa223-116">Télécharger Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="aa223-116">Download Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)

<span data-ttu-id="aa223-117">**Visual Studio Code et dotnet CLI** (les outils multiplateformes pour Mac, Linux et Windows).</span><span class="sxs-lookup"><span data-stu-id="aa223-117">**Visual Studio Code and dotnet CLI** (Cross-Platform Tools for Mac, Linux and Windows).</span></span> <span data-ttu-id="aa223-118">Si vous préférez un éditeur léger et inter-plateformes prenant en charge de n’importe quel langage de développement, vous pouvez utiliser Microsoft Visual Studio Code et l’interface CLI dotnet.</span><span class="sxs-lookup"><span data-stu-id="aa223-118">If you prefer a lightweight and cross-platform editor supporting any development language, you can use Microsoft Visual Studio Code and the dotnet CLI.</span></span> <span data-ttu-id="aa223-119">Ces produits fournissent une expérience simple et robuste qui simplifie le flux de travail du développeur.</span><span class="sxs-lookup"><span data-stu-id="aa223-119">These products provide a simple yet robust experience that streamlines the developer workflow.</span></span> <span data-ttu-id="aa223-120">En outre, Visual Studio Code prend en charge des extensions pour C\# et développement web, fournissant intellisense et les tâches de raccourcis dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="aa223-120">Additionally, Visual Studio Code supports extensions for C\# and web development, providing intellisense and shortcut-tasks within the editor.</span></span>

[<span data-ttu-id="aa223-121">Télécharger le Kit de développement logiciel de .NET Core</span><span class="sxs-lookup"><span data-stu-id="aa223-121">Download the .NET Core SDK</span></span>](https://www.microsoft.com/net/download/core)

[<span data-ttu-id="aa223-122">Télécharger Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="aa223-122">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a><span data-ttu-id="aa223-123">Flux de travail de développement pour les applications hébergés par Azure ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aa223-123">Development workflow for Azure-hosted ASP.NET Core apps</span></span>

<span data-ttu-id="aa223-124">Le cycle de vie de développement d’application commence à partir de l’ordinateur de chaque développeur, l’application à l’aide de leur langue par défaut et le tester localement de codage.</span><span class="sxs-lookup"><span data-stu-id="aa223-124">The application development lifecycle starts from each developer's machine, coding the app using their preferred language and testing it locally.</span></span> <span data-ttu-id="aa223-125">Les développeurs peuvent choisir leur système de contrôle de source par défaut et peuvent configurer l’intégration continue (CI) et/ou de remise/déploiement continu (CD) à l’aide d’un serveur de builds ou en fonction des fonctionnalités intégrées de Azure.</span><span class="sxs-lookup"><span data-stu-id="aa223-125">Developers may choose their preferred source control system and can configure Continuous Integration (CI) and/or Continuous Delivery/Deployment (CD) using a build server or based on built-in Azure features.</span></span>

<span data-ttu-id="aa223-126">Pour commencer à développer une application ASP.NET Core à l’aide de l’élément de configuration/CD, vous pouvez utiliser Visual Studio Team Services ou de votre organisation possède de Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="aa223-126">To get started with developing an ASP.NET Core application using CI/CD, you can use Visual Studio Team Services or your organization's own Team Foundation Server (TFS).</span></span>

### <a name="initial-setup"></a><span data-ttu-id="aa223-127">Programme d’installation initiale</span><span class="sxs-lookup"><span data-stu-id="aa223-127">Initial Setup</span></span>

<span data-ttu-id="aa223-128">Pour créer un pipeline de mise en production pour votre application, vous devez disposer de votre code d’application dans le contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="aa223-128">To create a release pipeline for your app, you need to have your application code in source control.</span></span> <span data-ttu-id="aa223-129">Configurer un référentiel local et le connecter à un référentiel distant dans un projet d’équipe.</span><span class="sxs-lookup"><span data-stu-id="aa223-129">Set up a local repository and connect it to a remote repository in a team project.</span></span> <span data-ttu-id="aa223-130">Suivez ces instructions :</span><span class="sxs-lookup"><span data-stu-id="aa223-130">Follow these instructions:</span></span>

-   <span data-ttu-id="aa223-131">[Partager votre code avec Git et Visual Studio](https://www.visualstudio.com/docs/git/share-your-code-in-git-vs) ou</span><span class="sxs-lookup"><span data-stu-id="aa223-131">[Share your code with Git and Visual Studio](https://www.visualstudio.com/docs/git/share-your-code-in-git-vs) or</span></span>

-   [<span data-ttu-id="aa223-132">Partager votre code avec TFVC et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aa223-132">Share your code with TFVC and Visual Studio</span></span>](https://www.visualstudio.com/docs/tfvc/share-your-code-in-tfvc-vs)

<span data-ttu-id="aa223-133">Créer un Service d’application Azure où vous allez déployer votre application.</span><span class="sxs-lookup"><span data-stu-id="aa223-133">Create an Azure App Service where you'll deploy your application.</span></span> <span data-ttu-id="aa223-134">Créer une application Web en accédant au panneau des Services d’application sur le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="aa223-134">Create a Web App by going to the App Services blade on the Azure portal.</span></span> <span data-ttu-id="aa223-135">Cliquez sur + Ajouter, sélectionnez le modèle d’application Web, cliquez sur Créer et fournir un nom et autres détails.</span><span class="sxs-lookup"><span data-stu-id="aa223-135">Click +Add, select the Web App template, click Create, and provide a name and other details.</span></span> <span data-ttu-id="aa223-136">L’application web est accessible à partir de {nom}. azurewebsites.net.</span><span class="sxs-lookup"><span data-stu-id="aa223-136">The web app will be accessible from {name}.azurewebsites.net.</span></span>

![AzureWebApp](./media/image10-2.png)

<span data-ttu-id="aa223-138">**Figure 10-2.**</span><span class="sxs-lookup"><span data-stu-id="aa223-138">**Figure 10-2.**</span></span> <span data-ttu-id="aa223-139">Création d’une application Azure App Service Web dans le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="aa223-139">Creating a new Azure App Service Web App in the Azure Portal.</span></span>

<span data-ttu-id="aa223-140">Votre processus de génération de l’élément de configuration effectue une génération automatique chaque fois que le nouveau code est validé dans le référentiel de contrôle de code source du projet.</span><span class="sxs-lookup"><span data-stu-id="aa223-140">Your CI build process will perform an automated build whenever new code is committed to the project's source control repository.</span></span> <span data-ttu-id="aa223-141">Cela vous donne des informations immédiates que le code est généré (et, dans l’idéal, réussit les tests automatisés) et peuvent potentiellement être déployés.</span><span class="sxs-lookup"><span data-stu-id="aa223-141">This gives you immediate feedback that the code builds (and, ideally, passes automated tests) and can potentially be deployed.</span></span> <span data-ttu-id="aa223-142">Cette version de l’élément de configuration génère un site web artefact de package de déploiement et le publier pour la consommation par votre processus de CD.</span><span class="sxs-lookup"><span data-stu-id="aa223-142">This CI build will produce a web deploy package artifact and publish it for consumption by your CD process.</span></span>

[<span data-ttu-id="aa223-143">Définir votre processus de génération de l’élément de configuration</span><span class="sxs-lookup"><span data-stu-id="aa223-143">Define your CI build process</span></span>](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#ci)

<span data-ttu-id="aa223-144">Veillez à activer l’intégration continue pour le système sera en file d’attente une build chaque fois qu’une personne de votre équipe valide le nouveau code.</span><span class="sxs-lookup"><span data-stu-id="aa223-144">Be sure to enable continuous integration so the system will queue a build whenever someone on your team commits new code.</span></span> <span data-ttu-id="aa223-145">La génération de test et vérifier qu’il produit un site web déployer le package comme l’un de ses artefacts.</span><span class="sxs-lookup"><span data-stu-id="aa223-145">Test the build and verify that it is producing a web deploy package as one of its artifacts.</span></span>

<span data-ttu-id="aa223-146">Lorsqu’une build terminée, votre processus de CD déploie les résultats de la génération de l’élément de configuration à votre application web Azure.</span><span class="sxs-lookup"><span data-stu-id="aa223-146">When a build succeeds, your CD process will deploy the results of your CI build to your Azure web app.</span></span> <span data-ttu-id="aa223-147">Pour configurer cela, vous créez et configurez un *version*, laquelle sera déployez votre service d’application Azure.</span><span class="sxs-lookup"><span data-stu-id="aa223-147">To configure this, you create and configure a *Release*, which will deploy to your Azure App Service.</span></span>

[<span data-ttu-id="aa223-148">Définir votre processus de mise en production du CD</span><span class="sxs-lookup"><span data-stu-id="aa223-148">Define your CD release process</span></span>](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#cd)

<span data-ttu-id="aa223-149">Une fois votre pipeline de l’élément de configuration/CD est configuré, vous pouvez simplement mettre à jour votre application web et les valider sur le contrôle de code source pour les déployer.</span><span class="sxs-lookup"><span data-stu-id="aa223-149">Once your CI/CD pipeline is configured, you can simply make updates to your web app and commit them to source control to have them deployed.</span></span>

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a><span data-ttu-id="aa223-150">Flux de travail pour développer des applications hébergés par Azure ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aa223-150">Workflow for developing Azure-hosted ASP.NET Core applications</span></span>

<span data-ttu-id="aa223-151">Une fois que vous avez configuré votre compte Azure et votre processus de l’élément de configuration/CD, le développement d’applications de Azure hébergé ASP.NET Core est simple.</span><span class="sxs-lookup"><span data-stu-id="aa223-151">Once you have configured your Azure account and your CI/CD process, developing Azure-hosted ASP.NET Core applications is simple.</span></span> <span data-ttu-id="aa223-152">Voici les étapes de base généralement lors de la création d’une application ASP.NET Core, hébergée dans Azure App Service comme une application Web, comme illustré dans la Figure 10-3.</span><span class="sxs-lookup"><span data-stu-id="aa223-152">The following are the basic steps you usually take when building an ASP.NET Core app, hosted in Azure App Service as a Web App, as illustrated in Figure 10-3.</span></span>

![EndToEndDevDeployWorkflow](./media/image10-3.png)

<span data-ttu-id="aa223-154">**Figure 10-3.**</span><span class="sxs-lookup"><span data-stu-id="aa223-154">**Figure 10-3.**</span></span> <span data-ttu-id="aa223-155">Flux de travail pas à pas pour la création d’applications ASP.NET Core et leur hébergement dans Azure</span><span class="sxs-lookup"><span data-stu-id="aa223-155">Step-by-step workflow for building ASP.NET Core apps and hosting them in Azure</span></span>

#### <a name="step-1-local-dev-environment-inner-loop"></a><span data-ttu-id="aa223-156">Étape 1.</span><span class="sxs-lookup"><span data-stu-id="aa223-156">Step 1.</span></span> <span data-ttu-id="aa223-157">Boucle interne des environnement de développement local</span><span class="sxs-lookup"><span data-stu-id="aa223-157">Local Dev Environment Inner Loop</span></span>

<span data-ttu-id="aa223-158">Développement de votre application ASP.NET Core pour le déploiement vers Azure n’est pas différente de développement de votre application dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="aa223-158">Developing your ASP.NET Core application for deployment to Azure is no different from developing your application otherwise.</span></span> <span data-ttu-id="aa223-159">Utiliser l’environnement de développement local que vous êtes à l’aise avec, que ce soit Visual Studio 2017 ou l’interface CLI dotnet et Code de Visual Studio ou votre éditeur favori.</span><span class="sxs-lookup"><span data-stu-id="aa223-159">Use the local development environment you're comfortable with, whether that's Visual Studio 2017 or the dotnet CLI and Visual Studio Code or your preferred editor.</span></span> <span data-ttu-id="aa223-160">Vous pouvez écrire du code, exécuter et déboguer vos modifications, exécuter des tests automatisés et rendre les validations locales pour le contrôle de code source jusqu'à ce que vous êtes prêt à transmettre vos modifications à votre référentiel de contrôle de source partagée.</span><span class="sxs-lookup"><span data-stu-id="aa223-160">You can write code, run and debug your changes, run automated tests, and make local commits to source control until you're ready to push your changes to your shared source control repository.</span></span>

#### <a name="step-2-application-code-repository"></a><span data-ttu-id="aa223-161">Étape 2.</span><span class="sxs-lookup"><span data-stu-id="aa223-161">Step 2.</span></span> <span data-ttu-id="aa223-162">Référentiel de Code d’application</span><span class="sxs-lookup"><span data-stu-id="aa223-162">Application Code Repository</span></span>

<span data-ttu-id="aa223-163">Chaque fois que vous êtes prêt à partager votre code avec votre équipe, vous devez orienter vos modifications à partir de votre référentiel local source vers le référentiel de partage de code source de votre équipe.</span><span class="sxs-lookup"><span data-stu-id="aa223-163">Whenever you're ready to share your code with your team, you should push your changes from your local source repository to your team's shared source repository.</span></span> <span data-ttu-id="aa223-164">Si vous avez déjà utilisé dans une branche personnalisée, cette étape implique généralement la fusion de votre code partagé à une branche (par exemple au moyen d’un [requête de tirage](https://www.visualstudio.com/docs/git/pull-requests)).</span><span class="sxs-lookup"><span data-stu-id="aa223-164">If you've been working in a custom branch, this step usually involves merging your code into a shared branch (perhaps by means of a [pull request](https://www.visualstudio.com/docs/git/pull-requests)).</span></span>

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a><span data-ttu-id="aa223-165">Étape 3.</span><span class="sxs-lookup"><span data-stu-id="aa223-165">Step 3.</span></span> <span data-ttu-id="aa223-166">Serveur de builds : L’intégration continue.</span><span class="sxs-lookup"><span data-stu-id="aa223-166">Build Server: Continuous Integration.</span></span> <span data-ttu-id="aa223-167">Package de build, de Test,</span><span class="sxs-lookup"><span data-stu-id="aa223-167">Build, Test, Package</span></span>

<span data-ttu-id="aa223-168">Une nouvelle build est déclenchée sur le serveur de builds chaque fois qu’une nouvelle validation est effectuée dans le référentiel de code d’application partagée.</span><span class="sxs-lookup"><span data-stu-id="aa223-168">A new build is triggered on the build server whenever a new commit is made to the shared application code repository.</span></span> <span data-ttu-id="aa223-169">Dans le cadre du processus de l’élément de configuration, cette build doit entièrement compiler l’application et exécuter des tests automatisés pour vérifier que tout fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="aa223-169">As part of the CI process, this build should fully compile the application and run automated tests to confirm everything is working as expected.</span></span> <span data-ttu-id="aa223-170">Le résultat final du processus de l’élément de configuration doit être une version de package de l’application web, prête pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="aa223-170">The end result of the CI process should be a packaged version of the web app, ready for deployment.</span></span>

#### <a name="step-4-build-server-continuous-delivery"></a><span data-ttu-id="aa223-171">Étape 4.</span><span class="sxs-lookup"><span data-stu-id="aa223-171">Step 4.</span></span> <span data-ttu-id="aa223-172">Serveur de builds : Livraison continue</span><span class="sxs-lookup"><span data-stu-id="aa223-172">Build Server: Continuous Delivery</span></span>

<span data-ttu-id="aa223-173">Une fois une build comme a réussi, le processus de CD prennent en charge les artefacts de build générés.</span><span class="sxs-lookup"><span data-stu-id="aa223-173">Once a build as succeeded, the CD process will pick up the build artifacts produced.</span></span> <span data-ttu-id="aa223-174">Cela inclut un site web déployer le package.</span><span class="sxs-lookup"><span data-stu-id="aa223-174">This will include a web deploy package.</span></span> <span data-ttu-id="aa223-175">Le serveur de builds déployez ce package du Service d’applications Azure, en remplaçant tout service existant par celui qui vient d’être créé.</span><span class="sxs-lookup"><span data-stu-id="aa223-175">The build server will deploy this package to Azure App Service, replacing any existing service with the newly created one.</span></span> <span data-ttu-id="aa223-176">En général, cette étape vise un environnement intermédiaire, mais certaines applications déploiement directement à la production via un processus de CD.</span><span class="sxs-lookup"><span data-stu-id="aa223-176">Typically this step targets a staging environment, but some applications deploy directly to production through a CD process.</span></span>

#### <a name="step-5-azure-app-service-web-app"></a><span data-ttu-id="aa223-177">Étape 5.</span><span class="sxs-lookup"><span data-stu-id="aa223-177">Step 5.</span></span> <span data-ttu-id="aa223-178">Service d’applications Azure.</span><span class="sxs-lookup"><span data-stu-id="aa223-178">Azure App Service.</span></span> <span data-ttu-id="aa223-179">Application Web.</span><span class="sxs-lookup"><span data-stu-id="aa223-179">Web App.</span></span>

<span data-ttu-id="aa223-180">Une fois déployé, l’application ASP.NET Core s’exécute dans le contexte d’une application Azure App Service Web.</span><span class="sxs-lookup"><span data-stu-id="aa223-180">Once deployed, the ASP.NET Core application runs within the context of an Azure App Service Web App.</span></span> <span data-ttu-id="aa223-181">Cette application Web peut être surveillée et davantage configurés à l’aide du portail Azure.</span><span class="sxs-lookup"><span data-stu-id="aa223-181">This Web App can be monitored and further configured using the Azure Portal.</span></span>

#### <a name="step-6-production-monitoring-and-diagnostics"></a><span data-ttu-id="aa223-182">Étape 6.</span><span class="sxs-lookup"><span data-stu-id="aa223-182">Step 6.</span></span> <span data-ttu-id="aa223-183">Surveillance de la production et de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="aa223-183">Production Monitoring and Diagnostics</span></span>

<span data-ttu-id="aa223-184">Pendant l’exécution de l’application Web, vous pouvez surveiller l’intégrité de l’application et collecter des données de comportement d’utilisateur et de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="aa223-184">While the Web App is running, you can monitor the health of the application and collect diagnostics and user behavior data.</span></span> <span data-ttu-id="aa223-185">Application Insights est inclus dans Visual Studio et offre une instrumentation automatique pour les applications ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="aa223-185">Application Insights is included in Visual Studio, and offers automatic instrumentation for ASP.NET apps.</span></span> <span data-ttu-id="aa223-186">Il peut vous fournir plus d’informations sur l’utilisation, des exceptions, les demandes, performances et des journaux.</span><span class="sxs-lookup"><span data-stu-id="aa223-186">It can provide you with information on usage, exceptions, requests, performance, and logs.</span></span>

## <a name="references"></a><span data-ttu-id="aa223-187">Références</span><span class="sxs-lookup"><span data-stu-id="aa223-187">References</span></span>

<span data-ttu-id="aa223-188">**Générer et déployer votre application ASP.NET Core vers Azure**</span><span class="sxs-lookup"><span data-stu-id="aa223-188">**Build and Deploy Your ASP.NET Core App to Azure**</span></span>  
<span data-ttu-id="aa223-189"><https://www.VisualStudio.com/docs/build/Apps/ASPNET/aspnetcore-to-Azure></span><span class="sxs-lookup"><span data-stu-id="aa223-189"><https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="aa223-190">[Précédente] (test-asp-net-core-mvc-apps.md) [suivant] (azure-hosting-recommendations-for-asp-net-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="aa223-190">[Previous] (test-asp-net-core-mvc-apps.md) [Next] (azure-hosting-recommendations-for-asp-net-web-apps.md)</span></span>