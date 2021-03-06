---
title: byte - Référence C#
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: 9c70c5a08e1509e9c8b1a007603abfbf18f03f14
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241226"
---
# <a name="byte-c-reference"></a>byte (référence C#)

`byte` désigne un type intégral qui stocke des valeurs comme indiqué dans le tableau suivant.  
  
|Type|Plage|Size|Type .NET|  
|----------|-----------|----------|-------------------------|  
|`byte`|0 à 255|Entier 8 bits non signé|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Littéraux  

 Vous pouvez déclarer et initialiser une variable `byte` en lui assignant un littéral décimal, hexadécimal ou binaire (à compter de C# 7.0). Si le littéral entier est en dehors de la plage autorisée pour le type `byte` (autrement dit, s’il est inférieur à <xref:System.Byte.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Byte.MaxValue?displayProperty=nameWithType>), une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 201 représentés comme des littéraux décimaux, hexadécimaux et binaires sont implicitement convertis des valeurs [int](../../../csharp/language-reference/keywords/int.md) en `byte`.    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire. Les littéraux décimaux n’ont pas de préfixe.

À compter de C# 7.0, des fonctionnalités ont été ajoutées pour améliorer la lisibilité. 
 - C# 7.0 prend en charge l’utilisation du caractère de soulignement (`_`) comme séparateur numérique.
 - C# 7.2 prend en charge l’utilisation de `_` comme séparateur de chiffres pour un littéral binaire ou hexadécimal, après le préfixe. Un trait de soulignement n’est pas autorisé au début d’un littéral décimal.

Voici quelques exemples.

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>Conversions  
 Il y a une conversion implicite prédéfinie du type `byte` en [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Vous ne pouvez pas convertir implicitement en type `byte` des types numériques non littéraux ayant une taille de stockage supérieure. Pour plus d’informations sur les tailles de stockage des types intégraux, consultez [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md). Observez l’exemple suivant qui utilise deux variables `byte`, `x` et `y` :  
  
```csharp  
byte x = 10, y = 20;  
```  
  
 L’instruction d’assignation suivante entraîne une erreur de compilation, car l’expression arithmétique située à droite de l’opérateur d’assignation donne la valeur `int` par défaut.  
  
```csharp  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Pour corriger ce problème, utilisez un cast :  
  
```csharp  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 Il est cependant possible d’utiliser les instructions suivantes, dans lesquelles la variable de destination a une taille de stockage égale ou supérieure :  
  
```csharp  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Il n’y a pas non plus de conversion implicite en `byte` pour les types virgule flottante. Par exemple, l’instruction suivante génère une erreur du compilateur, sauf si vous utilisez un cast explicite :  
  
```csharp  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Quand vous appelez des méthodes surchargées, vous devez utiliser un cast. Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `byte` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 L’utilisation du cast `byte` garantit l’appel du type correct, comme dans cet exemple :  
  
```csharp  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Types intégraux](~/_csharplang/spec/types.md#integral-types) dans la [spécification du langage C#](../language-specification/index.md). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi  

- <xref:System.Byte>  
- [Référence C#](../../../csharp/language-reference/index.md)  
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
- [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
- [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
