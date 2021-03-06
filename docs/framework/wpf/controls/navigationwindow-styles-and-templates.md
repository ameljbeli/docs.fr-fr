---
title: Styles et modèles NavigationWindow
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
ms.openlocfilehash: 469788cd172c8a695c6a7538f4b2fb7665a8e92f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660994"
---
# <a name="navigationwindow-styles-and-templates"></a>Styles et modèles NavigationWindow
Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Navigation.NavigationWindow> contrôle. Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner le contrôle une apparence unique. Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="navigationwindow-parts"></a>Éléments de NavigationWindow  
 Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Navigation.NavigationWindow> contrôle.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_NavWinCP|<xref:System.Windows.Controls.ContentPresenter>|La zone pour le contenu.|  
  
## <a name="navigationwindow-states"></a>États de NavigationWindow  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Navigation.NavigationWindow> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Valide|ValidationStates|Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.|  
|InvalidFocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.|  
  
## <a name="navigationwindow-controltemplate-example"></a>Exemple de ControlTemplate NavigationWindow  
 Bien que cet exemple contienne tous les éléments qui sont définies dans le <xref:System.Windows.Controls.ControlTemplate> d’un <xref:System.Windows.Navigation.NavigationWindow> par défaut, les valeurs spécifiques doivent être imaginées comme exemples.  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 L’exemple précédent utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md)
- [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
