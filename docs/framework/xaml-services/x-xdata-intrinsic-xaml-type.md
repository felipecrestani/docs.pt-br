---
title: Tipo intrínseco x:XData (XAML)
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: 3a16379fd6104342529723bf6d0bc9fb4762cf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="xxdata-intrinsic-xaml-type"></a>Tipo intrínseco x:XData (XAML)
Habilita o posicionamento de ilhas de dados dentro de uma produção XAML. Elementos XML no `x:XData` não devem ser tratados por processadores XAML, como se fossem uma parte da ação padrão do namespace XAML ou qualquer outro namespace XAML. `x:XData` pode conter XML bem formado arbitrário.  
  
## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`elementDataRoot`|O elemento raiz único da ilha de dados incluídos. Para a maioria dos consumidores eventual, XML que não tem uma única raiz é considerado inválido. Em particular, uma única raiz é necessária se o `x:XData` destina-se como uma fonte de dados XML para WPF ou muitas outras tecnologias que usam fontes de XML para associação de dados.|  
|`[elementData]`|Opcional. XML que representa os dados XML. Qualquer número de elementos pode ser contido como dados de elemento e elementos aninhados podem estar contidos em outros elementos; No entanto, se aplicam às regras gerais do XML.|  
  
## <a name="remarks"></a>Comentários  
 Os elementos de uma `x:XData` objeto pode declarar novamente todos os possíveis namespaces e prefixos do recipiente XMLDOM dentro dos dados.  
  
 Acesso programático aos dados XML e o `x:XData` tipo intrínseco do XAML é possível em serviços XAML do .NET Framework por meio de <xref:System.Windows.Markup.XData> classe.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 O `x:XData` objeto é usado principalmente como um objeto filho de um <xref:System.Windows.Data.XmlDataProvider>, ou como alternativa, como o objeto filho do <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> propriedade (em XAML, isso é geralmente expresso na sintaxe de elemento de propriedade).  
  
 Os dados normalmente devem redefinir o namespace XML base dentro da ilha de dados para um novo namespace de XML padrão (definido como uma cadeia de caracteres vazia). Isso é mais fácil para ilhas de dados simples, porque o <xref:System.Windows.Data.Binding.XPath%2A> expressões que são usadas para referenciar e associar os dados podem evitar a inclusão de prefixos. Ilhas de dados mais complexas podem definir vários prefixos para os dados e usar um prefixo específico para o namespace XML na raiz. Nesse caso, todos os <xref:System.Windows.Data.Binding.XPath%2A> referências de expressão devem incluir o prefixo mapeado em namespace apropriado. Para obter mais informações, consulte [Visão geral de vinculação de dados](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Tecnicamente, `x:XData` pode ser usado como o conteúdo de qualquer propriedade do tipo <xref:System.Xml.Serialization.IXmlSerializable>. No entanto, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> é a implementação somente destacada.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Data.XmlDataProvider>  
 [Visão geral da vinculação de dados](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Extensão de marcação de associação](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
