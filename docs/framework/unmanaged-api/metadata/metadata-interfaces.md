---
title: "Interfaces de métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 638727dae1f0f32e5c92c0da7513719bd11ae8d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-interfaces"></a><span data-ttu-id="aabcf-102">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="aabcf-102">Metadata Interfaces</span></span>
<span data-ttu-id="aabcf-103">Cette section décrit les interfaces non managées qui donnent accès aux métadonnées exposées par les types, méthodes, champs, etc. du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aabcf-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aabcf-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="aabcf-104">In This Section</span></span>  
 [<span data-ttu-id="aabcf-105">ICeeGen (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="aabcf-106">Fournit des méthodes pour la compilation de code dynamique.</span><span class="sxs-lookup"><span data-stu-id="aabcf-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="aabcf-107">IHostFilter (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="aabcf-108">Fournit une méthode permettant à l'hôte du runtime de marquer des jetons de métadonnées à traiter.</span><span class="sxs-lookup"><span data-stu-id="aabcf-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="aabcf-109">IMapToken (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="aabcf-110">Fournit des fonctionnalités de mappage entre des signatures de métadonnées importées et émises.</span><span class="sxs-lookup"><span data-stu-id="aabcf-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="aabcf-111">IMetaDataAssemblyEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="aabcf-112">Fournit des méthodes qui prennent en charge le modèle d'autodescription utilisé par le Common Language Runtime (CLR) pour résoudre et consommer des ressources.</span><span class="sxs-lookup"><span data-stu-id="aabcf-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="aabcf-113">IMetaDataAssemblyImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="aabcf-114">Fournit des méthodes pour accéder au contenu d'un manifeste d'assembly et l'examiner.</span><span class="sxs-lookup"><span data-stu-id="aabcf-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="aabcf-115">IMetaDataConverter (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="aabcf-116">Fournit des méthodes pour mapper des bibliothèques de types à leurs signatures de métadonnées et effectuer la conversion entre les deux.</span><span class="sxs-lookup"><span data-stu-id="aabcf-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="aabcf-117">IMetaDataDispenser (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="aabcf-118">`IMetaDataDispenser` est obsolète.</span><span class="sxs-lookup"><span data-stu-id="aabcf-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="aabcf-119">Utilisez plutôt `IMetaDataDispenserEx` .</span><span class="sxs-lookup"><span data-stu-id="aabcf-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="aabcf-120">IMetaDataDispenserEx (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="aabcf-121">Fournit des méthodes qui mappent des zones de mémoire pour créer ou modifier des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="aabcf-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="aabcf-122">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="aabcf-123">Fournit des méthodes pour créer, modifier et stocker les métadonnées sur l'assembly dans la portée actuellement définie.</span><span class="sxs-lookup"><span data-stu-id="aabcf-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="aabcf-124">IMetaDataEmit2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="aabcf-125">Fournit des méthodes pour définir et modifier les signatures de métadonnées de méthodes et de constructeurs avec les paramètres de type <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aabcf-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="aabcf-126">IMetaDataError (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="aabcf-127">Fournit un mécanisme de rappel pour signaler les erreurs pendant la résolution de la signature de métadonnées d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="aabcf-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="aabcf-128">IMetaDataFilter (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="aabcf-129">Fournit des méthodes pour marquer et filtrer des jetons de métadonnées pour éviter de répéter des actions qui ont déjà été prises.</span><span class="sxs-lookup"><span data-stu-id="aabcf-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="aabcf-130">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="aabcf-131">Fournit des méthodes pour importer et manipuler des types provenant d'autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="aabcf-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="aabcf-132">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="aabcf-133">Étend `IMetaDataImport` pour permettre d'utiliser des types génériques.</span><span class="sxs-lookup"><span data-stu-id="aabcf-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="aabcf-134">IMetaDataInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="aabcf-135">Fournit une méthode qui obtient des informations sur le mappage de métadonnées à partir d'un fichier sur disque dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="aabcf-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="aabcf-136">IMetaDataTables (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="aabcf-137">Fournit des méthodes pour le stockage et la récupération d'informations de métadonnées dans des tables.</span><span class="sxs-lookup"><span data-stu-id="aabcf-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="aabcf-138">IMetaDataTables2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="aabcf-139">Étend `IMetaDataTables` pour inclure des méthodes permettant d'utiliser des flux de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="aabcf-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="aabcf-140">IMetaDataValidate (Interface)</span><span class="sxs-lookup"><span data-stu-id="aabcf-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="aabcf-141">Fournit des méthodes à utiliser pour la validation des signatures de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="aabcf-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aabcf-142">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="aabcf-142">Related Sections</span></span>  
 [<span data-ttu-id="aabcf-143">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="aabcf-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="aabcf-144">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="aabcf-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="aabcf-145">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="aabcf-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="aabcf-146">Unions de métadonnées</span><span class="sxs-lookup"><span data-stu-id="aabcf-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)