---
title: "WriteableMetadataUpdateMode, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: WriteableMetadataUpdateMode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 001d80a2232f5b6fbfb43b9de5deafb3317e426d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="75f44-102">WriteableMetadataUpdateMode, énumération</span><span class="sxs-lookup"><span data-stu-id="75f44-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="75f44-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="75f44-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="75f44-104">Fournit des valeurs qui spécifient si les mises à jour en mémoire apportées aux métadonnées sont visibles par un débogueur.</span><span class="sxs-lookup"><span data-stu-id="75f44-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f44-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75f44-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="75f44-106">Membres</span><span class="sxs-lookup"><span data-stu-id="75f44-106">Members</span></span>  
  
|<span data-ttu-id="75f44-107">Nom de membre</span><span class="sxs-lookup"><span data-stu-id="75f44-107">Member name</span></span>|<span data-ttu-id="75f44-108">Description</span><span class="sxs-lookup"><span data-stu-id="75f44-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="75f44-109">Maintient la compatibilité avec les versions antérieures de .NET Framework lors de la mise à jour en mémoire de métadonnées visibles.</span><span class="sxs-lookup"><span data-stu-id="75f44-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="75f44-110">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="75f44-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="75f44-111">Rend les mises à jour en mémoire apportées aux métadonnées visibles par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="75f44-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75f44-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="75f44-112">Remarks</span></span>  
 <span data-ttu-id="75f44-113">Un membre de la `WriteableMetadataUpdateMode` énumération peut être passée à la [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) méthode pour contrôler si en mémoire des mises à jour aux métadonnées dans le processus cible sont visibles par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="75f44-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="75f44-114">L'option `LegacyCompatPolicy` force le même comportement que dans les versions de .NET Framework antérieures à 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="75f44-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="75f44-115">Cela signifie souvent que les métadonnées provenant des mises à jour ne sont pas visibles.</span><span class="sxs-lookup"><span data-stu-id="75f44-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="75f44-116">Cependant, les appels à certaines méthodes de débogage forcent implicitement le débogueur à rendre visibles les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="75f44-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="75f44-117">Par exemple, si le débogueur passe [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) l’index d’une variable introuvable dans les métadonnées d’origine de la méthode, toutes les métadonnées pour le module est mis à jour d’un instantané correspondant à l’état actuel de la processus.</span><span class="sxs-lookup"><span data-stu-id="75f44-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="75f44-118">En d'autres termes, avec l'option `LegacyCompatPolicy`, le débogueur peut voir aucune, certaines ou toutes les mises à jour des métadonnées disponibles, selon la façon dont il utilise les autres parties de l'API de débogage non managée.</span><span class="sxs-lookup"><span data-stu-id="75f44-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75f44-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="75f44-119">Requirements</span></span>  
 <span data-ttu-id="75f44-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75f44-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75f44-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75f44-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75f44-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75f44-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75f44-123">**Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75f44-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f44-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75f44-124">See Also</span></span>  
 [<span data-ttu-id="75f44-125">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="75f44-125">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="75f44-126">Setwriteablemetadataupdatemode, méthode</span><span class="sxs-lookup"><span data-stu-id="75f44-126">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)