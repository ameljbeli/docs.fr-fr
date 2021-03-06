---
title: '&lt;SMTP&gt; , élément (paramètres réseau)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 4a2947594f5adc9cc4c11471e133c6a4f2662a50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638013"
---
# <a name="ltsmtpgt-element-network-settings"></a>&lt;SMTP&gt; , élément (paramètres réseau)
Configure le format de remise, la méthode de remise et à partir de l’adresse pour l’envoi des e-mails.  
  
 \<configuration>  
\<system.net>  
\<mailSettings>  
\<smtp>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`deliveryFormat`|Spécifie le format de remise de messages électroniques sortants. Les valeurs acceptables sont SevenBit et International.|  
|`deliveryMethod`|Spécifie la méthode de remise pour les e-mails. Les valeurs acceptables sont réseau, PickupDirectoryFromIis et SpecifiedPickupDirectory.|  
|`from`|Spécifie l’adresse d’origine de messages électroniques sortants.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Attribut|Description|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|Configure le répertoire local pour un serveur SMTP Simple Mail Transport Protocol ().|  
|`network`|Configure les options de réseau pour un serveur SMTP externe.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|**Élément**|**Description**|  
|-----------------|---------------------|  
|[\<mailSettings>, élément (paramètres réseau)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Configure les options d’envoi du courrier.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer un e-mail à l’aide des informations d’identification du réseau par défaut.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [Schéma des paramètres réseau](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
