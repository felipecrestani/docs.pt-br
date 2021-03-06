---
title: '#undef (Referência de C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7a3c162c0ecb8bb39cc13a34dcd15fa3ce96ebb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="undef-c-reference"></a>#undef (Referência de C#)
`#undef` permite excluir as definições de um símbolo, de modo que, usando o símbolo como a expressão em uma diretiva [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), a expressão será avaliada como `false`.  
  
 Um símbolo pode ser definido com a diretiva [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) ou com a opção do compilador [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md). A diretiva `#undef` deve ser exibida no arquivo antes de usar qualquer instrução que também não sejam diretivas.  
  
## <a name="example"></a>Exemplo  
  
```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass   
{  
    static void Main()   
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```  
  
 **DEBUG não está definido**  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
