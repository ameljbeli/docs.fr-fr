---
title: 'Procédure : Déclarer, instancier et utiliser un délégué - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: bc9fc81a74d438aca57779fa565fdbeba3968087
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237062"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Procédure : Déclarer, instancier et utiliser un délégué (Guide de programmation C#)
Dans C# 1.0 et versions ultérieures, vous pouvez déclarer des délégués comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 C# 2.0 offre un moyen plus simple d’écrire la déclaration précédente, comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 Dans C# 2.0 et versions ultérieures, vous pouvez aussi utiliser une méthode anonyme pour déclarer et initialiser un [délégué](../../../csharp/language-reference/keywords/delegate.md), comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 Dans C# 3.0 et versions ultérieures, vous pouvez aussi déclarer et instancier des délégués à l’aide d’une expression lambda, comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 Pour plus d’informations, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 L’exemple suivant illustre la déclaration, l’instanciation et l’utilisation d’un délégué. La classe `BookDB` encapsule une base de données de librairie qui tient à jour un inventaire des livres. Elle expose une méthode, `ProcessPaperbackBooks`, qui recherche tous les livres de poche dans la base de données et appelle un délégué pour chacun d’entre eux. Le type `delegate` qui est utilisé se nomme `ProcessBookDelegate`. La classe `Test` utilise cette classe pour imprimer les titres et le prix moyen des livres de poche.  
  
 L’utilisation des délégués favorise une bonne séparation des fonctionnalités entre la base de données de librairie et le code client. Le code client n’a aucune connaissance de la façon dont les livres sont stockés, ni de la façon dont le code librairie trouve les livres de poche. Le code librairie n’a aucune connaissance du traitement effectué sur les livres de poche une fois qu’il les a trouvés.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a>Programmation fiable  
  
-   Déclaration d’un délégué.  
  
     L’instruction suivante déclare un nouveau type délégué.  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     Chaque type délégué décrit le nombre et les types des arguments, ainsi que le type de la valeur de retour des méthodes qu’il peut encapsuler. Chaque fois qu’un nouvel ensemble de types d’arguments ou de types de valeur de retour est nécessaire, un nouveau type délégué doit être déclaré.  
  
-   Instanciation d’un délégué.  
  
     Une fois que vous avez déclaré un type délégué, vous devez créer un objet délégué et l’associer à une méthode particulière. Pour cela, dans l’exemple précédent vous passez la méthode `PrintTitle` à la méthode `ProcessPaperbackBooks`, comme illustré dans l’exemple suivant :  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     Cela crée un nouvel objet délégué associé à la méthode [statique](../../../csharp/language-reference/keywords/static.md) `Test.PrintTitle`. De même, la méthode non statique `AddBookToTotal` sur l’objet `totaller` est passée comme dans l’exemple suivant :  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     Dans les deux cas, un nouvel objet délégué est passé à la méthode `ProcessPaperbackBooks`.  
  
     Une fois un délégué créé, la méthode à laquelle il est associé ne change jamais. Les objets délégué sont immuables.  
  
-   Appel d’un délégué.  
  
     Une fois créé, un objet délégué est généralement passé à un autre code qui appellera le délégué. Pour appeler un objet délégué, vous devez utiliser le nom de l’objet délégué, suivi des arguments entre parenthèses à passer au délégué. Voici un exemple d’appel de délégué :  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     Vous pouvez appeler un délégué de manière synchrone, comme dans cet exemple, ou de manière asynchrone à l’aide des méthodes `BeginInvoke` et `EndInvoke`.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
- [Événements](../../../csharp/programming-guide/events/index.md)  
- [Délégués](../../../csharp/programming-guide/delegates/index.md)
