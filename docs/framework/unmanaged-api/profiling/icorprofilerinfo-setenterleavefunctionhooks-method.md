---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d5ad57c3a5523494ce0384e665764bc02f679e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547421"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks, méthode
Spécifie les fonctions implémentées par le profileur à être appelée sur « entrée », « quitter » et « tailcall » de fonctions managées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFuncEnter`  
 [in] Un pointeur vers l’implémentation à utiliser comme la [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) rappel.  
  
 `pFuncLeave`  
 [in] Un pointeur vers l’implémentation à utiliser comme la [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) rappel.  
  
 `pFuncTailcall`  
 [in] Un pointeur vers l’implémentation à utiliser comme la [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) rappel.  
  
## <a name="remarks"></a>Notes  
 Dans le .NET Framework version 1.0, chaque pointeur fonction peut être null pour désactiver ce rappel correspondant.  
  
 Qu’un seul jeu de rappels peut être actif à la fois. Par conséquent, si un profileur appelle `SetEnterLeaveFunctionHooks` et [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), puis `SetEnterLeaveFunctionHooks2` est prioritaire.  
  
 Le `SetEnterLeaveFunctionHooks` méthode peut être appelée uniquement à partir du profileur [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) rappel.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
