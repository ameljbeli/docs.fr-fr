---
title: COR_HEAPOBJECT, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_HEAPOBJECT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_HEAPOBJECT
helpviewer_keywords: COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bcd971853707349bf0d60459cb46b0fea1e8a97b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="corheapobject-structure"></a><span data-ttu-id="79d7d-102">COR_HEAPOBJECT, structure</span><span class="sxs-lookup"><span data-stu-id="79d7d-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="79d7d-103">Fournit des informations à propos d’un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="79d7d-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79d7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79d7d-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="79d7d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="79d7d-105">Members</span></span>  
  
|<span data-ttu-id="79d7d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="79d7d-106">Member</span></span>|<span data-ttu-id="79d7d-107">Description</span><span class="sxs-lookup"><span data-stu-id="79d7d-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="79d7d-108">L’adresse de l’objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="79d7d-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="79d7d-109">La taille totale de l’objet, en octets.</span><span class="sxs-lookup"><span data-stu-id="79d7d-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="79d7d-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) jeton qui représente le type de l’objet.</span><span class="sxs-lookup"><span data-stu-id="79d7d-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79d7d-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="79d7d-111">Remarks</span></span>  
 <span data-ttu-id="79d7d-112">`COR_HEAPOBJECT`instances peuvent être récupérées par l’énumération d’une [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objet d’interface qui est remplie en appelant le [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="79d7d-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="79d7d-113">A `COR_HEAPOBJECT` instance fournit des informations sur un objet dynamique sur le tas managé, ou sur un objet qui n’est pas associé à une racine par n’importe quel objet, mais n’a pas encore été collecté par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="79d7d-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="79d7d-114">Pour de meilleures performances, le `COR_HEAPOBJECT.address` champ est un `CORDB_ADDRESS` valeur plutôt que ICorDebugValue valeur utilisée dans une grande partie de l’API de débogage de l’interface.</span><span class="sxs-lookup"><span data-stu-id="79d7d-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="79d7d-115">Pour obtenir un objet ICorDebugValue pour une adresse de l’objet donné, vous pouvez passer le `CORDB_ADDRESS` valeur le [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="79d7d-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="79d7d-116">Pour de meilleures performances, le `COR_HEAPOBJECT.type` champ est un `COR_TYPEID` valeur plutôt que la ICorDebugType valeur utilisée dans une grande partie de l’API de débogage de l’interface.</span><span class="sxs-lookup"><span data-stu-id="79d7d-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="79d7d-117">Pour obtenir un objet ICorDebugType pour un ID de type donné, vous pouvez passer le `COR_TYPEID` valeur le [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="79d7d-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="79d7d-118">Le `COR_HEAPOBJECT` structure inclut une interface COM contenant des références.</span><span class="sxs-lookup"><span data-stu-id="79d7d-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="79d7d-119">Si vous récupérez un `COR_HEAPOBJECT` instance à partir de l’énumérateur en appelant le [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) (méthode), vous devez libérer par la suite de la référence.</span><span class="sxs-lookup"><span data-stu-id="79d7d-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79d7d-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="79d7d-120">Requirements</span></span>  
 <span data-ttu-id="79d7d-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79d7d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79d7d-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79d7d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79d7d-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79d7d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79d7d-124">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79d7d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79d7d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79d7d-125">See Also</span></span>  
 [<span data-ttu-id="79d7d-126">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="79d7d-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="79d7d-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="79d7d-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)