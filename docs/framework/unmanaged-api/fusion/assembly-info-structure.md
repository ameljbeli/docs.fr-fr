---
title: ASSEMBLY_INFO, structure
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b69aa42fc2ebb9f59cbf699d83b521704805ea5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519747"
---
# <a name="assemblyinfo-structure"></a>ASSEMBLY_INFO, structure
Contient des informations relatives à un assembly qui est enregistré dans le global assembly cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`cbAssemblyInfo`|La taille, en octets, de la structure. Ce champ est réservé pour une extensibilité future.|  
|`dwAssemblyFlags`|Indicateurs qui indiquent les détails de l’installation sur l’assembly. Les valeurs suivantes sont prises en charge :<br /><br /> -La valeur ASSEMBLYINFO_FLAG_INSTALLED, ce qui indique que l’assembly est installé. La version actuelle du .NET Framework définit toujours `dwAssemblyFlags` à cette valeur.<br />-La valeur ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, ce qui indique que l’assembly est une charge utile résidente. La version actuelle du .NET Framework définit jamais `dwAssemblyFlags` à cette valeur.|  
|`uliAssemblySizeInKB`|La taille totale, en kilo-octets, des fichiers qui contient l’assembly.|  
|`pszCurrentAssemblyPathBuf`|Pointeur vers une mémoire tampon de chaîne qui contient le chemin d’accès actuel dans le fichier manifeste. Le chemin d’accès doit se terminer par un caractère null.|  
|`cchBuf`|Le nombre de caractères larges, y compris le terminateur null, qui `pszCurrentAssemblyPathBuf` contient.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
- [Structures de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [Global Assembly Cache](../../../../docs/framework/app-domains/gac.md)
