---
title: UShort, type de données (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 4b21624ea31fd0e11e598bab435b9f3c6f6d9b9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512838"
---
# <a name="ushort-data-type-visual-basic"></a>UShort, type de données (Visual Basic)

Contient des entiers 16 bits (2 octets) non signés compris entre 0 et 65 535.  
  
## <a name="remarks"></a>Notes

 Utilisez le `UShort` type de données pour contenir les données binaires trop grandes pour `Byte`.  
  
 La valeur par défaut de `UShort` est 0.  

## <a name="literal-assignments"></a>Affectations de littéraux

Vous pouvez déclarer et initialiser une `UShort` variable en lui assignant un littéral décimal, un littéral hexadécimal, un littéral octal, ou (à partir de Visual Basic 2017) un littéral binaire. Si le littéral entier est en dehors de la plage de `UShort` (autrement dit, s’il est inférieur à <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 65 034 représentés comme séparateur décimal, hexadécimal, et les littéraux binaires sont affectés à `UShort` valeurs.
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> Vous utilisez le préfixe `&h` ou `&H` pour désigner un littéral hexadécimal, le préfixe `&b` ou `&B` pour désigner un littéral binaire et le préfixe `&o` ou `&O` pour désigner un littéral octal. Les littéraux décimaux n’ont pas de préfixe.

À partir de Visual Basic 2017, vous pouvez également utiliser le caractère de soulignement, `_`, comme un séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant montre.

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

À partir de Visual Basic 15.5, vous pouvez également utiliser le caractère de soulignement (`_`) comme séparateur de début entre le préfixe et les chiffres hexadécimaux, binaires ou octaux. Exemple :

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Littéraux numériques peuvent également inclure le `US` ou `us` [caractère de type](../../programming-guide/language-features/data-types/type-characters.md) pour désigner le `UShort` type de données, comme le montre l’exemple suivant.

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>Conseils de programmation
  
-   **Nombres négatifs.** Étant donné que `UShort` est un type non signé, il ne peut pas représenter un nombre négatif. Si vous utilisez le moins unaire (`-`) opérateur sur une expression qui correspond au type `UShort`, Visual Basic convertit l’expression à `Integer` première.  
  
-   **Conformité CLS.** Le `UShort` type de données n’est pas dans le cadre de la [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), le code conforme CLS ne peut pas consommer un composant qui l’utilise.
  
-   **Étendues.** Le `UShort` type de données s’étend à `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, et `Double`. Cela signifie que vous pouvez convertir `UShort` à un de ces types sans rencontrer un <xref:System.OverflowException?displayProperty=nameWithType> erreur.  
  
-   **Caractères de type.** Ajout des caractères de type littéral `US` à un littéral force ce dernier à la `UShort` type de données. `UShort` n’a aucun caractère de type d’identificateur.  
  
-   **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.UInt16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi
- <xref:System.UInt16>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Guide pratique pour appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
