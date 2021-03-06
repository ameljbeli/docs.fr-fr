---
title: Vue d'ensemble des paramètres d'application
ms.date: 03/30/2017
f1_keywords:
- ApplicationsSettingsOverview
helpviewer_keywords:
- application settings [Windows Forms], about application settings
- dynamic properties
- user preferences [Windows Forms], tracking
ms.assetid: 0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc
ms.openlocfilehash: b30203aaf36d4fa6c0b06d54da1abc1f99d22afc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576900"
---
# <a name="application-settings-overview"></a>Vue d'ensemble des paramètres d'application
Cette rubrique explique comment créer et stocker des données de paramètres pour le compte de votre application et de vos utilisateurs.  
  
 La fonctionnalité Paramètres des applications de Windows Forms simplifie la création, le stockage et la gestion des applications personnalisées et des préférences utilisateur sur l’ordinateur client. Avec les paramètres des applications Windows Forms, vous pouvez stocker non seulement des données d'application telles que des chaînes de connexion de base de données, mais également des données spécifiques à l'utilisateur, telles que les préférences des applications utilisateur. À l'aide de Visual Studio ou de code managé personnalisé, vous pouvez créer de nouveaux paramètres, les lire et écrire sur disque, les lier à des propriétés sur vos formulaires et valider les données des paramètres avant le chargement et l'enregistrement.  
  
 Les paramètres des applications permettent aux développeurs d'enregistrer l'état dans leur application avec très peu de code personnalisé. Ils remplacent les propriétés dynamiques dans les versions précédentes de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Les paramètres des applications contiennent de nombreuses améliorations par rapport aux propriétés dynamiques, qui sont en lecture seule, à liaison tardive et nécessitent davantage de programmation personnalisée. Les classes de propriétés dynamiques ont été conservées dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], mais il s'agit simplement de classes de shell qui encapsulent de manière dynamique les classes de paramètres d'application.  
  
## <a name="what-are-application-settings"></a>Présentation des paramètres d'application  
 Vos applications Windows Forms nécessitent souvent des données critiques pour l'exécution de l'application, mais que vous ne souhaitez pas inclure directement dans le code de l'application. Si votre application utilise un service web ou un serveur de bases de données, vous souhaiterez peut-être stocker ces informations dans un fichier distinct, pour pouvoir le modifier à l'avenir sans recompilation. De même, vos applications peuvent nécessiter le stockage des données spécifiques à l'utilisateur actuel. La plupart des applications, par exemple, offrent des préférences utilisateur qui permettent de personnaliser leur apparence et leur comportement.  
  
 Les paramètres d'application répondent à ces deux besoins en fournissant un mécanisme simple de stockage des paramètres de portée application et de portée utilisateur sur l'ordinateur client. Avec Visual Studio ou un éditeur de code, vous définissez un paramètre pour une propriété donnée en spécifiant son nom, son type de données et sa portée (application ou utilisateur). Vous pouvez même placer des paramètres connexes dans des groupes nommés pour faciliter leur utilisation et leur lisibilité. Une fois définis, ces paramètres sont conservés et lus en mémoire automatiquement au moment de l'exécution. Une architecture enfichable permet de modifier le mécanisme de persistance, mais par défaut le système de fichiers local est utilisé.  
  
 Les paramètres d'application rendent les données persistantes au format XML dans différents fichiers de configuration (.config) en fonction de la portée du paramètre (application ou utilisateur). Dans la plupart des cas, les paramètres de portée application sont en lecture seule. Comme il s'agit d'informations sur le programme, vous n'aurez généralement pas besoin de les remplacer. En revanche, les paramètres de portée utilisateur peuvent être lus et modifiés en toute sécurité au moment de l'exécution, même si votre application s'exécute en mode de confiance partielle. Pour plus d’informations sur la confiance partielle, consultez [Security in Windows Forms Overview](../../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
 Les paramètres sont stockés en tant que fragments XML dans des fichiers de configuration. Les paramètres de portée application sont représentés par l'élément `<application.Settings>` et sont généralement placés dans *application*. exe.config, où *application* est le nom de votre fichier exécutable principal. Les paramètres de portée utilisateur sont représentés par l'élément `<userSettings>` et sont placés dans *utilisateur*.config, où *utilisateur* est le nom d'utilisateur de la personne qui exécute actuellement l'application. Vous devez déployer le fichier *application*.exe.config avec votre application. L'architecture de paramètres créera les fichiers *utilisateur*.config sur demande la première fois que l'application enregistrera les paramètres pour cet utilisateur. Vous pouvez également définir un bloc `<userSettings>` dans *application*.exe.config pour fournir des valeurs par défaut pour les paramètres de portée utilisateur.  
  
 Les contrôles personnalisés peuvent aussi enregistrer leurs propres paramètres en implémentant l'interface <xref:System.Configuration.IPersistComponentSettings> , qui expose la méthode <xref:System.Configuration.IPersistComponentSettings.SaveSettings%2A> . Le contrôle Windows Forms <xref:System.Windows.Forms.ToolStrip> implémente cette interface pour enregistrer la position des barres d'outils et des éléments de barre d'outils d'une session d'application à une autre. Pour plus d’informations sur les contrôles personnalisés et les paramètres d’application, consultez [Application Settings for Custom Controls](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md).  
  
## <a name="limitations-of-application-settings"></a>Limitations des paramètres d'application  
 Vous ne pouvez pas utiliser les paramètres d'application dans une application non managée qui héberge [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Les paramètres ne fonctionnent pas dans des environnements tels que les compléments Visual Studio, C++ pour Microsoft Office, l'hébergement de contrôles dans Internet Explorer ou les projets et les compléments Microsoft Outlook.  
  
 À l'heure actuelle, vous ne pouvez pas établir de liaison à certaines propriétés dans Windows Forms. L'exemple le plus notable est la propriété <xref:System.Windows.Forms.Form.ClientSize%2A> , car une liaison à cette propriété provoque un comportement imprévisible au moment de l'exécution. En règle générale, vous pouvez contourner ces problèmes en enregistrant et en chargeant ces paramètres par programmation.  
  
 Les paramètres d'application n'ont aucune fonctionnalité intégrée pour chiffrer automatiquement les informations. Vous ne devez jamais stocker d'informations relatives à la sécurité, telles que des mots de passe de base de données, en texte clair. Si vous souhaitez stocker ce genre d'informations sensibles, en tant que développeur de l'application vous êtes chargé de vous assurer qu'elles sont sécurisées. Si vous souhaitez stocker des chaînes de connexion, nous vous recommandons d'utiliser la sécurité intégrée de Windows et de ne pas recourir au codage en dur des mots de passe dans l'URL. Pour plus d'informations, consultez [Code Access Security and ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md).  
  
## <a name="getting-started-with-application-settings"></a>Prise en main des paramètres d'application  
 Si vous utilisez Visual Studio, vous pouvez définir des paramètres dans le Concepteur Windows Forms à l'aide de la propriété **(ApplicationSettings)** dans la fenêtre **Propriétés** . Quand vous définissez des paramètres de cette façon, Visual Studio crée automatiquement une classe wrapper managée personnalisée qui associe chaque paramètre à une propriété de classe. Visual Studio se charge aussi de la liaison du paramètre à une propriété sur un formulaire ou un contrôle pour que les paramètres du contrôle soient restaurés automatiquement quand son formulaire est affiché et enregistrés automatiquement quand le formulaire est fermé.  
  
 Si vous souhaitez bénéficier d'un contrôle plus précis sur vos paramètres, vous pouvez définir votre propre classe wrapper de paramètres d'application personnalisée. Pour cela, vous devez dériver une classe de <xref:System.Configuration.ApplicationSettingsBase>, ajouter une propriété qui correspond à chaque paramètre, puis appliquer des attributs spéciaux à ces propriétés. Pour plus d’informations sur la création de classes wrapper, consultez [Application Settings Architecture](../../../../docs/framework/winforms/advanced/application-settings-architecture.md).  
  
 Vous pouvez également utiliser la classe <xref:System.Windows.Forms.Binding> pour lier des paramètres par programmation à des propriétés sur des formulaires et des contrôles.  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- <xref:System.Configuration.IPersistComponentSettings>
- [Guide pratique pour Valider les paramètres d’Application](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
- [Gestion des paramètres d’une application (.NET)](https://msdn.microsoft.com/library/35254321-ad14-47d9-b8c6-39ab3203c5d9)
- [Guide pratique pour Lire des paramètres au moment de l’exécution avecC#](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)
- [Utilisation de paramètres d'application et de paramètres utilisateur](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Architecture des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
- [Application Settings for Custom Controls](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)
