---
title: Processus de développement des applications basées sur Docker
description: Obtenez une vue d’ensemble détaillée des options pour le développement d’applications basées sur Docker. Utilisation de votre choix de Visual Studio pour Windows, Visual Studio pour Mac ou Visual Studio Code pour la prise en charge multiplateforme (Windows, Mac et Linux).
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/27/2018
ms.openlocfilehash: eb87f9a214dbffe71dae1e1739f2563c08fac280
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084925"
---
# <a name="development-process-for-docker-based-applications"></a>Processus de développement des applications basées sur Docker

*Développez des applications .NET en conteneur comme vous le souhaitez, soit dans un environnement de développement intégré (IDE) avec Visual Studio et Visual Studio Tools pour Docker, soit avec une interface CLI/un éditeur avec une interface CLI Docker et Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Environnement de développement pour les applications Docker

### <a name="development-tool-choices-ide-or-editor"></a>Choix des outils de développement : IDE ou éditeur

Que vous préfériez un IDE complet et puissant ou un éditeur léger et agile, Microsoft propose des outils que vous pouvez utiliser pour développer des applications Docker.

**Visual Studio (pour Windows)**. Lorsque vous développez des applications basées sur Docker avec Visual Studio, il est recommandé d’utiliser Visual Studio 2017 version 15.7 ou ultérieure, qui est fourni avec les outils intégrés pour Docker. Les outils pour Docker vous permettent de développer, exécuter et valider vos applications directement dans l’environnement Docker cible. Vous pouvez appuyer sur F5 pour exécuter et déboguer votre application (conteneur unique ou plusieurs conteneurs) directement dans un hôte Docker, ou appuyer sur Ctrl+F5 pour modifier et actualiser votre application sans avoir à régénérer le conteneur. Ceci est le meilleur choix pour le développement d’applications basées sur Docker.

**Visual Studio pour Mac.** C’est un IDE (évolution de Xamarin Studio) qui s’exécute dans macOS et qui prend en charge Docker depuis la mi-année 2017. Ce choix est recommandé pour les développeurs qui travaillent sur des ordinateurs Mac et qui veulent utiliser un IDE puissant.

**Visual Studio Code et interface CLI Docker**. Si vous préférez un éditeur léger et multiplateforme qui prend en charge n’importe quel langage de développement, vous pouvez utiliser Microsoft Visual Studio Code (VS Code) et l’interface CLI Docker. Il s’agit d’une approche de développement multiplateforme pour Mac, Linux et Windows. De plus, Visual Studio Code prend en charge les extensions pour Docker comme IntelliSense pour les Dockerfiles et les tâches de raccourci afin d’exécuter des commandes Docker à partir de l’éditeur.

En installant les outils [Docker Community Edition (CE)](https://www.docker.com/community-edition), vous pouvez utiliser une seule interface CLI Docker pour générer des applications pour Windows et Linux.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Visual Studio**. Site officiel. \
  [*https://visualstudio.microsoft.com/vs/*](https://visualstudio.microsoft.com/vs/)

- **Visual Studio Code**. Site officiel. \
  [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

- **Docker Community Edition (CE) pour Mac et Windows** \
  [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Langages et frameworks .NET pour conteneurs Docker

Comme indiqué dans les sections précédentes de ce guide, vous pouvez utiliser .NET Framework, .NET Core ou le projet Mono open source pour développer des applications .NET Docker en conteneur. Vous pouvez développer en C\#, F\# ou Visual Basic quand vous ciblez des conteneurs Linux ou Windows, selon le .NET Framework en cours d’utilisation. Pour plus d’informations sur les langages .NET, consultez le billet de blog [Stratégie de langage .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Précédent](../architect-microservice-container-applications/using-azure-service-fabric.md)
>[Suivant](docker-app-development-workflow.md)