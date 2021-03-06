---
title: ESymbolReadingPolicy, énumération
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e17f88cf7f0d8572e65d00d8500a1fd83aa44eeb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663912"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy, énumération
Contient des valeurs qui définissent la stratégie pour la lecture des fichiers de programme (PDB) de la base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eSymbolReadingAlways`|Spécifie que le débogueur doit toujours lire des fichiers PDB.|  
|`eSymbolReadingFullTrustOnly`|Spécifie que le débogueur doit lire uniquement les fichiers PDB qui sont associés à des assemblys de confiance totale.|  
|`eSymbolReadingNever`|Spécifie que le débogueur doit lire jamais les fichiers PDB.|  
  
## <a name="remarks"></a>Notes  
 Le `ESymbolReadingPolicy` énumération est utilisée avec la [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
