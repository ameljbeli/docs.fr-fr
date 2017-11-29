---
title: "ICorDebugTypeEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugTypeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38f48c379ad4d84c2b16c208b33b71ac75caa52f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="89398-102">ICorDebugTypeEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="89398-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="89398-103">Obtient le nombre d’instances de « ICorDebugType » spécifié par `celt` à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="89398-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89398-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89398-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89398-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89398-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="89398-106">[in] Le nombre de `ICorDebugType` instances doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="89398-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="89398-107">[out] Un tableau de pointeurs, chacun pointant vers un `ICorDebugType` objet.</span><span class="sxs-lookup"><span data-stu-id="89398-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="89398-108">[out] Pointeur vers le nombre de `ICorDebugType` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="89398-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="89398-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="89398-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89398-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="89398-110">Requirements</span></span>  
 <span data-ttu-id="89398-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89398-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89398-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89398-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89398-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89398-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89398-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89398-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89398-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89398-115">See Also</span></span>  
 