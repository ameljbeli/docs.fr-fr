---
title: '&lt;Thread_UseAllCpuGroups&gt; élément'
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80f67502c61df13b17cfb3b75564d710e5fad2f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579939"
---
# <a name="ltthreaduseallcpugroupsgt-element"></a>&lt;Thread_UseAllCpuGroups&gt; élément
Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.  
  
 \<configuration>  
\<runtime>  
<Thread_UseAllCpuGroups>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Indique si le runtime distribue les threads managés entre tous les groupes de processeurs.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|`false`|Le runtime ne distribue pas les threads managés entre plusieurs groupes d’UC. Il s'agit de la valeur par défaut.|  
|`true`|Le runtime distribue les threads managés entre plusieurs groupes d’UC, si l’ordinateur dispose de plusieurs groupes d’UC et le [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) élément est activé.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’un ordinateur a plusieurs groupes d’UC, l’activation de cet élément, le runtime répartir les threads managés entre tous les groupes d’UC. Pour utiliser cette fonctionnalité, vous devez également activer le [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) élément, qui étend le garbage collection pour tous les groupes d’UC et tous les cœurs ne prend en compte lors de la création et l’équilibrage des segments de mémoire. L’activation de la [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) élément requiert l’activation de la [ \<< gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) élément. Si ces éléments ne sont pas activées, l’activation de la `<Thread_UseAllCpuGroups>` élément n’a aucun effet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment activer la prise en charge de plusieurs groupes d’UC.  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi
- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<GCCpuGroup > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
