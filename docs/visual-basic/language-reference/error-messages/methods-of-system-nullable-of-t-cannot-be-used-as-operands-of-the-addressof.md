---
title: Méthodes de &#39;System.Nullable (Of T)&#39; ne peut pas être utilisé en tant qu’opérandes de le &#39;AddressOf&#39; opérateur
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: c3e34e79f2e91bb55bb2e053ae3e59fd42c4250c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655320"
---
# <a name="methods-of-39systemnullableof-t39-cannot-be-used-as-operands-of-the-39addressof39-operator"></a>Méthodes de &#39;System.Nullable (Of T)&#39; ne peut pas être utilisé en tant qu’opérandes de le &#39;AddressOf&#39; opérateur
Une instruction utilise le `AddressOf` opérateur avec un opérande qui représente une procédure de la <xref:System.Nullable%601> structure.  
  
 **ID d’erreur :** BC32126  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Remplacez le nom de la procédure dans le `AddressOf` clause avec un opérande qui n’est pas un membre de <xref:System.Nullable%601>.  
  
-   Écrire une classe qui encapsule la méthode de <xref:System.Nullable%601> que vous souhaitez utiliser. Dans l’exemple suivant, le `NullableWrapper` classe définit une nouvelle méthode nommée `GetValueOrDefault`. Étant donné que cette nouvelle méthode n’est pas un membre de <xref:System.Nullable%601>, elle peut être appliquée à `nullInstance`, une instance d’un type nullable, pour former un argument pour `AddressOf`.  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.Nullable%601>
- [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Types valeur Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
