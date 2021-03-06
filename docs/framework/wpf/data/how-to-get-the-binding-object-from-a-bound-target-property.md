---
title: Como obter o objeto de associação de uma propriedade de destino associada
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 0bc793d4c95f8919517a83e434cf795e971dcd32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Como obter o objeto de associação de uma propriedade de destino associada
Este exemplo mostra como obter o objeto de associação de uma propriedade de associação de dados de destino.  
  
## <a name="example"></a>Exemplo  
 Você pode fazer o seguinte para obter o <xref:System.Windows.Data.Binding> objeto:  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  Você deve especificar a propriedade de dependência para a associação que você deseja pois é possível que mais de uma propriedade do objeto de destino esteja usando associação de dados.  
  
 Como alternativa, você pode obter o <xref:System.Windows.Data.BindingExpression> e, em seguida, obter o valor da <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> propriedade.  
  
 Para o exemplo completo, consulte [exemplo de validação de associação](http://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
>  Se a associação for uma <xref:System.Windows.Data.MultiBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Se for um <xref:System.Windows.Data.PriorityBinding>, use <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Se você não tiver certeza se a propriedade de destino está associada usando um <xref:System.Windows.Data.Binding>, um <xref:System.Windows.Data.MultiBinding>, ou um <xref:System.Windows.Data.PriorityBinding>, você pode usar <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Criar uma associação no código](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
