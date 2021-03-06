---
title: Expressões de objeto (F#)
description: 'Aprenda a usar expressões de objeto do F # quando desejar evitar o código extra e sobrecarga necessária para criar um novo tipo nomeado.'
ms.date: 05/16/2016
ms.openlocfilehash: fed78e2be52838eedf55759b195696f1210a8a20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="object-expressions"></a>Expressões de objeto

Um *objeto expressão* é uma expressão que cria uma nova instância de um tipo de objeto criado dinamicamente e anônimo que se baseia em um tipo base existente, uma interface ou um conjunto de interfaces.


## <a name="syntax"></a>Sintaxe

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

## <a name="remarks"></a>Comentários
Na sintaxe anterior, o *typename* representa um tipo de classe existente ou um tipo de interface. *parâmetros de tipo* descreve os parâmetros de tipo genérico opcional. O *argumentos* são usadas apenas para tipos de classe, que exigem parâmetros do construtor. O *definições de membro* são substituições de métodos de classe base ou implementações de métodos abstratos de uma classe base ou uma interface.

O exemplo a seguir ilustra os diferentes tipos de expressões de objeto.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>Usando expressões de objeto
Você usa expressões de objeto quando você deseja evitar a sobrecarga que é necessário para criar um novo tipo nomeado e código extra. Se você usar expressões de objeto para minimizar o número de tipos criada em um programa, você pode reduzir o número de linhas de código e evitar a proliferação desnecessária de tipos. Em vez de criar muitos tipos apenas para lidar com situações específicas, você pode usar uma expressão de objeto que personaliza um tipo existente ou fornece uma implementação apropriada de uma interface para o caso específico em questão.


## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)
