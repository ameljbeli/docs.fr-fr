---
title: Valeur de type &#39; &lt;nom_type1&gt; &#39; ne peut pas être converti en &#39; &lt;nom_type2&gt; &#39; (plusieurs références de fichier)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 943b9612a9217b90c19f34285e812c4e1cccf81a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691371"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>Valeur de type &#39; &lt;nom_type1&gt; &#39; ne peut pas être converti en &#39; &lt;nom_type2&gt; &#39; (plusieurs références de fichier)
Valeur de type '\<nom_type1 >' ne peut pas être convertie en '\<nom_type2 >'. Incompatibilité de type peut être dû à la combinaison d’une référence de fichier pour '\<chemin_fichier1 >' dans le projet '\<nom_projet1 >' avec une référence de fichier à '\<chemin_fichier2 >' dans le projet '\<nom_projet2 >'. Si les deux assemblys sont identiques, essayez de remplacer ces deux références pour qu’elles se situent au même emplacement.  
  
 Dans une situation où un projet fait plusieurs références de fichier à un assembly, le compilateur ne peut pas garantir qu’un type peut être converti vers un autre.  
  
 Chaque référence de fichier Spécifie un chemin d’accès et le nom du fichier de sortie d’un projet (généralement un fichier DLL). Le compilateur ne peut pas garantir que les fichiers de sortie proviennent de la même source, ou qu’ils représentent la même version du même assembly. Par conséquent, il ne peut pas garantir que les types dans les références différentes sont du même type, ou même que l’un peut être converti à l’autre.  
  
 Vous pouvez utiliser une référence de fichier unique si vous savez que les assemblys référencés ont la même identité d’assembly. L’ *identité de l’assembly* comprend le nom de l’assembly, sa version, sa clé publique (le cas échéant) et sa culture. Ces informations identifient de manière unique l’assembly.  
  
 **ID d’erreur :** BC30961  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si les assemblys référencés ont la même identité de l’assembly, supprimez ou remplacez une des références de fichier afin qu’il soit uniquement une référence de fichier unique.  
  
-   Si les assemblys référencés n’ont pas la même identité d’assembly, puis modifiez votre code afin qu’il ne tente pas de convertir un type dans un à un type dans l’autre.  
  
## <a name="see-also"></a>Voir aussi
- [Conversions de type en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)

