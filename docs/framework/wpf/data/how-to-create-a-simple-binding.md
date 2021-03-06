---
title: 'Procédure : Créer une liaison simple'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 3e38fa5fd1c7d0a635efd93de6ebe551f1eb1b82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594835"
---
# <a name="how-to-create-a-simple-binding"></a>Procédure : Créer une liaison simple
Cet exemple vous montre comment créer un simple <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, vous avez un `Person` objet avec une propriété de chaîne nommée `PersonName`. Le `Person` objet est défini dans l’espace de noms appelé `SDKSample`.  
  
 La ligne en surbrillance qui contient le `<src>` élément dans l’exemple suivant instancie le `Person` de l’objet avec un `PersonName` valeur de propriété `Joe`. Cette opération est effectuée le `Resources` section et affecté un `x:Key`.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 La ligne en surbrillance qui contient le `<TextBlock>` élément lie ensuite le <xref:System.Windows.Controls.TextBlock> le contrôle à la `PersonName` propriété. Par conséquent, le <xref:System.Windows.Controls.TextBlock> apparaît avec la valeur « Joe ».  
  
## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
