---
title: Expressions d'objet
description: Découvrez comment utiliser F# expressions d’objet lorsque vous souhaitez éviter le code supplémentaire et la surcharge requise pour créer un nouveau type nommé.
ms.date: 05/16/2016
ms.openlocfilehash: cb15983543fde2459c589b3de2554575d73db686
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613919"
---
# <a name="object-expressions"></a>Expressions d'objet

Un *objet expression* est une expression qui crée une nouvelle instance d’un type d’objet créé dynamiquement, anonyme qui est basée sur un type existant de base, une interface ou un ensemble d’interfaces.

## <a name="syntax"></a>Syntaxe

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, le *typename* représente un type de classe existant ou un type d’interface. *type-params* décrit les paramètres de type générique facultatifs. Le *arguments* sont utilisés uniquement pour les types de classe, qui nécessitent des paramètres de constructeur. Le *-des définitions de membre* sont des remplacements des méthodes de classe de base ou des implémentations de méthodes abstraites d’une classe de base ou une interface.

L’exemple suivant illustre les différents types d’expressions d’objet.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>À l’aide d’Expressions d’objet

Vous utilisez des expressions d’objet lorsque vous souhaitez éviter le code supplémentaire et la surcharge qui est nécessaire pour créer un nouveau type nommé. Si vous utilisez des expressions d’objet pour réduire le nombre de types créés dans un programme, vous pouvez réduire le nombre de lignes de code et empêcher la prolifération inutile de types. Au lieu de créer de nombreux types pour gérer des situations spécifiques seulement, vous pouvez utiliser une expression d’objet qui personnalise un type existant ou fournit une implémentation appropriée d’une interface pour le cas spécifique à portée de main.

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)