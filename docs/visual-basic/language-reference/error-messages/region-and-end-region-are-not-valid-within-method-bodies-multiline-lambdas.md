---
title: '&#39;#Region&#39; et &#39;#End Region&#39; instructions ne sont pas valides dans les expressions lambda multiligne de corps de méthode'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 55399cd123ce4d67cc833f2eabe3230acdafc0bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737213"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39;#Region&#39; et &#39;#End Region&#39; instructions ne sont pas valides dans les expressions lambda multiligne corps de méthode
Le `#Region` bloc doit être déclaré au niveau de la classe, module ou d’espace de noms. Une zone réductible peut inclure une ou plusieurs procédures, mais il ne peut pas commencer ou se terminer à l’intérieur d’une procédure.  
  
 **ID d’erreur :** BC32025  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que la procédure précédente est correctement terminée avec un `End Function` ou `End Sub` instruction.  
  
2.  Vérifiez que le `#Region` et `#End Region` sont des directives dans le même bloc de code.  
  
## <a name="see-also"></a>Voir aussi
- [#Region (directive)](../../../visual-basic/language-reference/directives/region-directive.md)
