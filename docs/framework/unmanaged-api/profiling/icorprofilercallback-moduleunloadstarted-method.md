---
title: ICorProfilerCallback::ModuleUnloadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5981e9a193f4ebfc88628f56cf865523c9b87c6f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744646"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a>ICorProfilerCallback::ModuleUnloadStarted, méthode
Notifie le profileur qu’un module est déchargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
#### <a name="parameters"></a>Paramètres  
 `moduleId`  
 [in] L’ID du module qui est en cours de déchargement.  
  
## <a name="remarks"></a>Notes  
 La valeur de `moduleId` n’est pas valide pour une demande d’informations après la `ModuleUnloadStarted` retourne de la méthode, il s’agit dernière chance du profileur d’obtenir des informations sur ce module.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ModuleUnloadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
