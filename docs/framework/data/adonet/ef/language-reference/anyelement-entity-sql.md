---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 16dbccf66413776af73f0b84463f9a56d2cee360
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624117"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)
Extrait un élément d'une collection à valeurs multiples.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression de requête valide qui retourne une collection dont extraire un élément.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément unique de la collection ou élément arbitraire si la collection en comporte plusieurs ; si la collection est vide, retourne `null`. Si `collection` est une collection de type `Collection<T>`, puis `ANYELEMENT(collection)` est une expression valide qui produit une instance de type `T`.  
  
## <a name="remarks"></a>Notes  
 ANYELEMENT extrait un élément arbitraire d'une collection à valeurs multiples. L'exemple ci-dessous tente d'extraire un élément singleton du jeu `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur ANYELEMENT pour extraire un élément d'une collection à valeurs multiples. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure décrite dans [Comment : Exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Voir aussi
- [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Types structurés autorisant la valeur null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
