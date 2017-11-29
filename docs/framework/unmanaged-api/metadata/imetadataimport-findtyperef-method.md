---
title: "IMetaDataImport::FindTypeRef, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d742033788e270f01ee0cea70569ca65e7f35697
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="fcbaa-102">IMetaDataImport::FindTypeRef, méthode</span><span class="sxs-lookup"><span data-stu-id="fcbaa-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="fcbaa-103">Obtient un pointeur vers le jeton TypeRef pour la <xref:System.Type> référence qui se trouve dans l’étendue spécifiée et qui porte le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="fcbaa-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcbaa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcbaa-104">Syntax</span></span>  
  
```  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fcbaa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fcbaa-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="fcbaa-106">[in] Un jeton ModuleRef, AssemblyRef ou TypeRef qui spécifie le type, un assembly ou un module, respectivement, dans laquelle la référence de type est défini.</span><span class="sxs-lookup"><span data-stu-id="fcbaa-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="fcbaa-107">[in] Le nom de la référence de type à rechercher.</span><span class="sxs-lookup"><span data-stu-id="fcbaa-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="fcbaa-108">[out] Pointeur vers le jeton TypeRef correspondant.</span><span class="sxs-lookup"><span data-stu-id="fcbaa-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcbaa-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fcbaa-109">Requirements</span></span>  
 <span data-ttu-id="fcbaa-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcbaa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcbaa-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fcbaa-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fcbaa-112">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fcbaa-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fcbaa-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcbaa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbaa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcbaa-114">See Also</span></span>  
 [<span data-ttu-id="fcbaa-115">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="fcbaa-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fcbaa-116">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="fcbaa-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)