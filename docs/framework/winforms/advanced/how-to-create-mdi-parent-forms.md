---
title: 'Procédure : Créer des formulaires MDI parents'
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: 1cc3d813b77ddf8220242f4a1dfc7fe39f9cb520
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512565"
---
# <a name="how-to-create-mdi-parent-forms"></a>Procédure : Créer des formulaires MDI parents
> [!IMPORTANT]
>  Cette rubrique utilise le contrôle <xref:System.Windows.Forms.MainMenu>, qui a été remplacé par le contrôle <xref:System.Windows.Forms.MenuStrip>. Le contrôle <xref:System.Windows.Forms.MainMenu> est conservé pour la compatibilité descendante et une utilisation future, au besoin.  Pour plus d’informations sur la création d’une MDI du formulaire parent en utilisant un <xref:System.Windows.Forms.MenuStrip>, consultez [Comment : Créer une liste des fenêtres MDI avec MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).  
  
 Le formulaire MDI parent constitue la base d'une application d'interface multidocument (MDI, Multiple-Document Interface). Ce formulaire contient les fenêtres MDI enfants, c'est-à-dire les sous-fenêtres dans lesquelles l'utilisateur interagit avec l'application MDI. Il est facile de créer un formulaire MDI parent, que ce soit par programmation ou dans le Concepteur Windows Forms.  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a>Pour créer un formulaire MDI parent au moment du design  
  
1.  Créez un projet d'application Windows.  
  
2.  Dans le **propriétés** fenêtre, définissez la <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriété **true**.  
  
     Ainsi, vous désignez le formulaire comme le conteneur MDI des fenêtres enfants.  
  
    > [!NOTE]
    >  Quand vous définissez des propriétés dans la fenêtre **Propriétés**, vous pouvez aussi si vous le souhaitez définir la propriété `WindowState` sur **Maximized**, car il est plus facile de manipuler des fenêtres enfants MDI quand le formulaire parent est agrandi au maximum. Sachez par ailleurs que le contour du formulaire MDI parent prend la couleur système (définie dans le Panneau de configuration Système Windows), et non la couleur d’arrière-plan que vous avez définie avec la propriété <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType>.  
  
3.  Dans la **Boîte à outils**, faites glisser un contrôle **MenuStrip** sur le formulaire. Créez un élément de menu de plus haut niveau en définissant la propriété **Text** sur **&File** avec des éléments de sous-menu appelés **&New** et **&Close**. Créez également un menu de plus haut niveau appelé **&Window**.  
  
     Le premier menu crée et masque les éléments de menu au moment de l'exécution, alors que le deuxième menu garde la trace des fenêtres MDI enfants ouvertes. À ce stade, vous avez créé une fenêtre MDI parente.  
  
4.  Appuyez sur **F5** pour exécuter l’application. Pour plus d’informations sur la création d’enfant MDI windows qui fonctionnent dans un formulaire MDI parent, consultez [Comment : Créer des formulaires enfants MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).  
  
## <a name="see-also"></a>Voir aussi
- [Applications d’interface multidocument (MDI, Multiple Document Interface)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)
- [Guide pratique pour Créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [Guide pratique pour Déterminer l’enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)
- [Guide pratique pour Envoyer des données à l’enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
- [Guide pratique pour Réorganiser des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
