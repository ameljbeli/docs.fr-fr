---
title: Responsabilités du développeur en matière de substitution du comportement par défaut
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 4773d4d5cf8192dfa1f8bfad6b5846c03ab1d2c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555620"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Responsabilités du développeur en matière de substitution du comportement par défaut
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] n’applique pas les exigences suivantes, mais le comportement est indéfini si ces conditions ne sont pas satisfaites.  
  
-   La méthode de substitution ne doit pas appeler <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ou <xref:System.Data.Linq.Table%601.Attach%2A>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lève une exception si ces méthodes sont appelées dans une méthode override.  
  
-   Les méthodes override ne peuvent pas être utilisées pour démarrer, valider ou arrêter une transaction. L'opération <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est effectuée dans le cadre d'une transaction. Une transaction imbriquée interne peut interférer avec la transaction externe. Les méthodes override de charge peuvent démarrer une transaction uniquement après avoir déterminé que l'opération n'est pas effectuée dans un <xref:System.Transactions.Transaction>.  
  
-   Les méthodes override sont supposées suivre le mappage d'accès concurrentiel optimiste applicable. La méthode override est supposée lever un <xref:System.Data.Linq.ChangeConflictException> lorsqu'un conflit d'accès concurrentiel optimiste se produit. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] intercepte cette exception afin que vous puissiez traiter correctement le <xref:System.Data.Linq.DataContext.SubmitChanges%2A> option fournie sur <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Les méthodes override de création (`Insert`) et `Update` sont supposées renvoyer les valeurs des colonnes générées par une base de données aux membres d'objet correspondants lorsque l'opération réussit.  
  
     Par exemple, si `Order.OrderID` est mappé à une colonne d’identité (*autoincrement* clé primaire), puis le `InsertOrder()` méthode de substitution doit récupérer l’ID de base de données et définissez la `Order.OrderID` membre à cet ID. De la même façon, les membres d'horodatage doivent être mis à jour aux valeurs d'horodatage générées par une base de données afin de vérifier que les objets mis à jour sont cohérents. Si les valeurs générées par une base de données ne peuvent pas être propagées, cela peut entraîner une incohérence entre la base de données et les objets suivis par le <xref:System.Data.Linq.DataContext>.  
  
-   L'utilisateur doit appeler l'API dynamique appropriée. Par exemple, dans la méthode override de mise à jour, seule la méthode <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> peut être appelée. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne détecte pas ni ne vérifie si la méthode dynamique appelée correspond à l'opération applicable. Les résultats ne sont pas définis si une méthode inapplicable est appelée (par exemple, <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> pour un objet à mettre à jour).  
  
-   Enfin, la méthode de substitution est supposée effectuer l'opération énoncée. La sémantique des opérations [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] telles que le chargement hâtif, le chargement différé et <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nécessitent que les substitutions fournissent le service indiqué. Par exemple, si une substitution de charge retourne simplement une collection vide sans vérifier le contenu dans la base de données, cela peut entraîner des incohérences au niveau des données.  
  
## <a name="see-also"></a>Voir aussi
- [Personnalisation des opérations d’insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
