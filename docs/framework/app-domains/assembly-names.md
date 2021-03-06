---
title: Noms d'assemblys
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6447593ba81e4512afaf2b5798fcec00b755e63c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50184774"
---
# <a name="assembly-names"></a>Noms d'assemblys
Le nom d’un assembly est stocké dans des métadonnées, et il a un impact significatif sur l’étendue de l’assembly et sur son utilisation dans une application. Un assembly avec nom fort a un nom qualifié complet qui inclut le nom, la culture, la clé publique et le numéro de version de l’assembly. Ceci est fréquemment appelé le nom d’affichage et, pour les assemblys chargés, il peut être obtenu avec la propriété <xref:System.Reflection.Assembly.FullName%2A>.  
  
 Le runtime utilise ces informations pour localiser l’assembly et pour le différencier des autres assemblys portant le même nom. Par exemple, un assembly avec un nom fort appelé `myTypes` peut avoir le nom qualifié complet suivant :  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  Une architecture de processeur est ajoutée à l’identité de l’assembly dans le .NET Framework version 2.0, pour permettre des versions d’assemblys spécifiques au processeur. Vous pouvez créer des versions d’un assembly dont l’identité diffère seulement par l’architecture de processeur, par exemple des versions spécifiques à des processeurs 32 bits et 64 bits. L’architecture de processeur n’est pas obligatoire pour les noms forts. Pour plus d'informations, consultez <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 Dans cet exemple, le nom qualifié complet indique que l’assembly `myTypes` a un nom fort avec un jeton de clé publique, a comme valeur Anglais (États-Unis) pour la culture et a comme numéro de version 1.0.1234.0. Son architecture de processeur est « msil », ce qui signifie qu’il sera compilé juste-à-temps (JIT)-compilé en code 32 bits ou 64 bits, en fonction du système d’exploitation et du processeur.  
  
 Le code qui demande des types dans un assembly doit utiliser un nom d’assembly qualifié complet. Ceci s’appelle une liaison qualifiée complète. Une liaison partielle, qui spécifie seulement un nom d’assembly, n’est pas autorisée lors du référencement d’assemblys dans le .NET Framework.  
  
 Toutes les références d’un assembly à des assemblys qui composent le .NET Framework doivent également contenir un nom qualifié complet de l’assembly. Par exemple, une référencer à l’assembly .NET Framework System.Data pour la version 1.0 va inclure :  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Notez que la version correspond au numéro de version de tous les assemblys .NET Framework fournis avec le .NET Framework version 1.0. Pour les assemblys .NET Framework, la valeur de culture est toujours neutre, et la clé publique est identique à celle qui est montrée dans l’exemple ci-dessus.  
  
 Par exemple, pour ajouter une référence d’assembly dans un fichier de configuration pour configurer un écouteur de suivi, vous incluez le nom qualifié complet de l’assembly system de .NET Framework :  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  Le runtime traite les noms d’assemblys sans tenir compte de la casse lors de la liaison à un assembly, mais il conserve la casse utilisée dans un nom d’assembly. Plusieurs outils des [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] gèrent les noms d’assemblys en tenant compte de la casse. Pour de meilleurs résultats, gérez les noms d’assemblys comme s’ils tenaient compte de la casse.  
  
## <a name="naming-application-components"></a>Nommage des composants d’application  
 Le runtime ne prend pas en compte pas le nom de fichier pour déterminer l’identité d’un assembly. L’identité de l’assembly, qui est constituée du nom, de la version, de la culture et du nom fort de l’assembly, doit être claire pour le runtime.  
  
 Par exemple, si vous avez un assembly appelé monAssembly.exe qui référence un assembly appelé monAssembly.dll, la liaison se fait correctement si vous exécutez monAssembly.exe. Cependant, si une autre application exécute monAssembly.exe en utilisant la méthode <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, le runtime détermine que « monAssembly » est déjà chargé quand monAssembly.exe demande la liaison à « monAssembly ». Dans ce cas, monAssembly.dll n’est jamais chargé. Comme monAssembly.exe ne contient pas le type demandé, une <xref:System.TypeLoadException> se produit.  
  
 Pour éviter ce problème, vérifiez que les assemblys qui composent votre application n’ont pas le même nom d’assembly ou que vous placez les assemblys portant le même nom dans des répertoires différents.  
  
> [!NOTE]
>  Si vous placez un assembly avec nom fort dans le Global Assembly Cache, le nom de fichier de l’assembly doit correspondre au nom de l’assembly (sans l’extension de nom de fichier, comme .exe ou .dll). Par exemple, si le nom de fichier d’un assembly est monAssembly.dll, le nom de l’assembly doit être monAssembly. Les assemblys privés déployés uniquement dans le répertoire racine de l’application peuvent avoir un nom d’assembly différent du nom du fichier.  
  
## <a name="see-also"></a>Voir aussi  
- [Guide pratique pour déterminer le nom qualifié complet d'un assembly](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
- [Création d’assemblys](../../../docs/framework/app-domains/create-assemblies.md)  
- [Assemblys avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md)  
- [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)  
- [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)
