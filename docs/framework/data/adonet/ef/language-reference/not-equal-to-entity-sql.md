---
title: '!= (différent de) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: d5e59fe61dbc05a48e98f5720dca446482b9968e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568130"
---
# <a name="-not-equal-to-entity-sql"></a>!= (différent de) (Entity SQL)
Compare deux expressions pour déterminer si l'expression de gauche est différente de l'expression de droite. L'opérateur != (différent de) est d'un point de vue fonctionnel équivalent à l'opérateur <>.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression valide. Les deux expressions doivent posséder des types de données implicitement convertibles.  
  
## <a name="result-types"></a>Types de résultats  
 `true` si l'expression de gauche est différente de l'expression de droite ; sinon, `false`.  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise l'opérateur != pour comparer deux expressions afin de déterminer si l'expression de gauche est différente de l'expression de droite. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1.  Suivez la procédure décrite dans [Comment : Exécuter une requête qui retourne des résultats StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a>Voir aussi
- [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
