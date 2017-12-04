---
title: CLRCreateInstance, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type: COM
f1_keywords: CLRCreateInstance
helpviewer_keywords: CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f10fe48bc2b61a9de5d0703720629f31531c1ea1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="21fbd-102">CLRCreateInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="21fbd-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="21fbd-103">Fournit l’un des trois interfaces : [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), ou [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="21fbd-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21fbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21fbd-104">Syntax</span></span>  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21fbd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21fbd-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="21fbd-106">[in] Un des trois identificateurs de classe : arguments CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy ou CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="21fbd-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="21fbd-107">[in] Un des trois identificateurs d’interface (IID) : IID_ICLRMetaHost, IID_ICLRMetaHostPolicy ou IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="21fbd-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="21fbd-108">[out] Un des trois interfaces : [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), ou [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="21fbd-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21fbd-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="21fbd-109">Return Value</span></span>  
 <span data-ttu-id="21fbd-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="21fbd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="21fbd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21fbd-111">HRESULT</span></span>|<span data-ttu-id="21fbd-112">Description</span><span class="sxs-lookup"><span data-stu-id="21fbd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21fbd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="21fbd-113">S_OK</span></span>|<span data-ttu-id="21fbd-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="21fbd-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="21fbd-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="21fbd-115">E_POINTER</span></span>|<span data-ttu-id="21fbd-116">`ppInterface` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="21fbd-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21fbd-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="21fbd-117">Remarks</span></span>  
 <span data-ttu-id="21fbd-118">Le tableau suivant affiche les combinaisons prises en charge pour `clsid` et `riid`.</span><span class="sxs-lookup"><span data-stu-id="21fbd-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="21fbd-119">Arguments CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="21fbd-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="21fbd-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="21fbd-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="21fbd-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="21fbd-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="21fbd-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="21fbd-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="21fbd-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="21fbd-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="21fbd-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="21fbd-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="21fbd-125">Le code suivant montre comment utiliser `CLRCreateInstance` pour obtenir ces trois interfaces :</span><span class="sxs-lookup"><span data-stu-id="21fbd-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="21fbd-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="21fbd-126">Requirements</span></span>  
 <span data-ttu-id="21fbd-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21fbd-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21fbd-128">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="21fbd-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="21fbd-129">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21fbd-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21fbd-130">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21fbd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21fbd-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21fbd-131">See Also</span></span>  
 [<span data-ttu-id="21fbd-132">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="21fbd-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)