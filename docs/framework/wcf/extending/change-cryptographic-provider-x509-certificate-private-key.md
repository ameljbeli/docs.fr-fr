---
title: 'Procédure : Modifier le fournisseur de services de chiffrement pour un certificat X.509&#39;clé privée s'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: 40c98d17a52643f451ec01bc8b97c60f2b011b36
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498971"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificate39s-private-key"></a>Procédure : Modifier le fournisseur de services de chiffrement pour un certificat X.509&#39;clé privée s
Cette rubrique montre comment modifier le fournisseur de services de chiffrement utilisé pour fournir la clé privée d’un certificat X.509 et comment intégrer le fournisseur dans l’infrastructure de sécurité de Windows Communication Foundation (WCF). Pour plus d’informations sur l’utilisation de certificats, consultez [utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 L’infrastructure de sécurité WCF fournit un moyen d’introduire de nouveaux types de jetons de sécurité comme décrit dans [Comment : Créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md). Vous pouvez aussi utiliser un jeton personnalisé pour remplacer les types de jeton existants fournis par le système.  
  
 Dans cette rubrique, le jeton de sécurité X.509 fourni par le système est remplacé par un jeton X.509 personnalisé qui fournit une implémentation différente pour la clé privée de certificat. Cette opération est utile dans les scénarios où la clé privée à proprement dite est fournie par un fournisseur de services de chiffrement différent du fournisseur Windows par défaut. Parmi les exemples d'un autre fournisseur de services de chiffrement figure un module de la sécurité du matériel qui effectue toutes les opérations de chiffrement liées à la clé privée sans stocker les clés privées en mémoire, ce qui améliore la sécurité du système.  
  
 L'exemple suivant est fourni à des fins de démonstration uniquement. Il ne remplace pas le fournisseur de services de chiffrement Windows par défaut, mais il montre comment intégrer ce type de fournisseur.  
  
## <a name="procedures"></a>Procédures  
 Chaque jeton de sécurité qui possède une clé ou des clés de sécurité associées doit implémenter la propriété <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> qui retourne une collection de clés issue de l'instance du jeton de sécurité. Si le jeton est un jeton de sécurité X.509, la collection contient une instance unique de la classe <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> qui représente à la fois les clés privées et publiques associées au certificat. Pour remplacer le fournisseur de services de chiffrement par défaut utilisé pour fournir les clés du certificat, créez une nouvelle implémentation de cette classe.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Pour créer une clé asymétrique X.509 personnalisée  
  
1.  Définissez une nouvelle classe dérivée de la classe <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>.  
  
2.  Substituez la propriété en lecture seule <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A>. Cette propriété retourne la taille de clé réelle de la paire de clés publique/privée du certificat.  
  
3.  Remplacez la méthode <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> . Cette méthode est appelée par l’infrastructure de sécurité WCF pour déchiffrer une clé symétrique avec la clé privée du certificat. (La clé a été chiffrée précédemment avec la clé publique du certificat.)  
  
4.  Remplacez la méthode <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> . Cette méthode est appelée par l’infrastructure de sécurité WCF pour obtenir une instance de la <xref:System.Security.Cryptography.AsymmetricAlgorithm> classe qui représente le fournisseur de chiffrement pour soit la clé du certificat privé ou public, selon les paramètres transmis à la méthode.  
  
5.  Facultatif. Remplacez la méthode <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A>. Substituez cette méthode si une implémentation différente de la classe <xref:System.Security.Cryptography.HashAlgorithm> est requise.  
  
6.  Remplacez la méthode <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A>. Cette méthode retourne une instance de la classe <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> associée à la clé privée du certificat.  
  
7.  Remplacez la méthode <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A>. Cette méthode est utilisée pour indiquer si un algorithme de chiffrement particulier est pris en charge par l'implémentation de la clé de sécurité.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 La procédure suivante montre comment intégrer le X.509 sécurité asymétrique clé implémentation personnalisée créée dans la procédure précédente avec l’infrastructure de sécurité WCF pour remplacer la sécurité X.509 fourni par le système de jeton.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Pour remplacer le jeton de sécurité X.509 fourni par le système par un jeton de clé de sécurité asymétrique X.509 personnalisé  
  
1.  Créez un jeton de sécurité X.509 personnalisé qui retourne la clé de sécurité asymétrique X.509 personnalisée au lieu de la clé de sécurité fournie par le système, comme indiqué dans l'exemple suivant. Pour plus d’informations sur les jetons de sécurité personnalisés, consultez [Comment : Créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2.  Créez un fournisseur de jetons de sécurité personnalisé qui retourne un jeton de sécurité X.509 personnalisé, comme indiqué dans l'exemple. Pour plus d’informations sur les fournisseurs de jetons de sécurité personnalisé, consultez [Comment : Créer un fournisseur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3.  Si la clé de sécurité personnalisée doit être utilisée sur le côté d'initiateur, créez un gestionnaire de jetons de sécurité client personnalisé et des classes d'informations d'identification du client personnalisées, comme indiqué dans l'exemple suivant. Pour plus d’informations sur les informations d’identification client personnalisées et les gestionnaires de jetons de sécurité client, consultez [procédure pas à pas : Création du Client personnalisés et les informations d’identification du Service](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4.  Si la clé de sécurité personnalisée doit être utilisée sur le côté destinataire, créez un gestionnaire de jetons de sécurité client personnalisé et des classes personnalisées d'informations d'identification du client, comme indiqué dans l'exemple suivant. Pour plus d’informations sur les informations d’identification de service personnalisées et les gestionnaires de jetons de sécurité de service, consultez [procédure pas à pas : Création du Client personnalisés et les informations d’identification du Service](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.Security.Cryptography.AsymmetricAlgorithm>
- <xref:System.Security.Cryptography.HashAlgorithm>
- <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>
- [Procédure pas à pas : Création du Client personnalisés et les informations d’identification de Service](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [Guide pratique pour Créer un authentificateur de jeton de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Guide pratique pour Créer un fournisseur de jetons de sécurité personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [Guide pratique pour Créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
- [Architecture de sécurité](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
