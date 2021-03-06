---
title: 'Procédure : Désactiver le chiffrement des Signatures numériques'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 360d939db1c7e75cea1b6f3c6a013f214564a717
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576367"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Procédure : Désactiver le chiffrement des Signatures numériques
Par défaut, un message est signé et la signature est chiffrée numériquement. Cette opération est contrôlée en créant une liaison personnalisée à l'aide d'une instance de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, et en affectant à la propriété `MessageProtectionOrder` de l'une de ces deux classes une valeur d'énumération <xref:System.ServiceModel.Security.MessageProtectionOrder>. La valeur par défaut est <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Ce processus consomme jusqu'à 30 pour cent de temps de plus que la simple signature et le chiffrement à partir de la taille de message totale (plus le message est petit, plus grand est l'impact sur les performances). Toutefois, désactiver le chiffrement de la signature présente un risque en matière de sécurité, puisqu'il peut permettre à un intrus de deviner le contenu du message. En effet, l'élément de la signature contient le code de hachage du texte brut de chaque partie signée du message. Par exemple, même si le corps des messages est chiffré par défaut, la signature non chiffrée contient le code de hachage du corps des messages avant le chiffrement. Si le jeu de valeurs possibles pour la partie signée et chiffrée est petit, un intrus peut être en mesure de deviner le contenu en consultant la valeur de hachage. Le chiffrement de la signature réduit les risques présents dans ce domaine.  
  
 Par conséquent, désactivez uniquement le chiffrement de la signature lorsque la valeur du contenu est basse ou le jeu de valeurs de contenu possible est grand et non déterministe, et le gain de performance est plus important que de réduire les risques d'attaque décrits précédemment.  
  
> [!NOTE]
>  Si le message ne contient aucun élément chiffré, l'élément de signature n'est pas chiffré, même lorsque la propriété <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> a la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Ce comportement se produit même avec les liaisons fournies par le système ; toutes les liaisons fournies par le système ont l’ordre de protection des messages défini à `SignBeforeEncryptAndEncryptSignature`. Toutefois, Web Services Description Language (WSDL) WCF généré contient toujours la `<sp:EncryptSignature>` assertion.  
  
### <a name="to-disable-digital-signing"></a>Pour désactiver la signature numérique  
  
1.  Créer un <xref:System.ServiceModel.Channels.CustomBinding>. Pour plus d'informations, voir [Procédure : Créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Ajoutez un élément <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou un élément <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à la collection de liaisons.  
  
3.  Affectez à la propriété <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> ou affectez à la propriété <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> la valeur <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Voir aussi
- [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
