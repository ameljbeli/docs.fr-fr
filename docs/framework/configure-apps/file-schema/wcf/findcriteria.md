---
title: '&lt;findCriteria&gt;'
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: b90e6cab923075dbf750dc0d26a0eb1196cfde32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741238"
---
# <a name="ltfindcriteriagt"></a>&lt;findCriteria&gt;
Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte. Critères peuvent être regroupées en critères de recherche (spécifiant les services que vous recherchez) et recherchez les critères d’arrêt (la durée pendant laquelle la recherche doit durer).  
  
 \<system.ServiceModel>  
\<standardEndpoints>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|duration|Valeur Timespan qui spécifie le temps d'attente maximal des réponses envoyées par les services sur le réseau. La durée par défaut est de 20 secondes.|  
|maxResults|Entier qui spécifie le nombre maximal de réponses à attendre en provenance des services sur un réseau ou sur Internet. Si le nombre maximal de réponses est reçu avant l'écoulement du délai d'attente spécifié dans l'attribut `duration`, l'opération de recherche prend fin.|  
|scopeMatchBy|URI qui spécifie l'algorithme de correspondance à utiliser, lors de la comparaison des portées dans le message Probe avec celles du point de terminaison.<br /><br /> Il existe cinq règles de correspondance de portée prises en charge. Si vous ne spécifiez pas de règle de correspondance de portée, `ScopeMatchByPrefix` est utilisé. Pour plus d'informations, consultez <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<contractTypeNames>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Une collection d’éléments de configuration qui contiennent les noms de types de contrat de service de workflow.|  
|\<extensions > de \<findCriteria >|Collection d’objets d’élément XML qui fournissent des extensions.|  
|[\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Collection d’objets qui contiennent des URI absolus utilisés pendant une opération de recherche afin de localiser des services ou un service particulier.<br /><br /> Si le service particulier est trouvé, une correspondance réussie est établie entre l'URI de service et l'URI de portée, parfois à l'aide de règles de portée qui gèrent les problèmes de correspondance.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Contient les paramètres requis par une application pour participer au processus de découverte de service en tant que client.|  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
