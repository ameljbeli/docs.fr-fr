---
title: '&lt;autorisation&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 56b25955cf36598909176170235623b27da20867
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573190"
---
# <a name="ltpermissiongt-visual-basic"></a>&lt;autorisation&gt; (Visual Basic)
Spécifie une autorisation requise pour le membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `member`  
 Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie. Placez `member` entre guillemets ( » «).  
  
 `description`  
 Description de l’accès au membre.  
  
## <a name="remarks"></a>Notes  
 Utilisez le `<permission>` balise à documenter l’accès d’un membre. Utilisez la <xref:System.Security.PermissionSet> classe pour spécifier l’accès à un membre.  
  
 Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le `<permission>` balises pour décrire qui le <xref:System.Security.Permissions.FileIOPermission> est requis par le `ReadFile` (méthode).  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a>Voir aussi
- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
