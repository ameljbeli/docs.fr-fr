---
title: Entrée XmlDataDocument dans XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7fb30104f36a565f4e6742c8f808c48e4ef39ec
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842552"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>Entrée XmlDataDocument dans XslTransform
> [!NOTE]
>  La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).  
  
 Microsoft [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implémente le DOM (Document Object Model) XML pour fournir l'accès aux données des documents XML et des classes supplémentaires pour lire et écrire des documents XML, ainsi que pour naviguer dans ceux-ci. La classe <xref:System.Xml.XmlDataDocument>, située dans l'espace de noms <xref:System.Xml>, fournit un accès relationnel aux données grâce à sa capacité de synchronisation avec les données relationnelles contenues dans le <xref:System.Data.DataSet>. Vous pouvez afficher et manipuler simultanément un document XML structuré par l'intermédiaire de la représentation relationnelle de l'objet <xref:System.Data.DataSet> ou manipuler le document XML semi-structuré par l'intermédiaire de la représentation DOM de l'objet <xref:System.Xml.XmlDataDocument>. C'est pourquoi l'objet <xref:System.Xml.XmlDataDocument> dépasse les limites des mondes XML et relationnels.  
  
 Si les données sont stockées dans une structure relationnelle et que vous souhaitez qu'elles soient une entrée dans une transformation XSLT, vous pouvez charger les données relationnelles dans un objet <xref:System.Data.DataSet> et les associer à l'objet <xref:System.Xml.XmlDataDocument>. L'objet <xref:System.Xml.XPath.XPathNavigator>, l'entrée dans l'objet <xref:System.Xml.Xsl.XslTransform>, est implémenté sur l'objet <xref:System.Xml.XmlDataDocument> à l'aide de l'interface <xref:System.Xml.XPath.IXPathNavigable>. En prenant des données relationnelles, en les chargeant dans un objet <xref:System.Data.DataSet> et en utilisant la synchronisation dans l'objet <xref:System.Xml.XmlDataDocument>, il est à présent possible d'effectuer des transformations XSLT sur des données relationnelles.  
  
 Pour plus d'informations sur l'application d'une transformation aux données relationnelles, consultez [Application d'une transformation XSLT à un DataSet](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDataDocument>  
- [Synchronisation DataSet et XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
- [Transformations XSLT avec la classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [Implémentation du processeur XSLT par la classe XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
- [XPathNavigator dans les transformations](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [XPathNodeIterator dans les transformations](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [Entrée XPathDocument dans XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [Entrée XmlDocument dans XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
