---
title: "ICorPublishProcess::EnumAppDomains, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.EnumAppDomains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 09d6a75fa5c0562f466dba45707795ef7fd161db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="8b39b-102">ICorPublishProcess::EnumAppDomains, méthode</span><span class="sxs-lookup"><span data-stu-id="8b39b-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="8b39b-103">Obtient un énumérateur pour les domaines d’application dans le processus qui est référencé par ce [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8b39b-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b39b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b39b-104">Syntax</span></span>  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b39b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8b39b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="8b39b-106">[out] Un pointeur vers l’adresse d’un [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance qui permet l’itération dans la collection de domaines d’application dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="8b39b-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b39b-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="8b39b-107">Remarks</span></span>  
 <span data-ttu-id="8b39b-108">La liste des domaines d’application est basée sur un instantané des domaines d’application qui existe lorsque le `EnumAppDomains` méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="8b39b-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="8b39b-109">Cette méthode peut être appelée plusieurs fois pour créer une liste à jour.</span><span class="sxs-lookup"><span data-stu-id="8b39b-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="8b39b-110">Listes existantes ne seront pas affectées par les appels suivants de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8b39b-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="8b39b-111">Si le processus a été arrêté, `EnumAppDomains` échoue avec une valeur HRESULT de CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="8b39b-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b39b-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8b39b-112">Requirements</span></span>  
 <span data-ttu-id="8b39b-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b39b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b39b-114">**En-tête :** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="8b39b-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8b39b-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b39b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b39b-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b39b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b39b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b39b-117">See Also</span></span>  
 [<span data-ttu-id="8b39b-118">ICorPublishProcess (Interface)</span><span class="sxs-lookup"><span data-stu-id="8b39b-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)