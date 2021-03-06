---
title: '&lt;TypeInstantiation&gt;, élément (.NET Native)'
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 818a52ceb1428327c5bcb778f85015458990578f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612561"
---
# <a name="lttypeinstantiationgt-element-net-native"></a>&lt;TypeInstantiation&gt;, élément (.NET Native)
Applique la stratégie de réflexion runtime à un type générique construit.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
                   Activate="policy_type"  
                   Browse="policy_type"  
                   Dynamic="policy_type"  
                   Serialize="policy_type"  
                   DataContractSerializer="policy_setting"  
                   DataContractJsonSerializer="policy_setting"  
                   XmlSerializer="policy_setting"  
                   MarshalObject="policy_setting"  
                   MarshalDelegate="policy_setting"  
                   MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Type d'attribut|Description|  
|---------------|--------------------|-----------------|  
|`Name`|Général|Attribut requis. Spécifie le nom du type.|  
|`Arguments`|Général|Attribut requis. Spécifie les arguments de type générique. Si plusieurs arguments sont présents, ils sont séparés par des virgules.|  
|`Activate`|Réflexion|Attribut facultatif. Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.|  
|`Browse`|Réflexion|Attribut facultatif. Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.|  
|`Dynamic`|Réflexion|Attribut facultatif. Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.|  
|`Serialize`|Sérialisation|Attribut facultatif. Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.|  
|`DataContractSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Sérialisation|Attribut facultatif. Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.|  
|`MarshalDelegate`|Interop|Attribut facultatif. Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.|  
|`MarshalStructure`|Interop|Attribut facultatif. Stratégie de contrôles pour le marshaling de structures en code natif.|  
  
## <a name="name-attribute"></a>Name (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|*type_name*|Nom du type. Si cet élément `<TypeInstantiation>` est l’enfant d’un élément [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), d’un élément [\<<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou d’un autre élément `<TypeInstantiation>`, *type_name* peut spécifier le nom du type sans son espace de noms. Dans le cas contraire, *type_name* doit inclure le nom de type complet. Le nom du type n'est pas décoré. Par exemple, pour un objet <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, l'élément `<TypeInstantiation>` peut apparaître comme suit :<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>Attribut Arguments  
  
|Valeur|Description|  
|-----------|-----------------|  
|*type_argument*|Spécifie les arguments de type générique. Si plusieurs arguments sont présents, ils sont séparés par des virgules. Chaque argument doit être composé du nom de type qualifié complet.|  
  
## <a name="all-other-attributes"></a>Tous les autres attributs  
  
|Valeur|Description|  
|-----------|-----------------|  
|*paramètre_stratégie*|Paramètre à appliquer à ce type de stratégie pour le type générique construit. Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`. Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)|Applique la stratégie de réflexion à un événement appartenant à ce type.|  
|[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)|Applique la stratégie de réflexion à un champ appartenant à ce type.|  
|[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|Applique la stratégie à un type, si cette stratégie a été appliquée au type représenté par l'élément conteneur `<TypeInstantiation>`.|  
|[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)|Applique la stratégie de réflexion à une méthode appartenant à ce type.|  
|[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Applique la stratégie de réflexion à une méthode générique construite appartenant à ce type.|  
|[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|Applique la stratégie de réflexion à une propriété appartenant à ce type.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie de réflexion à un type imbriqué.|  
|`<TypeInstantiation>`|Applique la stratégie de réflexion à un type générique construit imbriqué.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|Sert de conteneur pour des types à l'échelle de l'application et pour des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.|  
|[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|Applique la stratégie de réflexion à tous les types d'un assembly spécifié.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Définit l'assembly qui contient des types et des membres de types dont les métadonnées sont disponibles pour la réflexion au moment de l'exécution.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Applique la stratégie de réflexion à tous les types d'un espace de noms.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Applique la stratégie de réflexion à un type et à tous ses membres.|  
|`<TypeInstantiation>`|Applique la stratégie de réflexion à un type générique construit et à tous ses membres.|  
  
## <a name="remarks"></a>Notes  
 Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs. Toutefois, au moins un doit être présent.  
  
 Si un élément `<TypeInstantiation>` est l’enfant d’un élément [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md) ou [\<Type>](../../../docs/framework/net-native/type-element-net-native.md), il se substitue aux paramètres de stratégie définis par l’élément parent. Si un élément [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) spécifie une définition de type générique correspondante, l’élément `<TypeInstantiation>` se substitue à la stratégie de réflexion du runtime uniquement pour les instanciations du type générique construit spécifié.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise la réflexion pour récupérer la définition de type générique construit d'un objet <xref:System.Collections.Generic.Dictionary%602>. Il utilise également la réflexion pour afficher des informations sur les objets <xref:System.Type> qui représentent des types génériques construits et des définitions de type générique. La variable `b` dans l’exemple est un <xref:Windows.UI.Xaml.Controls.TextBlock> contrôle.  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 Après la compilation avec la chaîne de l’outil [!INCLUDE[net_native](../../../includes/net-native-md.md)], l’exemple lève une exception [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) sur la ligne qui appelle la méthode <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType>. Vous pouvez éliminer l'exception et fournir les métadonnées nécessaires en ajoutant l'élément `<TypeInstantiation>` suivant au fichier de directives runtime :  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Voir aussi
- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Éléments de directive runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
