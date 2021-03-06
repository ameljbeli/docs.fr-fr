---
title: ICLRDataTarget2::FreeVirtual, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02bba59a1c4445b3e432d5e44f2bccc4b72ce1da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711653"
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual, méthode
Appelé par les services d’accès aux données du common language runtime (CLR) à la mémoire précédemment allouée dans l’espace d’adressage du processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `addr`  
 [in] Un `CLRDATA_ADDRESS` valeur qui spécifie l’adresse de départ de la mémoire à libérer.  
  
 `size`  
 [in] La taille, en octets, de la mémoire à libérer.  
  
 `typeFlags`  
 [in] Indicateurs qui contrôlent la libération de mémoire. Consultez Win32 `VirtualFree` (fonction).  
  
## <a name="remarks"></a>Notes  
 Le `FreeVirtual` méthode sert de wrapper logique pour Win32 `VirtualFree` (fonction).  
  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [ICLRDataTarget2, interface](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [AllocVirtual, méthode](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
