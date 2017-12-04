---
title: "ICorProfilerInfo4::GetFunctionFromIP2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetFunctionFromIP2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2173326c5c67d1f4d3a8e28f84508fd6affb8299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="c3cda-102">ICorProfilerInfo4::GetFunctionFromIP2, méthode</span><span class="sxs-lookup"><span data-stu-id="c3cda-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="c3cda-103">Mappe un pointeur d’instruction de code managé vers la version recompilée juste-d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="c3cda-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3cda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3cda-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3cda-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3cda-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="c3cda-106">[in] Le pointeur d’instruction dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="c3cda-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="c3cda-107">[out] L’ID de fonction.</span><span class="sxs-lookup"><span data-stu-id="c3cda-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="c3cda-108">[out] L’identité de la version recompilée juste-de la fonction.</span><span class="sxs-lookup"><span data-stu-id="c3cda-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3cda-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="c3cda-109">Remarks</span></span>  
 <span data-ttu-id="c3cda-110">`GetFunctionFromIP2`est semblable à `GetFunctionFromIP`, sauf qu’elle obtient l’ID recompilé juste-au lieu de l’ID de la fonction de la fonction qui contient l’adresse IP spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c3cda-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3cda-111">`GetFunctionFromIP2`peut déclencher un garbage collection, tandis que `GetFunctionFromIP` ne seront pas.</span><span class="sxs-lookup"><span data-stu-id="c3cda-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="c3cda-112">Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="c3cda-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3cda-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c3cda-113">Requirements</span></span>  
 <span data-ttu-id="c3cda-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3cda-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3cda-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c3cda-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3cda-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3cda-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3cda-117">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3cda-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3cda-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3cda-118">See Also</span></span>  
 [<span data-ttu-id="c3cda-119">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="c3cda-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)