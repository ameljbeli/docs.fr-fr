---
title: "Procédure : Implémenter de manière explicite des membres d'interface - Guide de programmation C#"
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 11ef4eb3e4da0166ae4753b8028edb217f2a487e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236926"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Procédure : Implémenter de manière explicite des membres d'interface (Guide de programmation C#)
Cet exemple déclare une [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions` et une classe `Box`, qui implémente de manière explicite les membres d’interface `getLength` et `getWidth`. Les membres sont accessibles via l’instance d’interface `dimensions`.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a>Programmation fiable  
  
-   Notez que les lignes suivantes de la méthode `Main` sont commentées car elles produiraient des erreurs de compilation. Un membre d’interface qui est implémenté de façon explicite n’est pas accessible à partir d’une instance de [classe](../../../csharp/language-reference/keywords/class.md) :  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   Notez également que les lignes suivantes de la méthode `Main` impriment correctement les dimensions de la zone, car les méthodes sont appelées à partir d’une instance de l’interface :  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
- [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Interfaces](../../../csharp/programming-guide/interfaces/index.md)  
- [Guide pratique pour implémenter de manière explicite des membres de deux interfaces](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
