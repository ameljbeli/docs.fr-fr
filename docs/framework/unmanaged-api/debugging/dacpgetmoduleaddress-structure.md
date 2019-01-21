---
title: DacpGetModuleAddress Structure
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ca9ce04e9a4770d46f88e10785f4dafd044c9212
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416391"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="93c5f-102">DacpGetModuleAddress Structure</span><span class="sxs-lookup"><span data-stu-id="93c5f-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="93c5f-103">Définit le conteneur pour une demande d’adresse de module.</span><span class="sxs-lookup"><span data-stu-id="93c5f-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="93c5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93c5f-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="93c5f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="93c5f-105">Members</span></span>

| <span data-ttu-id="93c5f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="93c5f-106">Member</span></span>      | <span data-ttu-id="93c5f-107">Description</span><span class="sxs-lookup"><span data-stu-id="93c5f-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="93c5f-108">Pointeur vers le module.</span><span class="sxs-lookup"><span data-stu-id="93c5f-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="93c5f-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="93c5f-109">Methods</span></span>

| <span data-ttu-id="93c5f-110">Méthode</span><span class="sxs-lookup"><span data-stu-id="93c5f-110">Method</span></span>                                                                                               | <span data-ttu-id="93c5f-111">Description</span><span class="sxs-lookup"><span data-stu-id="93c5f-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="93c5f-112">Requête</span><span class="sxs-lookup"><span data-stu-id="93c5f-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="93c5f-113">Exécute une requête pour remplir la structure à partir de la structure de runtime donné.</span><span class="sxs-lookup"><span data-stu-id="93c5f-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="93c5f-114">Notes</span><span class="sxs-lookup"><span data-stu-id="93c5f-114">Remarks</span></span>

<span data-ttu-id="93c5f-115">Cette structure se trouve au sein du runtime et n’est pas exposée par le biais d’en-têtes ou les fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="93c5f-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="93c5f-116">Pour l’utiliser, définir la structure comme indiqué ci-dessus, où `CLRDATA_ADDRESS` est un entier non signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="93c5f-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="93c5f-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="93c5f-117">Requirements</span></span>
<span data-ttu-id="93c5f-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93c5f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="93c5f-119">**En-tête :** Aucun.</span><span class="sxs-lookup"><span data-stu-id="93c5f-119">**Header:** None</span></span>  
<span data-ttu-id="93c5f-120">**Bibliothèque :** Aucun.</span><span class="sxs-lookup"><span data-stu-id="93c5f-120">**Library:** None</span></span>  
<span data-ttu-id="93c5f-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="93c5f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="93c5f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93c5f-122">See Also</span></span>
- [<span data-ttu-id="93c5f-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="93c5f-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="93c5f-124">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="93c5f-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)