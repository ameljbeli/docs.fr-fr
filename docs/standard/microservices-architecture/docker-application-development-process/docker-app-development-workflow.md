---
title: Workflow de développement des applications Docker
description: Découvrez les détails du workflow de développement des applications Docker. Commencez étape par étape et entrez dans les détails pour optimiser les fichiers Dockerfile, puis terminez par le workflow simplifié disponible avec Visual Studio.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/27/2018
ms.openlocfilehash: 52053f270067ba0cc3ab8535560ec8145eda0758
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084977"
---
# <a name="development-workflow-for-docker-apps"></a>Workflow de développement des applications Docker

Le cycle de vie de développement d’une application débute sur votre ordinateur, si vous êtes développeur, là où vous codez l’application dans le langage de votre choix et que vous la testez localement. Avec ce workflow, quels que soient le langage, le framework et la plateforme que vous choisissez, vous développez et testez toujours des conteneurs Docker, mais vous le faites localement.

Chaque conteneur (instance d’une image Docker) inclut les éléments suivants :

- Un système d’exploitation sélectionné, par exemple, une distribution Linux, Windows Nano Server ou Windows Server Core.

- Des fichiers ajoutés pendant le développement, par exemple, du code source et des fichiers binaires d’application.

- Des informations de configuration, comme les paramètres d’environnement et les dépendances.

## <a name="workflow-for-developing-docker-container-based-applications"></a>Workflow pour développer des applications basées sur des conteneurs Docker

Cette section décrit le workflow de développement de la *boucle interne* pour les applications basées sur des conteneurs Docker. Dans ce workflow de boucle interne, le workflow DevOps (y compris le déploiement en production) plus global n’est pas pris en compte et seules les étapes de développement effectuées sur l’ordinateur du développeur sont traitées. Les étapes initiales de configuration de l’environnement ne sont pas comprises non plus, car elles sont effectuées une seule fois.

Une application est composée de vos propres services et de bibliothèques supplémentaires (dépendances). La figure 5-1 illustre les principales étapes qu’un développeur doit généralement effectuer pour créer une application Docker.

![Processus de développement des applications Docker : 1 - Coder votre application, 2 - Écrire un ou plusieurs fichiers Dockerfile, 3 - Créer des images définies dans les fichiers Dockerfile, 4 - (facultatif) Composer des services dans le fichier docker-compose.yml, 5 - Exécuter le conteneur ou l’application docker-compose, 6 - Tester votre application ou vos microservices, 7 - Pousser vers le dépôt et répéter. ](./media/image1.png)

**Figure 5-1.** Workflow pas à pas pour développer des applications Docker en conteneur

Cette section décrit tout ce processus en détail, en expliquant chacune des grandes étapes dans le contexte d’un environnement Visual Studio.

Si vous optez pour une approche de développement avec un éditeur ou une interface CLI (par exemple, Visual Studio Code plus l’interface CLI Docker sur macOS ou Windows), vous devez connaître toutes les étapes de manière plus détaillée que pour Visual Studio. Pour plus d’informations sur le développement dans un environnement CLI, consultez le livre électronique [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).

Si vous utilisez Visual Studio 2017, un grand nombre de ces étapes sont gérées pour vous, ce qui améliore considérablement votre productivité. C’est encore plus vrai si vous utilisez Visual Studio 2017 et ciblez des applications multiconteneurs. Par exemple, avec un seul clic de souris, Visual Studio ajoute les fichiers Dockerfile et docker-compose.yml à vos projets, avec la configuration de votre application. Quand vous exécutez l’application dans Visual Studio, le programme crée l’image Docker et exécute l’application multiconteneur directement dans Docker. Il vous permet même de déboguer plusieurs conteneurs à la fois. Grâce à ces fonctionnalités, vous allez développer nettement plus vite.

Toutefois, même si Visual Studio effectue ces étapes automatiquement, vous devez comprendre comment intervient Docker dans chacune d’elles. Par conséquent, le guide suivant décrit en détail chaque étape.

![1- Coder votre application](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Étape 1. Commencer le codage et créer votre base de référence initiale pour l’application ou le service

Le développement d’une application se déroule de façon similaire avec ou sans Docker. La différence est que, quand vous développez avec Docker, vous déployez et testez l’application ou les services exécutés dans des conteneurs Docker dans votre environnement local (une machine virtuelle Linux configurée par Docker ou directement Windows si vous utilisez des conteneurs Windows).

### <a name="set-up-your-local-environment-with-visual-studio"></a>Configurer votre environnement local avec Visual Studio

Pour commencer, assurez-vous que [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) pour Windows est installé, comme cela est expliqué dans les instructions suivantes :

[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/)

Vous avez également besoin de Visual Studio 2017 version 15.7 ou ultérieure, avec la charge de travail **Développement multiplateforme .NET Core** installée (voir la figure 5-2).

![Sélection de la charge de travail Développement multiplateforme .NET Core pendant l’installation de Visual Studio.](./media/image3.png)

**Figure 5-2**. Sélection de la charge de travail **Développement multiplateforme .NET Core** pendant l’installation de Visual Studio 2017

Vous pouvez commencer le codage de votre application en .NET brut (généralement dans .NET Core si vous envisagez d’utiliser des conteneurs) même si vous n’avez pas encore activé Docker dans votre application, ni effectué de déploiement et de test dans Docker. Toutefois, nous vous recommandons de commencer à travailler dans Docker le plus tôt possible, car Docker sera le véritable environnement de développement, et vous pourrez détecter les problèmes éventuels dès le début. Nous le conseillons d’autant plus que Visual Studio rend l’utilisation de Docker extrêmement simple et intuitive. L’exemple le plus significatif est le débogage des applications multiconteneurs à partir de Visual Studio.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Bien démarrer avec Docker CE pour Windows** \
  [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

- **Visual Studio 2017** \
  [*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![2 - Écrire des fichiers Dockerfile](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Étape 2. Créer un fichier Dockerfile associé à une image de base .NET existante

Vous avez besoin d’un fichier Dockerfile pour chaque image personnalisée que vous souhaitez créer. Vous avez également besoin d’un fichier Dockerfile pour chaque conteneur à déployer, que vous choisissiez de le déployer automatiquement à partir de Visual Studio ou manuellement à l’aide de la CLI Docker (commandes docker run et docker-compose). Si votre application contient un seul service personnalisé, créez un seul fichier Dockerfile. Si votre application contient plusieurs services (comme dans une architecture de microservices), vous devez créer un fichier Dockerfile pour chaque service.

Le fichier Dockerfile est créé dans le dossier racine de votre application ou service. Il contient les commandes qui indiquent à Docker comment configurer et exécuter votre application ou service dans un conteneur. Vous pouvez créer manuellement un fichier Dockerfile dans le code et l’ajouter à votre projet, avec vos dépendances .NET.

Avec Visual Studio et ses outils pour Docker, cette tâche se fait en quelques clics de souris seulement. Quand vous créez un projet dans Visual Studio 2017, vous avez une option nommée **Activer la prise en charge des conteneurs (Docker)** (voir la figure 5-3).

![Case à cocher d’activation de la prise en charge de Docker pendant la création d’un projet ASP.NET Core dans Visual Studio 2017](./media/image5.png)

**Figure 5-3**. Activation de la prise en charge de Docker pendant la création d’un projet ASP.NET Core dans Visual Studio 2017

Vous pouvez aussi activer la prise en charge de Docker dans un projet d’application web ASP.NET Core existant en cliquant avec le bouton droit sur le projet dans l’**Explorateur de solutions** et en sélectionnant **Ajouter** > **Prise en charge de Docker** (voir la figure 5-4).

![Option de menu Ajouter la prise en charge de Docker dans Visual Studio](./media/image6.png)

**Figure 5-4**. Activation de la prise en charge de Docker dans un projet Visual Studio 2017 existant

Cette action ajoute un fichier *Dockerfile* au projet avec la configuration nécessaire. Elle est disponible uniquement dans les projets d’application web ASP.NET Core.

De la même manière, Visual Studio peut également ajouter un fichier docker-compose.yml pour l’ensemble de la solution avec l’option **Ajouter > Prise en charge de l’orchestrateur de conteneurs**. À l’étape 4, nous explorons cette option plus en détail.

### <a name="using-an-existing-official-net-docker-image"></a>Utilisation d’une image Docker .NET officielle existante

Le plus souvent, vous créez une image personnalisée pour votre conteneur à partir d’une image de base que vous obtenez dans un dépôt officiel comme le registre [Docker Hub](https://hub.docker.com/). C’est précisément ce qui se passe en arrière-plan quand vous activez la prise en charge de Docker dans Visual Studio. Votre fichier Dockerfile utilise une image `aspnetcore` existante.

Précédemment, nous avons expliqué quels images et dépôts Docker vous pouvez utiliser selon le framework et le système d’exploitation que vous avez choisis. Par exemple, si vous souhaitez utiliser ASP.NET Core (Windows ou Linux), l’image à utiliser est `microsoft/dotnet:2.1-aspnetcore-runtime`. La seule chose à faire est donc de spécifier l’image Docker de base à utiliser pour votre conteneur. Pour ce faire, ajoutez `FROM microsoft/dotnet:2.1-aspnetcore-runtime` à votre fichier Dockerfile. Cette opération est effectuée automatiquement par Visual Studio, mais si vous avez à mettre à jour la version, vous devez modifier cette valeur.

L’utilisation d’un dépôt d’images .NET officiel fourni dans le Docker Hub avec un numéro de version garantit que les mêmes fonctionnalités de langage sont disponibles sur toutes les machines (y compris celles de développement, test et production).

L’extrait de code suivant est un exemple de fichier Dockerfile pour un conteneur ASP.NET Core.

```Dockerfile
FROM microsoft/aspnetcore:2.0
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

Dans ce cas, l’image est basée sur la version 2.1 de l’image Docker ASP.NET Core officielle (multi-architecture pour Linux et Windows). Il s’agit du paramètre `FROM microsoft/dotnet:2.1-aspnetcore-runtime`. (Pour plus d’informations sur cette image de base, consultez la page [Image Docker ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) et la page [Image Docker .NET Core](https://hub.docker.com/r/microsoft/dotnet/).) Dans le fichier Dockerfile, vous devez également indiquer à Docker d’écouter le port TCP qui sera utilisé au moment de l’exécution (dans cet exemple, le port 80 est configuré avec le paramètre EXPOSE).

Vous pouvez spécifier des paramètres de configuration supplémentaires dans le fichier Dockerfile, en fonction du langage et du framework que vous utilisez. Par exemple, la ligne ENTRYPOINT avec `["dotnet", "MySingleContainerWebApp.dll"]` indique à Docker d’exécuter une application .NET Core. Si vous utilisez le SDK et l’interface CLI (dotnet) de .NET Core pour créer et exécuter l’application .NET, ce paramètre est différent. L’essentiel à retenir est que la ligne ENTRYPOINT et certains autres paramètres varient selon le langage et la plateforme choisis pour votre application.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Création d’images Docker pour les applications .NET Core** \
  [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

- **Créer votre propre image**. Dans la documentation officielle de Docker.\
  [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

- **Rester à jour avec les Images de conteneur .NET** \
  [*https://blogs.msdn.microsoft.com/dotnet/2018/06/18/staying-up-to-date-with-net-container-images/*](https://blogs.msdn.microsoft.com/dotnet/2018/06/18/staying-up-to-date-with-net-container-images/)

- **Utilisation conjointe de .NET et Docker - DockerCon 2018 Update** \
  [*https://blogs.msdn.microsoft.com/dotnet/2018/06/13/using-net-and-docker-together-dockercon-2018-update/*](https://blogs.msdn.microsoft.com/dotnet/2018/06/13/using-net-and-docker-together-dockercon-2018-update/)

### <a name="using-multi-arch-image-repositories"></a>Utilisation de dépôts d’images multi-arch

Un dépôt peut contenir des variantes de plateforme, comme une image Linux et une image Windows. Cette fonctionnalité permet aux fournisseurs comme Microsoft (créateurs d’images de base) de créer un dépôt commun pour plusieurs plateformes (Linux et Windows). Par exemple, le dépôt [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) disponible dans le registre Docker Hub fournit la prise en charge de Linux et Windows Nano Server en utilisant le même nom de dépôt.

Si vous spécifiez une balise, le ciblage d’une plateforme est explicite, comme dans les cas suivants :

- `microsoft/dotnet:2.1-aspnetcore-runtime-stretch-slim` \
  Cibles : Runtime uniquement .NET Core 2.1 sur Linux

- `microsoft/dotnet:2.1-aspnetcore-runtime-nanoserver-1709` \
  Cibles : Runtime uniquement .NET Core 2.1 sur Windows Nano Server

Toutefois, si vous spécifiez le même nom d’image avec la même balise, les images multi-architectures (comme l’image `aspnetcore`) utilisent la version Windows ou Linux selon le système d’exploitation hôte de Docker que vous déployez, comme indiqué dans l’exemple suivant :

- `microsoft/dotnet:2.1-aspnetcore-runtime` \
  Multi-architecture : runtime uniquement .NET Core 2.1 sur Linux ou Windows Nano Server en fonction du système d’exploitation hôte de Docker

Ainsi, quand vous tirez (pull) une image d’un hôte Windows, la variante Windows est tirée et quand vous tirez le même nom d’image d’un hôte Linux, la variante Linux est tirée.

### <a name="multi-stage-builds-in-dockerfile"></a>Builds multi-étapes dans le fichier Dockerfile

Le fichier Dockerfile est similaire à un script de commandes par lot. C’est la même chose que configurer un ordinateur à partir de la ligne de commande.

Il commence par une image de base qui définit le contexte initial, comme le système de fichiers de départ, qui repose sur le système d’exploitation hôte. Ce n’est pas un système d’exploitation, mais vous pouvez le considérer comme « le » système d’exploitation à l’intérieur du conteneur.

L’exécution de chaque ligne de commande crée une couche sur le système de fichiers avec les changements de la couche précédente, et c’est la combinaison de ces couches qui produit le système de fichiers.

Comme chaque nouvelle couche « repose » sur la précédente et que la taille de l’image obtenue augmente avec chaque commande, les images peuvent devenir très grandes, surtout si elles doivent comprendre, par exemple, le SDK nécessaire à la génération et la publication d’une application.

D’où l’intérêt des builds multi-étapes (à partir de Docker 17.05 et versions ultérieures).

L’idée fondamentale est que vous pouvez diviser le processus d’exécution des fichiers Dockerfile en étapes, où une étape est une image initiale suivie d’une ou plusieurs commandes et la dernière étape détermine la taille finale de l’image.

En bref, les builds multi-étapes permettent de diviser la création en différentes « étapes » et d’assembler l’image finale en prenant uniquement les répertoires appropriés des étapes intermédiaires. La stratégie générale pour utiliser cette fonctionnalité est :

1. Utiliser une image SDK de base (peu importe la taille), avec tous les éléments nécessaires pour générer et publier l’application dans un dossier, puis

2. Utiliser une image de base, petite et pour le runtime uniquement, et copier le dossier de publication de l’étape précédente pour produire une petite image finale.

Vraisemblablement, la meilleure façon de comprendre le concept du multi-étape est d’étudier en détail un fichier Dockerfile, ligne par ligne. Commençons donc avec le fichier Dockerfile initial créé par Visual Studio pendant l’ajout de la prise en charge de Docker à un projet, nous verrons les optimisations plus tard.

Le fichier Dockerfile initial peut ressembler à ceci :

```Dockerfile
 1  FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM microsoft/dotnet:2.1-sdk AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks … 
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -0 /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

Voici les détails, ligne par ligne :

1.  Commencez une étape avec une « petite » image de base runtime uniquement, appelez-la **base** pour référence.
2.  Créez le répertoire **/app** dans l’image.
3.  Exposez le port **80**.
<!-- skip -->
5.  Commencez une nouvelle étape avec une « grande » image pour la génération/publication, appelez-la **build** pour référence.
6.  Créez le répertoire **/src** dans l’image.
7.  Jusqu’à la ligne 16, copiez les fichiers projet référencés **.csproj** pour pouvoir restaurer les packages par la suite.
<!-- skip -->
17. Restaurez les packages pour le projet **Catalog.API** et les projets référencés.
18. Copiez **toute l’arborescence de répertoires de la solution** (sauf les fichiers/répertoires inclus dans le fichier **.dockerignore**) à partir du répertoire **/src** dans l’image.
19. Remplacez le dossier actuel par le projet **Catalog.API**.
20. Générez le projet (et les autres dépendances du projet) et placez-la sortie dans le répertoire **/app** de l’image.
<!-- skip -->
22. Commencez une nouvelle étape à partir de la build, appelez-la **publish** pour référence.
23. Publiez le projet (et les dépendances) et placez la sortie dans le répertoire **/app** de l’image.
<!-- skip -->
25. Commencez une nouvelle étape à partir de **base** et appelez-la **final**
26. Remplacez le répertoire actuel par **/app**
27. Copiez le répertoire **/app** à partir de l’étape **publish** dans le répertoire actuel
28. Définissez la commande à exécuter au démarrage du conteneur.

Voyons maintenant les optimisations possibles pour améliorer les performances de l’ensemble du processus qui, dans le cas d’eShopOnContainers, signifie 22 minutes ou plus pour générer la solution complète dans des conteneurs Linux.

Vous allez tirer parti de la fonctionnalité de cache de couches de Docker, qui est assez simple : si l’image de base et les commandes sont les mêmes que certaines exécutées précédemment, vous pouvez gagner du temps en utilisant simplement la couche qui en résulte sans avoir à exécuter les commandes.

Par conséquent, prenons l’étape **build**, les lignes 5 et 6 sont quasiment les mêmes, mais les lignes 7 à 17 sont différentes pour chaque service d’eShopOnContainers, et doivent donc être exécutées à chaque fois, mais si vous remplacez les lignes 7 à 16 par :

```
COPY . .
```

Elles sont alors identiques pour chaque service, la solution entière est copiée, ce qui produit une couche plus grande, mais :

1) Le processus de copie est seulement exécuté la première fois (et pendant la regénération si un fichier est changé) et utilise le cache pour tous les autres services, et

2) Comme l’image plus grande est produite dans une étape intermédiaire, cela n’affecte pas la taille de l’image finale.

L’optimisation importante suivante implique la commande `restore` exécutée à la ligne 17, qui est également différente pour chaque service d’eShopOnContainers. Si vous remplacez cette ligne simplement par :

```console
RUN dotnet restore
```

Les packages sont restaurés pour l’ensemble de la solution, mais une fois encore, ils sont restaurés une seule fois au lieu de 15 fois avec la stratégie actuelle.

Toutefois, `dotnet restore` s’exécute uniquement si le dossier contient un seul fichier projet ou solution. Les choses se compliquent donc un peu et vous pouvez résoudre le problème, sans rentrer dans les détails, de la façon suivante :

1) Ajoutez les lignes suivantes à **.dockerignore**  :

   - `*.sln`, pour ignorer tous les fichiers solution dans l’arborescence de dossiers principale

   - `!eShopOnContainers-ServicesAndWebApps.sln`, pour inclure uniquement ce fichier solution.

2) Ajoutez l’argument `/ignoreprojectextensions:.dcproj` à `dotnet restore`, pour que le processus ignore également le projet docker-compose et restaure uniquement les packages de la solution eShopOnContainers-ServicesAndWebApps.

Voyons maintenant l’optimisation finale : la ligne 20 est redondante et, comme la ligne 23 génère aussi l’application et suit, logiquement, la ligne 20, la commande prend beaucoup de temps.

Le fichier résultant est alors :

```Dockerfile
 1  FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM microsoft/dotnet:2.1-sdk AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a>Création de votre image de base à partir de zéro

Vous pouvez créer votre propre image de base Docker à partir de zéro. Ce scénario n’est pas recommandé si vous n’êtes pas encore familiarisé avec Docker, mais si vous souhaitez définir les bits spécifiques de votre propre image de base, vous pouvez le faire.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Images .NET Core multi-architectures**.\
  [*https://github.com/dotnet/announcements/issues/14*](https://github.com/dotnet/announcements/issues/14)

- **Créer une image de base**. Documentation officielle de Docker.\
  [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![3 - Créer des images définies dans des fichiers Dockerfile](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Étape 3. Créer vos images Docker personnalisées et incorporer votre application ou service dans ces images

Pour chaque service inclus dans votre application, vous devez créer une image associée. Si votre application est composée uniquement d’un service ou d’une application web, vous avez besoin d’une seule image.

Sachez que les images Docker sont créées automatiquement dans Visual Studio. Les étapes suivantes s’appliquent uniquement dans le cadre du workflow avec un éditeur ou une CLI. Elles sont expliquées pour vous permettre de bien en comprendre tous les dessous.

En tant que développeur, vous avez besoin d’écrire du code et de le tester localement avant de pousser (push) une fonctionnalité ou un changement terminé à votre système de contrôle de code source (par exemple, à GitHub). Cela signifie que vous devez créer les images Docker et déployer des conteneurs sur un hôte Docker local (machine virtuelle Windows ou Linux), et exécuter, tester et déboguer dans ces conteneurs locaux.

Pour créer une image personnalisée dans votre environnement local avec la CLI Docker et votre fichier Dockerfile, vous pouvez utiliser la commande docker build, comme indiqué dans la figure 5-5.

![Écran de progression pour la création d’une image Docker](./media/image8.png)

**Figure 5-5**. Création d’une image Docker personnalisée

Si vous le souhaitez, au lieu d’exécuter la commande docker build directement à partir du dossier de projet, vous pouvez d’abord générer un dossier déployable avec les fichiers binaires et les bibliothèques .NET nécessaires en exécutant `dotnet publish` puis en utilisant la commande `docker build`.

Cette action crée une image Docker appelée `cesardl/netcore-webapi-microservice-docker:first`. Dans ce cas, :first est une balise qui représente une version spécifique. Vous pouvez répéter cette étape pour chaque image personnalisée à créer pour votre application Docker composée.

Quand une application est constituée de plusieurs conteneurs (une application multiconteneur), vous pouvez également utiliser la commande `docker-compose up --build` pour créer toutes les images associées avec une seule commande à l’aide des métadonnées exposées dans les fichiers docker-compose.yml associés.

Vous pouvez rechercher les images existantes dans votre dépôt local avec la commande docker images (voir la figure 5-6).

![Vue de l’écran de la liste d’images à partir de la commande docker images](./media/image9.png)

**Figure 5-6.** Affichage des images existantes à l’aide de la commande docker images

### <a name="creating-docker-images-with-visual-studio"></a>Création d’images Docker avec Visual Studio

Quand vous utilisez Visual Studio pour créer un projet avec la prise en charge de Docker, vous ne créez pas une image explicitement. En fait, l’image est créée quand vous appuyez sur **F5** (ou **Ctrl-F5**) pour exécuter l’application ou le service dockerisé. Cette étape est automatique dans Visual Studio. Vous ne la verrez donc pas à l’écran, mais il est important d’en comprendre le mécanisme.

![4 - (facultatif) Composer des services dans le fichier docker-compose.yml](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Étape 4. Définir vos services dans docker-compose.yml lors de la création d’une application Docker multiconteneur

Le fichier [docker-compose.yml](https://docs.docker.com/compose/compose-file/) vous permet de définir un ensemble de services à déployer ensemble comme application composée avec les commandes de déploiement. Il configure également ses relations de dépendance et la configuration d’exécution.

Pour utiliser un fichier docker-compose.yml, vous devez d’abord le créer dans votre dossier solution principal ou racine. Le contenu du fichier doit être semblable à l’exemple suivant :

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

Ce fichier docker-compose.yml est une version simplifiée et fusionnée. Il contient des données de configuration statiques pour chaque conteneur (comme le nom de l’image personnalisée), qui sont toujours nécessaires, ainsi que des informations de configuration variables selon l’environnement de déploiement, comme la chaîne de connexion. Dans des sections ultérieures, vous découvrez comment fractionner la configuration du fichier docker-compose.yml en plusieurs fichiers docker-compose et remplacer les valeurs en fonction de l’environnement et du type d’exécution (debug ou release).

L’exemple de fichier docker-compose.yml définit quatre services : le service `webmvc` (une application web), deux microservices (`ordering.api` et `basket.api`), et un conteneur de source de données (`sql.data`), basé sur SQL Server pour Linux exécuté comme un conteneur. Comme chaque service est déployé comme un conteneur, ils ont chacun besoin d’une image Docker.

Le fichier docker-compose.yml spécifie les conteneurs utilisés, mais aussi la configuration de chaque conteneur. Par exemple, la définition du conteneur `webmvc` dans le fichier .yml :

- Utilise une image `eshop/web:latest` prédéfinie. Toutefois, vous pouvez également configurer l’image à créer à l’exécution de docker-compose avec une configuration supplémentaire basée sur une section :build dans le fichier docker-compose.

- Initialise deux variables d’environnement (CatalogUrl et OrderingUrl).

- Transfère le port exposé 80 sur le conteneur vers le port externe 80 sur la machine hôte.

- Lie l’application web aux services catalog et ordering avec le paramètre depends_on. Cela force le service à attendre le démarrage de ces services.

Nous reparlerons du fichier docker-compose.yml dans une section ultérieure, quand nous expliquerons comment implémenter des microservices et des applications multiconteneurs.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Utilisation de docker-compose.yml dans Visual Studio 2017

En plus d’ajouter un fichier Dockerfile à un projet, comme nous l’avons mentionné précédemment, Visual Studio 2017 (à partir de la version 15.8) peut ajouter à une solution la prise en charge d’un orchestrateur pour Docker Compose.

Quand vous ajoutez pour la première fois la prise en charge d’un orchestrateur de conteneurs, comme indiqué dans la Figure 5-7, Visual Studio crée le fichier Dockerfile pour le projet ainsi qu’un projet (section service) dans votre solution avec plusieurs fichiers `docker-compose*.yml` généraux, puis ajoute le projet à ces fichiers. Vous pouvez ensuite ouvrir les fichiers docker-compose.yml et les mettre à jour avec des fonctionnalités supplémentaires.

Vous devez répéter cette opération pour chaque projet que vous souhaitez inclure dans le fichier docker-compose.yml.

Au moment de la rédaction de cet article, Visual Studio prend en charge les orchestrateurs Docker Compose et Service Fabric.

![Option de menu contextuel pour ajouter la prise en charge de l’orchestrateur à un projet ASP.NET Core](./media/image21.png)

**Figure 5-7**. Ajout de la prise en charge de Docker dans Visual Studio 2017 en cliquant avec le bouton droit sur un projet ASP.NET Core

Après avoir ajouté la prise en charge des orchestrateurs à votre solution dans Visual Studio, vous voyez également un nouveau nœud (dans le fichier projet `docker-compose.dcproj`) dans l’Explorateur de solutions. Ce nœud contient les fichiers docker-compose.yml qui ont été ajoutés (voir la figure 5-8).

![Nœud docker-compose dans l’Explorateur de solutions](./media/image11.png)

**Figure 5-8**. Nœud d’arborescence **docker-compose** ajouté dans l’Explorateur de solutions de Visual Studio 2017

Vous pouvez déployer une application multiconteneur avec un seul fichier docker-compose.yml en utilisant la commande `docker-compose up`. Toutefois, Visual Studio ajoute un groupe de ces fichiers pour vous permettre de remplacer les valeurs selon l’environnement (développement ou production) et le type d’exécution (release ou debug). Cette fonctionnalité sera expliquée dans des sections ultérieures.

![5 - Exécuter des conteneurs ou une application composée](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Étape 5. Générer et exécuter votre application Docker

Si votre application n’a qu’un seul conteneur, vous pouvez l’exécuter en la déployant sur l’hôte Docker (machine virtuelle ou serveur physique). Si votre application contient plusieurs services, vous pouvez la déployer en tant qu’application composée, soit à l’aide d’une seule commande CLI (docker-compose up), soit avec Visual Studio, qui utilise cette commande en arrière-plan. Voyons les différentes options.

### <a name="option-a-running-a-single-container-application"></a>Option A : Exécution d’une application monoconteneur

#### <a name="using-docker-cli"></a>Utilisation de l’interface CLI Docker

Vous pouvez exécuter un conteneur Docker à l’aide de la commande `docker run`, comme indiqué dans la figure 5-9 :

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

La commande ci-dessus crée une instance de conteneur à partir de l’image spécifiée, chaque fois qu’elle est exécutée. Vous pouvez utiliser le paramètre `--name` pour donner un nom au conteneur, puis utiliser `docker start {name}` (ou l’ID de conteneur ou le nom automatique) pour exécuter une instance de conteneur existante.

![Vue de l’écran d’exécution d’un conteneur Docker à l’aide de la commande docker run](./media/image13.png)

**Figure 5-9**. Exécution d’un conteneur Docker à l’aide de la commande docker run

Dans ce cas, la commande lie le port interne 5000 du conteneur au port 80 de la machine hôte. Cela signifie que l’hôte écoute le port 80 et transfère le port sur le port 5000 sur le conteneur.

Le code de hachage indiqué est l’ID de conteneur, auquel est attribué un nom lisible aléatoire si l’option `--name` n’est pas utilisée.

#### <a name="using-visual-studio"></a>Utilisation de Visual Studio.

Si vous n’avez pas ajouté la prise en charge de l’orchestrateur de conteneurs, vous pouvez également exécuter une application monoconteneur dans Visual Studio en appuyant sur **Ctrl-F5** et vous pouvez aussi utiliser **F5** pour déboguer l’application dans le conteneur. Avec docker run, le conteneur s’exécute localement.

### <a name="option-b-running-a-multi-container-application"></a>Option B : Exécution d’une application multiconteneur

Dans la plupart des scénarios d’entreprise, une application Docker est composée de plusieurs services, ce qui signifie que vous devez exécuter une application multiconteneur, comme illustré à la figure 5-10.

![Machine virtuelle avec plusieurs conteneurs Docker](./media/image14.png)

**Figure 5-10**. Machine virtuelle avec des conteneurs Docker déployés

#### <a name="using-docker-cli"></a>Utilisation de l’interface CLI Docker

Pour exécuter une application multiconteneur avec l’interface CLI Docker, vous utilisez la commande `docker-compose up`. Cette commande utilise le fichier **docker-compose.yml** que vous avez au niveau de la solution pour déployer une application multiconteneur. La figure 5-11 montre les résultats de l’exécution de la commande à partir de votre répertoire de solution principal, qui contient le fichier docker-compose.yml.

![Vue de l’écran d’exécution de la commande docker-compose up](./media/image15.png)

**Figure 5-11**. Exemple de résultats de l’exécution de la commande docker-compose up

Après l’exécution de la commande docker-compose up, l’application et ses conteneurs associés sont déployés sur votre hôte Docker, comme indiqué dans la figure 5-10.

#### <a name="using-visual-studio"></a>Utilisation de Visual Studio.

L’exécution d’une application multiconteneur à l’aide de Visual Studio 2017 est extrêmement simple. Appuyez simplement sur **Ctrl-F5** pour exécuter ou **F5** pour déboguer, comme d’habitude, en configurant le projet **docker-compose** comme projet de démarrage.  Visual Studio gère tous les paramètres nécessaires, vous pouvez donc créer des points d’arrêt comme d’habitude et déboguer ce qui devient des processus indépendants s’exécutant dans des « serveurs à distance », tout simplement.

Comme nous l’avons mentionné plus haut, chaque fois que vous ajoutez la prise en charge de la solution Docker à un projet dans une solution, ce projet est configuré dans le fichier docker-compose.yml global (au niveau de la solution), ce qui vous permet d’exécuter ou de déboguer la solution dans son intégralité. Visual Studio démarre un conteneur pour chaque projet pour lequel la prise en charge de la solution Docker est activée, puis il effectue automatiquement toutes les étapes internes (dotnet publish, docker build, etc.).

Si vous voulez rentrer dans les détails, jetez un œil au fichier :

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

Le point important ici est que, comme indiqué dans la figure 5-12, Visual Studio 2017 fournit une commande **Docker** supplémentaire associée à l’action de la touche F5. Cette option vous permet d’exécuter ou de déboguer une application multiconteneur en exécutant tous les conteneurs qui sont définis dans les fichiers docker-compose.yml au niveau de la solution. Pour déboguer des solutions multiconteneurs, vous pouvez définir plusieurs points d’arrêt, chaque point d’arrêt dans un projet (conteneur) distinct, et, pendant le débogage à partir de Visual Studio, vous vous arrêtez aux points d’arrêt définis dans les différents projets et exécutés sur des conteneurs différents.

![Barre d’outils de débogage Visual Studio exécutant un projet docker-compose](./media/image16.png)

**Figure 5-12**. Exécution d’applications multiconteneurs dans Visual Studio 2017

### <a name="additional-resources"></a>Ressources supplémentaires

- **Déployer un conteneur ASP.NET sur un hôte Docker distant** \
  [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Note sur le test et le déploiement avec des orchestrateurs

Les commandes docker-compose up et docker run (ou l’exécution et le débogage des conteneurs dans Visual Studio) sont une approche appropriée pour tester les conteneurs dans votre environnement de développement. Toutefois, vous ne devez pas utiliser cette approche pour les déploiements de production, où vous devez cibler des orchestrateurs comme [Kubernetes](https://kubernetes.io/) ou [Service Fabric](https://azure.microsoft.com/services/service-fabric/). Si vous utilisez Kubernetes, vous devez utiliser des [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) pour organiser les conteneurs et des [services](https://kubernetes.io/docs/concepts/services-networking/service/) pour les mettre en réseau. Vous utilisez également des [déploiements](https://kubernetes.io/docs/tutorials/k8s201/#deployments) pour organiser la création et la modification des pods.

![6 - Tester votre application ou vos microservices](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Étape 6. Tester votre application Docker à l’aide de l’hôte Docker local

Cette étape varie en fonction de ce que fait votre application. Dans une application web .NET Core simple qui est déployée comme service ou conteneur unique, vous pouvez accéder au service en ouvrant un navigateur sur l’hôte Docker et en accédant à ce site (voir la figure 5-13). (Si la configuration dans le fichier Dockerfile mappe le conteneur à un autre port sur l’hôte que le port 80, incluez le port de l’hôte dans l’URL.)

![Vue dans le navigateur d’une réponse de point de terminaison d’API](./media/image18.png)

**Figure 5-13**. Exemple de test de l’application Docker en local avec localhost

Si localhost ne pointe pas vers l’IP hôte de Docker (contrairement à la configuration par défaut quand vous utilisez Docker CE), utilisez l’adresse IP de la carte réseau de votre machine pour pouvoir accéder à votre service.

Notez que cette URL dans le navigateur utilise le port 80 pour l’exemple de conteneur particulier présenté ici. Toutefois, en interne, les requêtes sont redirigées vers le port 5000, car le déploiement a été fait de cette façon avec la commande docker run, comme nous l’avons expliqué dans une étape précédente.

Vous pouvez également tester l’application en exécutant curl à partir du terminal, comme indiqué à la figure 5-14. Dans une installation Docker sur Windows, l’adresse IP par défaut de l’hôte Docker est toujours 10.0.75.1 en plus de l’adresse IP réelle de votre machine.

![Vue de l’écran d’une réponse de point de terminaison d’API avec curl](./media/image19.png)

**Figure 5-14**. Exemple de test de l’application Docker en local avec curl

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Test et débogage des conteneurs avec Visual Studio 2017

Quand vous exécutez et déboguez les conteneurs avec Visual Studio 2017, vous pouvez déboguer l’application .NET pratiquement de la même façon que pour une exécution sans conteneurs.

### <a name="testing-and-debugging-without-visual-studio"></a>Test et débogage sans Visual Studio

Si vous avez choisi l’approche de développement avec un éditeur ou une interface CLI, le débogage des conteneurs est plus difficile. Vous pouvez alors déboguer les conteneurs en générant des traces.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Débogage d’applications dans un conteneur Docker local** \
  [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- **Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.** Vidéo. \
  [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Workflow simplifié du développement de conteneurs avec Visual Studio

En effet, le workflow avec Visual Studio est beaucoup plus simple que si vous utilisez un éditeur ou une CLI. La plupart des étapes requises par Docker liées aux fichiers Dockerfile et docker-compose.yml sont masquées ou simplifiées par Visual Studio, comme illustré à la figure 5-15.

![Workflow de développement de conteneurs simplifié avec Visual Studio : 1 - Coder votre application, 2 - Ajouter la prise en charge de Docker aux projets (seulement une fois), 3 - Exécuter le conteneur ou l’application docker-compose, 4 - Tester votre application ou vos microservices, 5 - Pousser vers le dépôt et répéter.](./media/image20.png)

**Figure 5-15**. Workflow simplifié du développement avec Visual Studio

De plus, notez que vous devez effectuer l’étape 2 (ajout de la prise en charge de Docker à vos projets) une seule fois. Le workflow est donc similaire aux tâches de développement que vous avez l’habitude de faire dans le cadre d’un développement avec .NET. Vous devez comprendre ce qui se passe en arrière-plan (le processus de création d’image, les images de base utilisées, le déploiement des conteneurs, etc.) et parfois vous devez modifier le fichier Dockerfile ou docker-compose.yml pour personnaliser les comportements. Au final, Visual Studio simplifie considérablement la plupart des tâches et vous permet de développer beaucoup plus rapidement.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Steve Lasker. Développement Docker .NET avec Visual Studio 2017** \
  [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Utilisation de commandes PowerShell dans un fichier Dockerfile pour configurer des conteneurs Windows 

Les [conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) vous permettent de convertir vos applications Windows existantes en images Docker, puis de les déployer avec les mêmes outils que le reste de l’écosystème Docker. Pour utiliser les conteneurs Windows, vous exécutez des commandes PowerShell dans le fichier Dockerfile, comme indiqué dans l’exemple suivant :

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Dans ce cas, nous utilisons une image de base Windows Server Core (le paramètre FROM) et nous installons IIS à l’aide d’une commande PowerShell (le paramètre RUN). De la même façon, vous pouvez également utiliser des commandes PowerShell pour configurer des composants supplémentaires comme ASP.NET 4.x, .NET 4.6 ou tout autre logiciel Windows. Par exemple, la commande suivante dans un fichier Dockerfile configure ASP.NET 4.5 :

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Ressources supplémentaires

- **aspnet-docker/Dockerfile.** Exemples de commandes PowerShell à exécuter à partir de fichiers Dockerfile pour ajouter des fonctionnalités Windows.\
  [*https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile)

>[!div class="step-by-step"]
>[Précédent](index.md)
>[Suivant](../multi-container-microservice-net-applications/index.md)