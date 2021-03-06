---
title: IDefinitionAppId, interface
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e8bb31967a6ad515761e6cd03657f2c834debe5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545554"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId, interface
Représente un identificateur unique pour le code qui définit l’application dans la portée actuelle.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Obtient une chaîne mise en forme qui représente le code de cette `IDefinitionAppId` objet.|  
|`IDefinitionAppId::put_Codebase`|Définit le code de cet `IDefinitionAppId` objet spécifié à la mise en forme la valeur de chaîne.|  
|`IDefinitionAppId::EnumAppPath`|Obtient un pointeur d’interface vers un [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) objet qui contient les assemblys dans le chemin d’accès d’application actuel.|  
|`IDefinitionAppId::SetAppPath`|Définit le chemin d’accès de l’application pour l’assembly dans la portée actuelle à la valeur référencée par le [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) objet.|  
|`IDefinitionAppId::get_SubscriptionId`|Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de jeton pour un abonnement à ce `IDefinitionAppId` objet.|  
|`IDefinitionAppId::put_SubscriptionId`|Définit l’identificateur de jeton pour un abonnement à ce `IDefinitionAppId` objet à la valeur de chaîne spécifiée.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Isolation.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [Interfaces de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
