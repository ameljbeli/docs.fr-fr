---
title: INotifySink2, interface
ms.date: 03/30/2017
api_name:
- INotifySink2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2
helpviewer_keywords:
- INotifySink2 interface [.NET Framework debugging]
ms.assetid: c1018789-4206-455d-aacc-2d876fc0d0bb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc5d09ac12919b8c68b9fe4bf9f7dc0009b2d4b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705467"
---
# <a name="inotifysink2-interface"></a>INotifySink2, interface
Déclare des méthodes pour la notification du récepteur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[OnSyncCallEnter, méthode](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)|Est appelé lors de la saisie d’un appel.|  
|[OnSyncCallExit, méthode](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)|Est appelé lors de la sortie d’un appel.|  
|[OnSyncCallOut, méthode](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)|Appelée lorsque l’appel est sortant.|  
|[OnSyncCallReturn, méthode](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)|Appelée lorsqu’un appel est retourné.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Voir aussi
- [INotifyConnection2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [INotifySource2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [Interfaces du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
