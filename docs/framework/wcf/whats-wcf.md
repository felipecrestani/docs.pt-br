---
title: O que é o Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: e49b393b9dd09a513066a6cb3612ad9f938e9adb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="what-is-windows-communication-foundation"></a>O que é o Windows Communication Foundation
Windows Communication Foundation (WCF) é uma estrutura para criar aplicativos orientados a serviços. Usando o WCF, você pode enviar dados como mensagens assíncronas do ponto de extremidade de um serviço para outro. Um ponto de extremidade de serviço pode ser parte de um serviço disponível continuamente hospedado pelo IIS, ou pode ser um serviço hospedado em um aplicativo. Um ponto de extremidade pode ser um cliente de um serviço que solicita dados de um ponto de extremidade de serviço. As mensagens podem ser simples como um único caractere ou uma palavra enviada como XML ou complexo como um fluxo de dados binários. Alguns cenários de exemplo incluem:  
  
-   Um serviço seguro para processar transações comerciais.  
  
-   Um serviço que fornece dados atuais para outros, como um relatório de tráfego ou outro serviço de monitoramento.  
  
-   Um serviço de chat que permite que duas pessoas se comuniquem ou troquem dados em tempo real.  
  
-   Um aplicativo do painel que pesquisa um ou mais serviços para dados e os apresenta em uma apresentação lógica.  
  
-   Expõe um fluxo de trabalho implementado usando o Windows Workflow Foundation como um serviço WCF.  
  
-   Um aplicativo do Silverlight que pesquisa um serviço para os feeds de dados mais recentes.  
  
 Ao criar esses aplicativos era possível antes da existência do WCF, o WCF torna o desenvolvimento de pontos de extremidade mais fácil. Em resumo, o WCF foi projetado para oferecer uma abordagem gerenciável para a criação de serviços Web e clientes de serviço Web.  
  
## <a name="features-of-wcf"></a>Recursos do WCF  
 O WCF inclui o seguinte conjunto de recursos. Para obter mais informações, consulte [detalhes do recurso WCF](../../../docs/framework/wcf/feature-details/index.md).  
  
-   **Orientação de serviço**  
  
     O benefício de usar padrões WS é WCF permite que você crie *orientada a serviços* aplicativos. A arquitetura orientada a serviços (SOA) é a confiança nos serviços Web para enviar e receber dados. Os serviços têm a vantagem geral de serem fracamente acoplados em vez de embutidos no código de um aplicativo para outro. Uma relação fracamente acoplada significa que qualquer cliente criado em qualquer plataforma pode se conectar a qualquer serviço contanto que os contratos essenciais sejam atendidos.  
  
-   **Interoperabilidade**  
  
     O WCF implementa modernos padrões para interoperabilidade de serviço da Web. Para obter mais informações sobre os padrões com suporte, consulte [interoperabilidade e integração](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).  
  
-   **Vários padrões de mensagens**  
  
     As mensagens são trocadas em um dos vários padrões. O padrão mais comum é o padrão de solicitação/resposta, onde um ponto de extremidade solicita dados de um segundo ponto de extremidade. O segundo ponto de extremidade responde. Há outros padrões como uma mensagem unidirecional em que um único ponto de extremidade envia uma mensagem sem nenhuma expectativa de resposta. Um padrão mais complexo é o padrão de troca duplex onde dois pontos de extremidade estabelecem uma conexão de dados e enviar para frente e para trás, semelhante a um programa de mensagens instantâneas. Para obter mais informações sobre como implementar a troca de mensagens diferentes padrões de uso do WCF consulte [contratos](../../../docs/framework/wcf/feature-details/contracts.md).  
  
-   **Metadados de serviço**  
  
     O WCF dá suporte a metadados de serviço de publicação usando formatos especificados em padrões do setor como WSDL, esquema XML e WS-Policy. Esses metadados podem ser usado para gerar automaticamente e configurar clientes para acessar os serviços do WCF. Os metadados podem ser publicados em HTTP e HTTPS ou usando o padrão Metadata Exchange do Serviço Web. Para obter mais informações, consulte [metadados](../../../docs/framework/wcf/feature-details/metadata.md).  
  
-   **Contratos de dados**  
  
     Porque o WCF é criado usando o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ele também inclui código compatível com métodos de fornecimento de contratos que você deseja impor. Um dos tipos universais de contratos é o contrato de dados. Essencialmente, à medida que você codifica o serviço usando Visual C# ou Visual Basic, a maneira mais fácil de manipular dados é criando classes que representam uma entidade de dados com as propriedades que pertencem à entidade de dados. O WCF inclui um sistema abrangente para trabalhar com dados dessa maneira fácil. Assim que você tiver criado as classes que representam dados, o serviço gera automaticamente os metadados que permitem que os clientes sejam compatíveis com os tipos de dados que você criou. Para obter mais informações, consulte [usando contratos de dados](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
-   **Segurança**  
  
     As mensagens podem ser criptografadas para proteger a privacidade e você pode exigir que os usuários se autentiquem antes de terem permissão de receber mensagens. A segurança pode ser implementada usando padrões conhecidos como SSL ou WS-SecureConversation. Para obter mais informações, consulte [Segurança](../../../docs/framework/wcf/feature-details/security.md).  
  
-   **Várias codificações e transportes**  
  
     As mensagens podem ser enviadas de qualquer um dos vários protocolos e codificações internos de transporte. Mais comum de protocolo e codificação é enviar texto codificado mensagens SOAP usando o protocolo HTTP (HyperText Transfer) para uso na World Wide Web. Como alternativa, o WCF permite que você envie mensagens sobre TCP, pipes nomeados ou MSMQ. Essas mensagens podem ser codificadas como texto ou usando um formato binário otimizado.  Os dados binários podem ser enviados com eficiência usando o padrão MTOM. Se nenhum dos transportes ou codificações fornecidos atender às suas necessidades, você poderá criar seu próprio transporte ou codificação personalizado. Para obter mais informações sobre os transportes e codificações com suporte do WCF, consulte [transportes](../../../docs/framework/wcf/feature-details/transports.md).  
  
-   **Mensagens confiáveis e em fila**  
  
     WCF dá suporte à troca de mensagens confiável usando sessões confiáveis implementado sobre mensagens WS-Reliable e usar o MSMQ. Para obter mais informações sobre o suporte de sistema de mensagens confiável e em fila no WCF, consulte [sessões confiáveis e filas](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).  
  
-   **Mensagens duráveis**  
  
     Uma mensagem é durável porque nunca é perdida devido a um rompimento na comunicação. As mensagens em um padrão durável são sempre salvas em um banco de dados. Se um rompimento ocorrer, o banco de dados permitirá que você retome a troca de mensagens quando a conexão for restaurada. Você também pode criar uma mensagem durável usando o Windows Workflow Foundation (WF). Para obter mais informações, consulte [serviços de fluxo de trabalho](../../../docs/framework/wcf/feature-details/workflow-services.md).  
  
-   **Transações**  
  
     O WCF também oferece suporte a transações usando um dos três modelos de transação: WS-AtomicTtransactions, as APIs no namespace <xref:System.Transactions> e Coordenador de transações distribuídas da Microsoft. Para obter mais informações sobre transações no WCF Consulte suporte [transações](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).  
  
-   **AJAX e suporte a REST**  
  
     REST é um exemplo de uma tecnologia Web 2.0 em evolução. WCF pode ser configurado para processar dados XML "simples" que não são encapsulados em um envelope SOAP. WCF também pode ser estendido para oferecer suporte a formatos XML específicos, como formatos de XML não mesmo, como JSON JavaScript Object Notation () e ATOM um popular RSS (padrão).  
  
-   **Extensibilidade**  
  
     A arquitetura do WCF tem um número de pontos de extensibilidade. Se o recurso adicional for necessário, há inúmeros pontos de entrada que permitem que você personalize o comportamento de um serviço. Para obter mais informações sobre a extensibilidade disponível pontos consulte [estendendo o WCF](../../../docs/framework/wcf/extending/index.md).  
  
## <a name="wcf-integration-with-other-microsoft-technologies"></a>Integração WCF com outras tecnologias da Microsoft  
 O WCF é uma plataforma flexível. Devido a essa flexibilidade extrema, o WCF também é usado em vários outros produtos da Microsoft. Compreendendo os fundamentos do WCF, você tem uma vantagem imediata se você também usar qualquer um desses produtos.  
  
 A primeira tecnologia emparelhar com o WCF foi o Windows Workflow Foundation (WF). Fluxos de trabalho simplificam o desenvolvimento de aplicativo encapsular as etapas no fluxo de trabalho como "atividades". Na primeira versão do Windows Workflow Foundation, um desenvolvedor precisava criar um host para o fluxo de trabalho. A próxima versão do Windows Workflow Foundation foi integrada com o WCF. Que pode facilmente ser hospedado em um serviço WCF; qualquer fluxo de trabalho Você pode fazer isso escolhendo automaticamente WCF/WF um tipo de projeto em [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
 Microsoft BizTalk Server R2 também utiliza o WCF como uma tecnologia de comunicação. O BizTalk é criado para receber e transformar dados de um formato padronizado para outro. As mensagens devem ser entregues a sua caixa de mensagens central onde a mensagem pode ser transformada usando um mapeamento restrito ou usando um dos recursos de BizTalk como o mecanismo de fluxo de trabalho. BizTalk agora pode usar o adaptador WCF linha de negócios (LOB) para entregar mensagens para a caixa de mensagem.  
  
 O Microsoft Silverlight é uma plataforma para criar aplicativos Web interoperáveis, aplicativos Web avançados que permitem que os desenvolvedores criem sites voltados para mídia (como a streaming de vídeo). Começando com a versão 2, Silverlight incorporou WCF como uma tecnologia de comunicação para conectar os aplicativos Silverlight para pontos de extremidade do WCF.  
  
 O [!INCLUDE[dublin](../../../includes/dublin-md.md)] servidor de aplicativos foi desenvolvido especificamente para implantação e gerenciamento de aplicativos que usam o WCF para comunicação. O [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] inclui opções de configuração e ferramentas avançadas projetadas especificamente para aplicativos habilitados para WCF.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel>  
 [Conceitos fundamentais do Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)  
 [Arquitetura do Windows Communication Foundation](../../../docs/framework/wcf/architecture.md)  
 [Diretrizes e práticas recomendadas](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
 [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Guia da documentação](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Programação básica do WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Amostras do Windows Communication Foundation](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
