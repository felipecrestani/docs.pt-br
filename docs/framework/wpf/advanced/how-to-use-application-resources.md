---
title: Como usar recursos do aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: 4305c49c4322d164e2481c1508dda7c038c14694
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-application-resources"></a>Como usar recursos do aplicativo
Esse exemplo demonstra como usar recursos do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um arquivo de definição de aplicativo. O arquivo de definição de aplicativo define uma seção de recursos (um valor para o <xref:System.Windows.Application.Resources%2A> propriedade). Recursos definidos no nível do aplicativo podem ser acessados por todas as outras páginas que fazem parte do aplicativo. Nesse caso, o recurso é um estilo declarado. Como um estilo completo que inclui um modelo de controle pode ser demorado, este exemplo omite o modelo de controle que é definido dentro do <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> setter de propriedade do estilo.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 A exemplo a seguir mostra um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] página que referencia o recurso no nível do aplicativo que o exemplo anterior definiu. O recurso referenciado usando um [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) que especifica a chave de recurso exclusivo para o recurso solicitado. Nenhum recurso com chave de "GelButton" é encontrado na página atual, portanto, o escopo da pesquisa de recursos para o recurso solicitado continua além da página atual e até os recursos de nível de aplicativo definidos.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Consulte também  
 [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Visão geral do gerenciamento de aplicativos](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
