---
title: ICorDebugObjectEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a5f21855ce83f5c1fb68637e3eeb6d3c831bce2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745152"
---
# <a name="icordebugobjectenumnext-method"></a>ICorDebugObjectEnum::Next, méthode
Obtient les adresses virtuelles relatives (RVA) du nombre spécifié d’objets à partir de l’énumération, en commençant à la position actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Nombre d'objets à récupérer.  
  
 `objects`  
 [out] Tableau de pointeurs, chacun pointant vers un objet CORDB_ADDRESS.  
  
 `pceltFetched`  
 [out] Pointeur vers le nombre d’objets réellement retournés. Cette valeur peut être null si `celt` fait partie.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

