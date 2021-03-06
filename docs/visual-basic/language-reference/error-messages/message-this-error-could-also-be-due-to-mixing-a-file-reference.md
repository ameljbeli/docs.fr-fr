---
title: '&lt;message&gt; cette erreur peut également être en raison d’une combinaison d’une référence de fichier avec une référence de projet à l’assembly &#39; &lt;assemblyname&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: d4fb2a8985a21ecea5056b83d2766e8dc468180d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528990"
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;message&gt; cette erreur peut également être en raison d’une combinaison d’une référence de fichier avec une référence de projet à l’assembly &#39; &lt;assemblyname&gt;&#39;
\<message > Cette erreur peut également être en raison d’une combinaison d’une référence de fichier avec une référence de projet à l’assembly '\<nom_assembly >. Dans ce cas, essayez de remplacer la référence de fichier à '\<nom_fichier_assembly >' dans le projet '\<nom_projet1 >' avec une référence de projet à '\<nom_projet2 >'.  
  
 Code de votre projet accède à un membre d’un autre projet, mais la configuration de votre solution n’autorise pas le compilateur Visual Basic résoudre la référence.  
  
 Pour accéder à un type défini dans un autre assembly, le compilateur Visual Basic doit avoir une référence à cet assembly. Il doit s’agir d’une référence unique et non équivoque qui ne provoque pas de références circulaires parmi des projets.  
  
 **ID d’erreur :** BC30971  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer. Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.  
  
2.  Dans les propriétés de votre projet, ajoutez une référence au projet contenant l’assembly qui définit le type que vous utilisez.  
  
## <a name="see-also"></a>Voir aussi
- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)
- [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
- [Dépannage de références rompues](/visualstudio/ide/troubleshooting-broken-references)
