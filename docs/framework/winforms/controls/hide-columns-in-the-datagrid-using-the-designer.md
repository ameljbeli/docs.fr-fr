---
title: 'Procédure : Masquer des colonnes dans le contrôle de DataGridView Windows Forms à l’aide du Concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: 77aa5614d185a80c1f70ec5afad57834cff003d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517810"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Procédure : Masquer des colonnes dans le contrôle de DataGridView Windows Forms à l’aide du Concepteur
Parfois, vous souhaiterez afficher uniquement quelques-unes des colonnes qui sont disponibles dans un contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms. Par exemple, vous souhaitez afficher un employé colonne salaire aux utilisateurs avec les informations d’identification de gestion tout en la masquant d’autres utilisateurs. Ou bien, vous souhaiterez lier le contrôle à une source de données qui contient de nombreuses colonnes, que seuls certains d'entre eux vous souhaitez afficher. Dans ce cas, vous supprimerez en général les colonnes que vous n’êtes pas intéressé à afficher plutôt que de les masquer. Pour plus d'informations, voir [Procédure : Ajouter et supprimer des colonnes dans les Windows Forms DataGridView Control à l’aide du concepteur](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
 La procédure suivante nécessite un **Windows Application** projet avec un formulaire contenant un <xref:System.Windows.Forms.DataGridView> contrôle. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : Créer un projet d’Application Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : Ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-hide-a-column-using-the-designer"></a>Pour masquer une colonne à l’aide du Concepteur  
  
1.  Cliquez sur le glyphe de balise active (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le coin supérieur droit de la <xref:System.Windows.Forms.DataGridView> contrôler, puis sélectionnez **modifier les colonnes**.  
  
2.  Sélectionnez une colonne dans la **colonnes sélectionnées** liste.  
  
3.  Dans le **propriétés de la colonne** grille, définissez la <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> propriété `false`.  
  
    > [!NOTE]
    >  Vous pouvez également masquer une colonne lors de son ajout en désactivant le **Visible** case à cocher dans la **ajouter une colonne** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Guide pratique pour Ajouter et supprimer des colonnes dans le contrôle de DataGridView Windows Forms à l’aide du Concepteur](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Guide pratique pour créer un projet d’application Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)
- [Guide pratique pour Ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
