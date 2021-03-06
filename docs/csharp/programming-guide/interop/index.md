---
title: Interoperabilidade (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e854c51bd80809b92bb538475a407422b2eba7c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="interoperability-c-programming-guide"></a>Interoperabilidade (Guia de Programação em C#)
A interoperabilidade permite que você mantenha e aproveite os investimentos existentes em código não gerenciado. O código que é executado sob o controle do CLR (Common Language Runtime) é chamado de *código gerenciado*, e o código que é executado fora do CLR é chamado de *código não gerenciado*. COM, COM+, componentes do C++, componentes do ActiveX e a API do Microsoft Win32 são exemplos de código não gerenciado.  
  
 O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] habilita a interoperabilidade com código não gerenciado por meio de serviços de invocação de plataforma, o namespace <xref:System.Runtime.InteropServices>, a interoperabilidade com C++ e a interoperabilidade COM.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral sobre interoperabilidade](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 Descreve métodos para fins de interoperabilidade entre código gerenciado em C# e código não gerenciado.  
  
 [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Descreve os recursos que são introduzidos no Visual C# para facilitar a programação do Office.  
  
 [Como usar propriedades indexadas na programação para interoperabilidade COM](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Descreve como usar propriedades indexadas para acesso propriedades COM que têm parâmetros.  
  
 [Como usar invocação de plataforma para executar um arquivo wave](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Descreve como usar os serviços de invocação de plataforma para reproduzir um arquivo de som .wav no sistema operacional Windows.  
  
 [Passo a passo: programação do Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Mostra como criar uma planilha do Excel e um documento do Word com um link para a planilha.  
  
 [Exemplo de classe COM](../../../csharp/programming-guide/interop/example-com-class.md)  
 Demonstra como expor uma classe C# como um objeto COM.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Interoperação com código não gerenciado](../../../../docs/framework/interop/index.md)  
 [Passo a passo: programação do Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
