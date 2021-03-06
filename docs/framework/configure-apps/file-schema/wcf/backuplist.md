---
title: '&lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: c11fd38e7c40f740d4c1c36ab87c44744ed0daab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627981"
---
# <a name="ltbackuplistgt"></a>&lt;backupList&gt;
Représente une section de configuration pour définir une liste de sauvegarde qui énumère un ensemble de points de terminaison que vous souhaitez que le Service de routage à utiliser au cas où le point de terminaison principal n’est pas accessible. Si le premier point de terminaison de la liste est inactif, le service de routage bascule automatiquement sur le suivant dans la liste.  Vous disposez ainsi d’une méthode rapide pour renforcer la fiabilité de votre application sans avoir à apprendre à votre application cliente à gérer des modèles complexes ou à rechercher l’emplacement de tous vos services déployés.  
  
 \<system.serviceModel>  
\<routing>  
\<backupLists>  
\<backupList>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Chaîne qui spécifie le nom permettant d'identifier la liste de points de terminaison.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Liste de points de terminaison de sauvegarde.|  
  
## <a name="remarks"></a>Notes  
 Cette section contient une collection ordonnée de points de terminaison auxquels un message sera transmis si une exception de communication se produit lors de l’envoi au point de terminaison primaire.  
  
 Si un envoi au point de terminaison primaire répertorié dans le `endpointName` attribut de [ \<Ajouter >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) échoue avec une exception de communication, le Service de routage essaiera d’envoyer le message au premier point de terminaison dans ce section de configuration. Si l’opération échoue également avec une exception de communication, le service de routage essaie d’envoyer le message au point de terminaison suivant contenu dans cette section jusqu’à ce que la tentative d’envoi aboutisse, retourne une erreur autre qu’une exception de communication, ou que tous les points de terminaison de la collection retournent une erreur.  
  
 Dans l’exemple suivant, si un envoi au point de terminaison primaire appelé « Destination » retourne une exception de communication, le service essaiera d’envoyer le message à « alternateServiceQueue ». Si cette tentative retourne également une exception de communication, le service de routage essaiera d’envoyer le message au point de terminaison suivant dans la collection.  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
