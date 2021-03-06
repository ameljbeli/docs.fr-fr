---
title: 'Procédure : Lier le contrôle DataGrid Windows Forms à une Source de données à l’aide du Concepteur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: 414c989d258ca4b7a9097afa2b7f2407505fb629
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687581"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Procédure : Lier le contrôle DataGrid Windows Forms à une Source de données à l’aide du Concepteur

> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Les formulaires Windows <xref:System.Windows.Forms.DataGrid> contrôle est spécifiquement conçu pour afficher des informations à partir d’une source de données. Vous liez le contrôle au moment du design en définissant le <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriétés, ou en cours d’exécution en appelant le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (méthode). Bien que vous pouvez afficher des données à partir de diverses sources de données, les sources les plus courantes sont les vues de données et des jeux de données.  
  
 Si la source de données est disponible au moment du design, par exemple, si le formulaire contient une instance d’un jeu de données ou une vue de données, vous pouvez lier la grille à la source de données au moment du design. Vous pouvez ensuite afficher un aperçu l’aspect qu’aura les données dans la grille.  
  
 Vous pouvez également lier la grille par programmation, en cours d’exécution. Cela est utile lorsque vous souhaitez définir une source de données basée sur les informations que vous obtenez en cours d’exécution. Par exemple, l’application peut permettre l’utilisateur à spécifier le nom d’une table à afficher. Il est également nécessaire dans les situations où la source de données n’existe pas au moment du design. Cela inclut les sources de données telles que les tableaux, les collections, les datasets non typés et les lecteurs de données.  
  
 La procédure suivante nécessite un **Windows Application** projet avec un formulaire contenant un <xref:System.Windows.Forms.DataGrid> contrôle. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : Créer un projet d’Application Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : Ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Dans Visual Studio 2005, le <xref:System.Windows.Forms.DataGrid> contrôle n’est pas dans le **boîte à outils** par défaut. Pour plus d’informations sur son ajout, consultez [Comment : Ajouter des éléments à la boîte à outils](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0). En outre dans Visual Studio 2005, vous pouvez utiliser la **des Sources de données** fenêtre pour la liaison de données au moment du design. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Lier aux données du contrôle DataGrid à une seule table dans le Concepteur  
  
1.  Définir le contrôle <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété à l’objet qui contient les éléments de données que vous souhaitez établir une liaison.  
  
2.  Si la source de données est un jeu de données, définissez la <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriété le nom de la table à lier.  
  
3.  Si la source de données est un jeu de données ou une vue de données basée sur une table de dataset, ajoutez le code au formulaire pour remplir le dataset.  
  
     Le code exact que vous utilisez dépend où le jeu de données est l’obtention de données. Si le jeu de données est rempli directement à partir d’une base de données, vous appelez généralement la `Fill` méthode d’un adaptateur de données, comme dans l’exemple de code suivant, qui remplit un dataset nommé `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  (Facultatif) Ajouter les styles de table approprié et les styles de colonne à la grille.  
  
     S’il n’y a aucun style de tableau, vous verrez la table, mais avec la mise en forme minimale et toutes les colonnes visibles.  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Lier aux données du contrôle DataGrid à plusieurs tables dans un jeu de données dans le Concepteur  
  
1.  Définir le contrôle <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété à l’objet qui contient les éléments de données que vous souhaitez établir une liaison.  
  
2.  Si le jeu de données contient des tables connexes (autrement dit, si elle contient un objet de relation), définissez le <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriété le nom de la table parente.  
  
3.  Écrire du code pour remplir le dataset.  
  
## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du contrôle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)
- [Guide pratique pour Ajouter des Tables et des colonnes au contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)
- [Accès aux données dans Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
