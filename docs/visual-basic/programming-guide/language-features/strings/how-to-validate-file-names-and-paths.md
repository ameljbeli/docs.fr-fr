---
title: 'Procédure : Valider les noms de fichiers et chemins d’accès dans Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: c0d39ecbaf9ca23c72e45b8839d268fbc38fe48e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648447"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Procédure : Valider les noms de fichiers et chemins d’accès dans Visual Basic
Cet exemple retourne un `Boolean` valeur qui indique si une chaîne représente un nom de fichier ou le chemin d’accès. La validation vérifie si le nom contient des caractères qui ne sont pas autorisés par le système de fichiers.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 Cet exemple ne vérifie pas si le nom a placé incorrectement deux-points ou répertoires sans nom, ou si la longueur du nom dépasse la longueur maximale définie par le système. Elle également ne vérifie pas si l’application est autorisé à accéder à la ressource de système de fichiers avec le nom spécifié.  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Validation de chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
