---
title: Valeur de type &#39; &lt;nom_type1&gt; &#39; ne peut pas être converti en &#39; &lt;nom_type2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 00ce143eecefbdf2f1b9e204ae2005be4bb81e39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627601"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>Valeur de type &#39; &lt;nom_type1&gt; &#39; ne peut pas être converti en &#39; &lt;nom_type2&gt;&#39;
Valeur de type '\<nom_type1 >' ne peut pas être convertie en '\<nom_type2 >'. Incompatibilité de type peut être dû à la combinaison d’une référence de fichier avec une référence de projet à l’assembly '\<nom_assembly >'. Essayez de remplacer la référence de fichier à '\<filepath >' dans le projet '\<nom_projet1 >' avec une référence de projet à '\<nom_projet2 >'.  
  
 Dans une situation où un projet fait une référence de projet et une référence de fichier, le compilateur ne peut pas garantir qu’un type peut être converti vers un autre.  
  
 Le pseudo-code suivant illustre une situation qui peut générer cette erreur.  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 Projet `P1` établit une référence de projet indirecte via le projet `P2` au projet `P3`et également une référence de fichier directe à `P3`. La déclaration de `commonObject` utilise la référence de fichier à `P3`, tandis que l’appel à `P2.getCommonClass` utilise la référence de projet `P3`.  
  
 Le problème dans ce cas est que la référence de fichier Spécifie un chemin d’accès et le nom du fichier de sortie de `P3` (en général, p3.dll), tandis que les références de projet identifient le projet source (`P3`) par le nom du projet. Pour cette raison, le compilateur ne peut pas garantir que le type `P3.commonClass` provient le même code source, les deux références différentes.  
  
 Cette situation se produit généralement lorsque les références de projet et les références de fichier sont combinés. Dans l’illustration précédente, le problème se produirait pas si `P1` crée une référence de projet directe pour `P3` au lieu d’une référence de fichier.  
  
 **ID d’erreur :** BC30955  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Modifiez la référence de fichier à une référence de projet.  
  
## <a name="see-also"></a>Voir aussi
- [Conversions de type en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)

