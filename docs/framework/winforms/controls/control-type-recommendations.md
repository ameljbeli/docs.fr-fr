---
title: Recommandations relatives au type du contrôle
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: 5e3337dddcc39517558cf85af76223306d20d2bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599697"
---
# <a name="control-type-recommendations"></a>Recommandations relatives au type du contrôle
.NET Framework vous offre la possibilité de développer et d'implémenter de nouveaux contrôles. Outre le contrôle utilisateur familier, vous constaterez que vous pouvez désormais écrire des contrôles personnalisés qui effectuent leur propre peinture et même étendre les fonctionnalités des contrôles existants via l'héritage. Le choix du type de contrôle à créer peut être délicat. Cette section souligne les différences entre les différents types de contrôles à partir desquels vous pouvez hériter et fournit des conseils quant au type le plus adapté à votre projet.  
  
> [!NOTE]
>  Si vous souhaitez créer un contrôle à utiliser sur des Web Forms, consultez [Développement de contrôles serveur ASP.NET personnalisés](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Héritage d'un contrôle Windows Forms  
 Vous pouvez dériver un contrôle hérité à partir de n'importe quel contrôle Windows Forms existant. Cette approche vous permet de conserver toutes les fonctionnalités inhérentes d'un contrôle Windows Forms et de les étendre en y ajoutant des propriétés ou des méthodes personnalisées ou d'autres fonctionnalités. Par exemple, vous pouvez créer un contrôle dérivé de <xref:System.Windows.Forms.TextBox> qui accepte uniquement les nombres et convertit automatiquement l'entrée en une valeur. Ce genre de contrôle peut contenir du code de validation appelé chaque fois que le texte dans la zone de texte change et peut avoir une propriété supplémentaire, Valeur. Dans certains contrôles, vous pouvez également ajouter une apparence personnalisée à l'interface graphique de votre contrôle en substituant la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe de base.  
  
 Héritez d'un contrôle Windows Forms si :  
  
-   la plupart des fonctionnalités dont vous avez besoin sont déjà identiques à un contrôle Windows Forms existant ;  
  
-   vous n'avez pas besoin d'une interface graphique personnalisée ou vous souhaitez concevoir une nouvelle interface graphique frontale pour un contrôle existant.  
  
## <a name="inheriting-from-the-usercontrol-class"></a>Héritage de la classe UserControl  
 Un contrôle utilisateur est une collection de contrôles Windows Forms encapsulés dans un conteneur commun. Le conteneur contient toutes les fonctionnalités inhérentes associées à chacun des contrôles Windows Forms et vous permet d'exposer et de lier leurs propriétés de manière sélective. En guise d'exemple de contrôle utilisateur, vous pourriez avoir un contrôle conçu pour afficher des données d'adresses de clients à partir d'une base de données. Ce contrôle contiendrait plusieurs zones de texte pour afficher chaque champ et des contrôles de bouton pour parcourir les enregistrements. Les propriétés de liaison de données pourraient être exposées de manière sélective et l'ensemble du contrôle pourrait être empaqueté et réutilisé d'une application à l'autre.  
  
 Héritez de la classe <xref:System.Windows.Forms.UserControl> si :  
  
-   vous souhaitez combiner les fonctionnalités de plusieurs contrôles Windows Forms dans une même entité réutilisable.  
  
## <a name="inheriting-from-the-control-class"></a>Héritage de la classe Contrôle  
 Une autre façon de créer un contrôle consiste à en créer un tout nouveau en héritant de <xref:System.Windows.Forms.Control>. La classe <xref:System.Windows.Forms.Control> fournit toutes les fonctionnalités de base requises par les contrôles (par exemple des événements), mais aucune fonctionnalité ou interface graphique spécifique. La création d'un contrôle en héritant de la classe <xref:System.Windows.Forms.Control> nécessite beaucoup plus de réflexion et d'efforts que l'héritage d'un contrôle utilisateur ou d'un contrôle Windows Forms existant. Vous devez écrire du code pour l'événement <xref:System.Windows.Forms.Control.OnPaint%2A> du contrôle, ainsi que tout code spécifique aux fonctionnalités nécessaires. Vous bénéficiez toutefois d'une plus grande souplesse et vous pouvez personnaliser le contrôle en fonction de vos besoins exacts. En guise d'exemple de contrôle personnalisé, vous pourriez avoir un contrôle d'horloge imitant l'apparence et l'action d'une horloge analogique. La peinture personnalisée serait appelée pour déclencher le déplacement des aiguilles de l'horloge en réponse aux événements <xref:System.Windows.Forms.Timer.Tick> d'un composant d'horloge interne.  
  
 Héritez de la classe <xref:System.Windows.Forms.Control> si :  
  
-   vous souhaitez fournir une représentation graphique personnalisée de votre contrôle ;  
  
-   vous devez implémenter des fonctionnalités personnalisées qui ne sont pas disponible via les contrôles standard.  
  
-   [Guide pratique pour Afficher un contrôle dans la boîte de dialogue de boîte à outils éléments choisir](https://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [Procédure pas à pas : Sérialisation des Collections de Types Standard avec DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [Procédure pas à pas : Héritage d’un contrôle de formulaire Windows avec VisualC#](https://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))  
  
-   [Guide pratique pour Fournir une Bitmap de boîte à outils pour un contrôle](https://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [Guide pratique pour Windows existant hériter de contrôles de formulaires](https://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [Procédure pas à pas : Débogage des contrôles Windows Forms personnalisés au moment du design](https://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [Guide pratique pour Héritez de la classe de contrôle](https://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [Guide pratique pour Tester le comportement au moment de l’exécution d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [Guide pratique pour Aligner un contrôle sur les bords des formulaires au moment du Design](https://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [Guide pratique pour Hériter de la classe UserControl](https://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [Guide pratique pour Créer des contrôles pour les Windows Forms](https://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [Guide pratique pour Créer des contrôles composites](https://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [Procédure pas à pas : Création d’un contrôle Composite avec Visual Basic](https://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [Procédure pas à pas : Création d’un contrôle Composite avec VisualC#](https://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))  
  
-   [Procédure pas à pas : Héritage d’un contrôle de formulaire Windows avec Visual Basic](https://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [Guide pratique pour Créer un contrôle Windows Forms tire parti des fonctionnalités de conception](https://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [Guide pratique pour Créer un contrôle Windows Forms tire parti des fonctionnalités de conception](https://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Développer un contrôle de formulaires Windows Simple](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)
- [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
