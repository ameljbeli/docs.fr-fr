---
title: ICorDebugVirtualUnwinder::GetContext, méthode
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec68e36e2e5a06836d0f5d5758a230591626b03e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744100"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext, méthode
Obtient le contexte actuel de ce dérouleur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `contextFlags`  
 [in] Indicateurs spécifiant les parties du contexte à retourner (définition contenue dans WinNT.h).  
  
 `cbContextBuf`  
 [in] Nombre d'octets dans `contextBuf`.  
  
 `contextSize`  
 [out] Pointeur vers le nombre d'octets réellement écrits dans `contextBuf`.  
  
 `contextBuf`  
 [out] Tableau d'octets contenant le contexte actuel de ce dérouleur.  
  
## <a name="return-value"></a>Valeur de retour  
 Toute valeur HRESULT indiquant un échec reçue par mscordbi est considérée comme irrécupérable et forcent les API ICorDebug à retourner `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Notes  
 Vous définissez la valeur initiale de la `contextBuf` l’argument de la mémoire tampon de contexte retourné en appelant le [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) (méthode).  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
 Le déroulement ne pouvant restaurer qu'un sous-ensemble des registres, par exemple les registres non volatiles, le contexte peut différer de l'état du registre au moment de l'appel de la méthode.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [ICorDebugMemoryBuffer, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
