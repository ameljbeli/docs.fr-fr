---
title: 'Procédure : Créer du texte avec contour'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: a06ef9adbd5740fee74be2e9d8d13a8a5bdc5b95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521476"
---
# <a name="how-to-create-outlined-text"></a>Procédure : Créer du texte avec contour
Dans la plupart des cas, lorsque vous ajoutez ornementation élaborée pour les chaînes de texte dans votre [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, à l’aide de texte en termes d’une collection de caractères discrets, ou glyphes. Par exemple, Impossible de créer un pinceau dégradé linéaire et de l’appliquer à la <xref:System.Windows.Controls.Control.Foreground%2A> propriété d’un <xref:System.Windows.Controls.TextBox> objet. Lorsque vous affichez ou modifiez la zone de texte, le pinceau de dégradé linéaire est automatiquement appliqué à l’ensemble actuel de caractères dans la chaîne de texte.  
  
 ![Texte affiché avec un pinceau dégradé linéaire](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")  
Exemple d’un pinceau de dégradé linéaire appliqué à une zone de texte  
  
 Toutefois, vous pouvez également convertir le texte en <xref:System.Windows.Media.Geometry> objets, ce qui vous permet de créer d’autres types de texte visuellement enrichi. Par exemple, vous pouvez créer un <xref:System.Windows.Media.Geometry> objet basé sur le contour d’une chaîne de texte.  
  
 ![Contour du texte à l’aide d’un pinceau dégradé linéaire](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Exemple d’un pinceau de dégradé linéaire appliqué à la géométrie de contour du texte  
  
 Lorsque le texte est converti en un <xref:System.Windows.Media.Geometry> de l’objet, il n’est plus une collection de caractères, vous ne pouvez pas modifier les caractères dans la chaîne de texte. Vous pouvez néanmoins modifier l’apparence du texte converti en changeant ses propriétés de trait et de remplissage. Le trait fait référence au contour du texte converti et le remplissage à la zone située à l’intérieur du contour du texte converti.  
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels en modifiant le trait et le remplissage de texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Exemple de définition du trait et du remplissage de différentes couleurs  
  
 ![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Exemple de pinceau image appliqué au trait  
  
 Il est également possible de modifier le rectangle de cadre englobant ou mise en surbrillance, du texte converti. L’exemple suivant illustre un moyen de créer des effets visuels en modifiant le trait et surbrillance du texte converti.  
  
 ![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Exemple de pinceau image appliqué au trait et surbrillance  
  
## <a name="example"></a>Exemple  
 La clé pour la conversion de texte à un <xref:System.Windows.Media.Geometry> objet consiste à utiliser le <xref:System.Windows.Media.FormattedText> objet. Une fois que vous avez créé cet objet, vous pouvez utiliser la <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> et <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> méthodes pour convertir le texte à <xref:System.Windows.Media.Geometry> objets. La première méthode retourne la géométrie du texte mis en forme ; la deuxième méthode retourne que la géométrie de la mise en forme du texte de la zone de délimitation. L’exemple de code suivant montre comment créer un <xref:System.Windows.Media.FormattedText> objet et récupérer les géométries du texte mis en forme et son cadre englobant.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Pour afficher les données récupérées les <xref:System.Windows.Media.Geometry> objets, vous devez accéder à la <xref:System.Windows.Media.DrawingContext> de l’objet qui affiche le texte converti. Dans ces exemples de code, cela en créant un objet de contrôle personnalisé qui est dérivé d’une classe qui prend en charge le rendu défini par l’utilisateur.  
  
 Pour afficher <xref:System.Windows.Media.Geometry> objets dans le contrôle personnalisé, fournissez une substitution pour la <xref:System.Windows.UIElement.OnRender%2A> (méthode). Votre méthode de substitution doit utiliser le <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> méthode pour dessiner le <xref:System.Windows.Media.Geometry> objets.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Pour la source de l’exemple d’objet d’un contrôle utilisateur personnalisé, consultez [OutlineTextControl.cs pour C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) et [OutlineTextControl.vb pour Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb). 
  
## <a name="see-also"></a>Voir aussi
- [Dessin du texte mis en forme](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
