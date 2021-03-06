---
title: Guia de Introdução Tutorial1
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 64d9fc09d56c417c2226d030ef6f5ee7204c4eb6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="getting-started-tutorial"></a>Guia de introdução ao tutorial
Os tópicos contidos nesta seção destinam-se a dar exposição rápida para o Windows Communication Foundation (WCF) experiência em programação. Eles devem ser concluídos na ordem da lista que se encontra na parte inferior deste tópico. Trabalhando com este tutorial fornece um entendimento introdutório das etapas necessárias para criar o cliente e o serviço WCF aplicativos. Um serviço expõe um ou mais pontos de extremidade, sendo que cada um deles expõe uma ou mais operações de serviço. O *ponto de extremidade* de um serviço Especifica um endereço onde o serviço pode ser encontrado, uma associação que contém as informações que descrevem como um cliente deve se comunicar com o serviço e um contrato que define a funcionalidade fornecido pelo serviço para seus clientes.  
  
 Após concluir a sequência de tópicos neste tutorial, você terá um serviço em execução e um cliente que chama o serviço. Os três primeiros tópicos descrevem como definir um contrato de serviço, como implementá-lo e como hospedar o serviço. O serviço criado é auto-hospedado em um aplicativo de console. Os serviços também podem ser hospedados no IIS (Serviços de Informações da Internet). Para obter mais informações sobre como fazer isso, consulte [como: hospedar um serviço WCF no IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md). O serviço está configurado no código; no entanto, os serviços também podem ser configurados em um arquivo de configuração. Para obter mais informações sobre como usar um arquivo de configuração, consulte [Configurando serviços usando arquivos de configuração](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).  
  
 Os três tópicos a seguir descrevem como criar um proxy do cliente, configurar o aplicativo cliente e usar o proxy do cliente para chamar a operação de serviço exposta pelo serviço. Os serviços publicam metadados que definem as informações que um aplicativo cliente precisa para se comunicar com o serviço. O [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] automatiza o processo de acesso a esses metadados e usa-o para construir e configurar o aplicativo cliente para o serviço. Se você não estiver usando [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], você pode usar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para construir e configurar o aplicativo cliente para o serviço.  
  
 Todos os tópicos nesta seção supõem que você está usando o Visual Studio 2011 como o ambiente de desenvolvimento. Se você estiver usando outro ambiente de desenvolvimento, ignore as instruções específicas do Visual Studio.  
  
> [!NOTE]
>  Se você estiver executando [!INCLUDE[wv](../../../includes/wv-md.md)] ou versões posteriores do sistema operacional Windows, você deve iniciar o Visual Studio no menu Iniciar e clique direito no Visual Studio 2011 e selecionando **executar como administrador**. Para iniciar o Visual Studio 2011 sempre como um administrador, você pode criar um atalho, clique com botão direito no atalho, selecione Propriedades, selecione o **compatibilidade** guia e verifique o **executar este programa como administrador** caixa de seleção. Quando você iniciar o Visual Studio 2011 com esse atalho, ele sempre será executado como administrador.  
  
 Para aplicativos de exemplo que podem ser baixados em seu disco rígido e executar, consulte os tópicos [exemplos do Windows Communication Foundation](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91). Este tópico, em particular, consulte o [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
 Para obter informações mais detalhadas sobre a criação de serviços e clientes, consulte [básicas de programação WCF](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 Descreve como criar um contrato WCF usando uma interface definida pelo usuário. O contrato define a funcionalidade exposta pelo serviço.  
  
 [Como implementar um contrato de serviço](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 Descreve como implementar um contrato de serviço. Após ser definido, um contrato deve ser implementado com uma classe de serviço.  
  
 [Como hospedar e executar um serviço básico](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 Descreve como configurar um ponto de extremidade para o serviço no código e como hospedar o serviço em um aplicativo de console. Para se tornar ativo, um serviço deve ser configurado e hospedado em um ambiente de tempo de execução. Esse ambiente cria o serviço e controla seu contexto e tempo de vida.  
  
 [Como criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 Descreve como recuperar os metadados usados para criar um proxy de cliente do WCF do serviço WCF. Esse processo usa a funcionalidade de Adicionar Referência de Serviço no Visual Studio 2011.  
  
 [Como configurar um cliente](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 Descreve como configurar um cliente WCF. A configuração do cliente requer a especificação do ponto de extremidade que o cliente usa para acessar o serviço.  
  
 [Como usar um cliente](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 Descreve como usar o proxy do cliente WCF para chamar operações de serviço.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Amostras do Windows Communication Foundation](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [Ciclo de vida de programação básica](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral conceitual](../../../docs/framework/wcf/conceptual-overview.md)  
 [Guia da documentação](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [O que é o Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Detalhes de recursos do WCF](../../../docs/framework/wcf/feature-details/index.md)
