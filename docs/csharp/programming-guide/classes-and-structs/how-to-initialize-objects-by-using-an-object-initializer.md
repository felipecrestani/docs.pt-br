---
title: Como inicializar objetos usando um inicializador de objeto (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8e9130983aabe991660ff4cca90b33609f86c158
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Como inicializar objetos usando um inicializador de objeto (Guia de Programação em C#)
Você pode usar os inicializadores de objeto para inicializar objetos de tipo de maneira declarativa, sem invocar explicitamente um construtor para o tipo.  
  
 Os exemplos a seguir mostram como usar os inicializadores de objeto com objetos nomeados. O compilador processa os inicializadores de objetos ao acessar, primeiro, o construtor de instância padrão e, em seguida, processar as inicializações de membro. Portanto, se o construtor padrão for declarado como `private` na classe, os inicializadores de objeto que exigem acesso público falharão.  
  
 Se você estiver definindo um tipo anônimo, é necessário usar um inicializador de objeto. Para obter mais informações, consulte [Como retornar subconjuntos de propriedades de elementos em uma consulta](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como inicializar um novo tipo `StudentName`, usando inicializadores de objeto.  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como inicializar uma coleção de tipos `StudentName`, usando um inicializador de coleção. Observe que um inicializador de coleção é uma série de inicializadores de objeto separados por vírgulas.  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para executar esse código, copie e cole a classe em um projeto de aplicativo de console do Visual C# que foi criado no Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
