---
title: 'Procédure : Remplir une arborescence XML avec un XmlWriter (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: 53c77a9b31fa51f1ba79e99d564e5092f7c079a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625872"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>Procédure : Remplir une arborescence XML avec un XmlWriter (LINQ to XML) (Visual Basic)
L’une des manières de remplir une arborescence XML consiste à utiliser <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un objet <xref:System.Xml.XmlWriter>, puis à écrire dans l’objet <xref:System.Xml.XmlWriter>. L’arborescence XML est remplie avec tous les nœuds écrits dans l’objet <xref:System.Xml.XmlWriter>.  
  
 Cette méthode est généralement utilisée quand [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est utilisé avec une autre classe censée écrire dans un objet <xref:System.Xml.XmlWriter>, comme <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Exemple  
 Une utilisation possible de <xref:System.Xml.Linq.XContainer.CreateWriter%2A> est lors de l'appel à une transformation XSLT. Cet exemple crée une arborescence XML, crée un objet <xref:System.Xml.XmlReader> à partir de l'arborescence XML, crée un nouveau document, puis crée un objet <xref:System.Xml.XmlWriter> pour écrire dans le nouveau document. Il appelle ensuite la transformation XSLT, en passant <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>. Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>   
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                    <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                    <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [Création d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
