---
title: ICorDebugCode::GetILToNativeMapping, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8614dd612fff2886c4e44a977d05a575fce74eec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648941"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping, méthode
Obtient un tableau d’instances de « COR_DEBUG_IL_TO_NATIVE_MAP » qui représentent les mappages à partir de Microsoft intermediate language (MSIL) aux offsets natifs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cMap`  
 [in] Taille du tableau `map`.  
  
 `pcMap`  
 [out] Un pointeur vers le nombre réel d’éléments retournés dans le `map` tableau.  
  
 `map`  
 [out] Un tableau de `COR_DEBUG_IL_TO_NATIVE_MAP` structures, chacun d’eux représente un mappage d’un offset MSIL à un offset natif.  
  
 Il n’existe aucun classement dans le tableau d’éléments retournés.  
  
## <a name="remarks"></a>Notes  
 Le `GetILToNativeMapping` méthode retourne des résultats significatifs uniquement si cette instance de « ICorDebugCode » représente le code natif qui a été compilé à partir du code MSIL juste-à-temps (JIT).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [ICorDebugCode, interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
