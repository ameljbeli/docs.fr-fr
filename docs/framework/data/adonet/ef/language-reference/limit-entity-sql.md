---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 3c38fd3fc20ad19bdeeca5c02c25de6c8269def6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493818"
---
# <a name="limit-entity-sql"></a>LIMIT (Entity SQL)
Une pagination physique peut être effectuée par le biais de la sous-clause LIMIT de la clause ORDER BY. La sous-clause LIMIT ne peut pas être utilisée sans la clause ORDER BY.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Nombre d'éléments qui seront sélectionnés.  
  
 Si une sous-clause d'expression LIMIT est présente dans une clause ORDER BY, la requête sera triée en fonction de la spécification de classement et le nombre de lignes obtenu sera limité par l'expression LIMIT. Par exemple, LIMIT 5 limitera le jeu de résultats à 5 instances ou lignes. LIMIT est d'un point de vue fonctionnel équivalent à TOP, sauf que LIMIT a besoin de la présence de la clause ORDER BY. SKIP et LIMIT peuvent être utilisés indépendamment avec la clause ORDER BY.  
  
> [!NOTE]
>  Une requête Entity SQL est considérée comme non valide si le modificateur TOP et la sous-clause SKIP se trouvent dans une même expression de requête. La requête doit être réécrite en remplaçant l'expression TOP par l'expression LIMIT.  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL suivante utilise l'opérateur ORDER BY avec LIMIT pour spécifier l'ordre de classement employé sur les objets retournés dans une instruction SELECT. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure décrite dans [Comment : Exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a>Voir aussi
- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Guide pratique pour Parcourir les résultats de la requête](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
- [Pagination](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
