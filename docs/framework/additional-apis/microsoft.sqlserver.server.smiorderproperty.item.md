---
title: Propriété SmiOrderProperty.Item (Microsoft.SqlServer.Server)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 5453167e16e2658b3546b7114201b04d481a0c79
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223004"
---
# <a name="smiorderpropertyitem-property"></a>Propriété de SmiOrderProperty.Item

Obtient l’ordre des colonnes pour l’entité. L’assembly qui contient cette propriété a une relation de friend avec SQLAccess.dll. Il est prévu pour une utilisation par SQL Server. Pour les autres bases de données, utilisez le mécanisme d’hébergement fourni par cette base de données.

## <a name="syntax"></a>Syntaxe

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a>Valeur de propriété

L’ordre des colonnes.

## <a name="remarks"></a>Notes

> [!WARNING]
> Le `SmiOrderProperty.Item` propriété est interne et n’est pas destinée à être utilisé directement dans votre code.
>
> Microsoft ne prend pas en charge l’utilisation de cette propriété dans une application de production en toute circonstance.

## <a name="requirements"></a>Spécifications

**Espace de noms :** <xref:Microsoft.SqlServer.Server>

**Assembly :** System.Data (dans System.Data.dll)

**Versions du .NET framework :** Disponible à partir de 2.0.