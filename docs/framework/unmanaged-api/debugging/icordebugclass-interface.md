---
title: ICorDebugClass Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass
helpviewer_keywords: ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79e93a44f2cc532286a7e9b01fa32292a4e1c69a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass-interface1"></a><span data-ttu-id="c99db-102">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="c99db-102">ICorDebugClass Interface1</span></span>
<span data-ttu-id="c99db-103">Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur).</span><span class="sxs-lookup"><span data-stu-id="c99db-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="c99db-104">Si le type est générique, `ICorDebugClass` représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="c99db-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c99db-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c99db-105">Methods</span></span>  
  
|<span data-ttu-id="c99db-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="c99db-106">Method</span></span>|<span data-ttu-id="c99db-107">Description</span><span class="sxs-lookup"><span data-stu-id="c99db-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c99db-108">GetModule (méthode)</span><span class="sxs-lookup"><span data-stu-id="c99db-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="c99db-109">Obtient le module qui définit cette classe.</span><span class="sxs-lookup"><span data-stu-id="c99db-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="c99db-110">GetStaticFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="c99db-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="c99db-111">Obtient la valeur du champ statique spécifié.</span><span class="sxs-lookup"><span data-stu-id="c99db-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="c99db-112">GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="c99db-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="c99db-113">Obtient le `TypeDef` jeton de métadonnées pour cette classe.</span><span class="sxs-lookup"><span data-stu-id="c99db-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c99db-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="c99db-114">Remarks</span></span>  
 <span data-ttu-id="c99db-115">Le `ICorDebugClass` interface représente un type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="c99db-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="c99db-116">L’interface ICorDebugType représente un type générique instancié.</span><span class="sxs-lookup"><span data-stu-id="c99db-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="c99db-117">Par exemple, `Hashtable<K, V>` serait représenté par `ICorDebugClass`, alors que `Hashtable<Int32, String>` serait représenté par `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="c99db-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="c99db-118">Les types non génériques sont représentés par les deux `ICorDebugClass` et `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="c99db-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="c99db-119">Cette dernière interface a été introduite dans le .NET Framework version 2.0 pour gérer l’instanciation de type.</span><span class="sxs-lookup"><span data-stu-id="c99db-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c99db-120">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="c99db-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c99db-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c99db-121">Requirements</span></span>  
 <span data-ttu-id="c99db-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c99db-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c99db-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c99db-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c99db-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c99db-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c99db-125">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c99db-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c99db-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c99db-126">See Also</span></span>  
 [<span data-ttu-id="c99db-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c99db-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)