---
title: out, modificateur de paramètre - Référence C#
ms.custom: seodec18
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: f50490195344c488d264735f89e0107caba888c2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242059"
---
# <a name="out-parameter-modifier-c-reference"></a>out, modificateur de paramètre (référence C#)
Le mot clé `out` entraîne le passage des arguments par référence. Il est similaire au mot clé [ref](ref.md), à la différence que `ref` nécessite que la variable soit initialisée avant d’être passée. Il est également similaire au mot clé [in](in-parameter-modifier.md), à la différence que `in` n’autorise pas la méthode appelée à modifier la valeur d’argument. Pour utiliser un paramètre `out`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `out`. Par exemple :  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> Le mot clé `out` peut également être utilisé avec un paramètre de type générique pour spécifier que le paramètre de type est covariant. Pour plus d’informations sur l’utilisation du mot clé `out` dans ce contexte, consultez [out, modificateur générique](out-generic-modifier.md).
  
Les variables passées comme arguments `out` n’ont pas à être initialisées avant d’être passées dans un appel de méthode. Toutefois, la méthode appelée doit assigner une valeur avant le retour de la méthode.  
  
Bien que les mots clés `in`, `ref` et `out` entraînent un comportement différent au moment de l’exécution, ils ne sont pas considérés comme faisant partie de la signature de la méthode au moment de la compilation. Par conséquent, les méthodes ne peuvent pas être surchargées si la seule différence est que l’une d’elles accepte un argument `ref` ou `in` et que l’autre accepte un argument `out`. Le code suivant, par exemple, ne se compilera pas :  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Toutefois, la surcharge est autorisée si une méthode prend un argument `ref`, `in` ou `out`, et que l’autre méthode n’a aucun de ces modificateurs, comme suit :  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Le compilateur choisit la meilleure surcharge en mettant en correspondance les modificateurs de paramètre sur le site d’appel et les modificateurs de paramètre utilisés dans l’appel de méthode.
 
Les propriétés ne sont pas des variables et, par conséquent, ne peuvent pas être passées en tant que paramètres `out`.
  
Vous ne pouvez pas utiliser les mots clés `in`, `ref` ou `out` pour les types de méthodes suivants :  
  
-   Méthodes async, que vous définissez à l’aide du modificateur [async](../../../csharp/language-reference/keywords/async.md).  
  
-   Les méthodes Iterator, qui incluent une instruction [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  

## <a name="declaring-out-arguments"></a>Déclaration d’arguments `out`   

 La déclaration d’une méthode avec des arguments `out` est utile lorsque vous souhaitez qu’une méthode retourne plusieurs valeurs. L'exemple suivant utilise `out` pour retourner trois variables avec un seul appel de méthode. Notez que le troisième argument reçoit la valeur null. Cela permet aux méthodes de retourner des valeurs le cas échéant.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 Le [modèle Try](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods) consiste à retourner une valeur `bool` qui indique si une opération a réussi ou échoué et à retourner le résultat de l’opération dans un argument `out`. Un certain nombre de méthodes d’analyse, notamment la méthode [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)), utilisent ce modèle.
   
## <a name="calling-a-method-with-an-out-argument"></a>Appel d’une méthode avec un argument `out`

Dans C# 6 et les versions antérieures, vous devez déclarer une variable dans une instruction distincte avant de la passer comme argument `out`. L’exemple suivant déclare une variable nommée `number` avant de la passer à la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)), qui tente de convertir une chaîne en nombre.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

À compter de C# 7.0, vous pouvez déclarer la variable `out` dans la liste d’arguments de l’appel de méthode au lieu de le faire dans une déclaration de variable distincte. Cette technique rend le code plus simple et plus lisible, et vous empêche également d’assigner par inadvertance une valeur à la variable avant l’appel de méthode. L’exemple suivant est semblable au précédent, sauf qu’il définit la variable `number` dans l’appel de la méthode [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)).

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
Dans l’exemple précédent, la variable `number` est fortement typée en `int`. Vous pouvez également déclarer une variable locale implicitement typée, comme dans l’exemple suivant.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>Spécification du langage C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../../../csharp/language-reference/index.md)  
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
- [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
- [Paramètres de méthodes](../../../csharp/language-reference/keywords/method-parameters.md)
