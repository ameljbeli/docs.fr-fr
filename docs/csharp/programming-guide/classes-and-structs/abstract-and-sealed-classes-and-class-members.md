---
title: Classes abstract et sealed et membres de classe - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 8c0b8e9814bf692e486624dd8a4a99d98337bca9
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235853"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Classes abstract et sealed et membres de classe (Guide de programmation C#)
Le mot clé [abstract](../../../csharp/language-reference/keywords/abstract.md) vous permet de créer des classes et des membres de [class](../../../csharp/language-reference/keywords/class.md) qui sont incomplets et doivent être implémentés dans une classe dérivée.  
  
 Le mot clé [sealed](../../../csharp/language-reference/keywords/sealed.md) vous permet d’empêcher l’héritage d’une classe ou de certains membres de classe qui étaient précédemment marqués comme [virtual](../../../csharp/language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Classes abstraites et membres de classe  
 Les classes peuvent être déclarées comme abstraites en plaçant le mot clé `abstract` avant la définition de classe. Par exemple :  
  
 [!code-csharp[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]  
  
 Une classe abstraite ne peut pas être instanciée. Le but d'une classe abstraite est de fournir une définition commune d'une classe de base pouvant être partagée par plusieurs classes dérivées. Par exemple, une bibliothèque de classes peut définir une classe abstraite qui est utilisée comme un paramètre pour beaucoup de ses fonctions, et exiger des programmeurs qui l'utilisent de fournir leur propre implémentation de la classe en créant une classe dérivée.  
  
 Les classes abstraites peuvent également définir des méthodes abstraites. Pour ce faire, ajoutez le mot clé `abstract` avant le type de retour de la méthode. Exemple :  
  
 [!code-csharp[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]  
  
 Les méthodes abstraites n'ont pas d'implémentation. Ainsi, la définition de la méthode est suivie d'un point-virgule au lieu d'un bloc de méthode normal. Les classes dérivées de la classe abstraite doivent implémenter toutes les méthodes abstraites. Lorsqu'une classe abstraite hérite d'une méthode virtuelle d'une classe de base, la classe abstraite peut substituer la méthode virtuelle par une méthode abstraite. Par exemple :  
  
 [!code-csharp[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]  
  
 Si une méthode `virtual` est déclarée `abstract`, elle demeure virtuelle pour toutes les classes qui héritent de la classe abstraite. Une classe qui hérite d’une méthode abstraite ne peut pas accéder à l’implémentation d’origine de la méthode. Dans l’exemple précédent, `DoWork` sur la classe F ne peut pas appeler `DoWork` sur la classe D. De cette manière, une classe abstraite peut forcer les classes dérivées à fournir de nouvelles implémentations de méthode pour les méthodes virtuelles.  
  
## <a name="sealed-classes-and-class-members"></a>Classes sealed et membres de classe  
 Les classes peuvent être déclarées comme [sealed](../../../csharp/language-reference/keywords/sealed.md) en plaçant le mot clé `sealed` avant la définition de classe. Exemple :  
  
 [!code-csharp[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]  
  
 Une classe sealed ne peut pas être utilisée comme une classe de base. Pour cette raison, elle ne peut pas également être une classe abstraite. Les classes sealed empêchent la dérivation. Étant donné qu'elles ne peuvent pas être utilisées comme une classe de base, quelques optimisations au moment de l'exécution permettent d'accélérer un peu les appels aux membres des classes sealed.  
  
 Une méthode, un indexeur, une propriété ou un événement sur une classe dérivée qui substitue un membre virtuel de la classe de base peut déclarer ce membre comme sealed. Cela nie l'aspect virtuel du membre pour toute classe dérivée ultérieure. Pour ce faire, mettez le mot clé `sealed` avant le mot clé [override](../../../csharp/language-reference/keywords/override.md) dans la déclaration de membre de classe. Par exemple :  
  
 [!code-csharp[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
- [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
- [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)  
- [Guide pratique pour définir des propriétés abstraites](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
