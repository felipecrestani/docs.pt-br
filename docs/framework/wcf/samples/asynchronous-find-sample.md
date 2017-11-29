---
title: "Exemplo de assíncrono encontrado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a793945906bb1a106916d59ff07ea813f38469d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-find-sample"></a><span data-ttu-id="816df-102">Exemplo de assíncrono encontrado</span><span class="sxs-lookup"><span data-stu-id="816df-102">Asynchronous Find Sample</span></span>
<span data-ttu-id="816df-103">Este exemplo mostra como usar a operação de localização assíncrona de um aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="816df-103">This sample shows how to use the asynchronous find operation from a client application.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="816df-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="816df-104">Sample Details</span></span>  
 <span data-ttu-id="816df-105">O benefício de seguir esse padrão de design é que o cliente seja notificado de forma assíncrona dos pontos de extremidade, como resultado da solicitação de localização.</span><span class="sxs-lookup"><span data-stu-id="816df-105">The benefit of following this design pattern is that the client is notified asynchronously of the endpoints located as a result of the find request.</span></span> <span data-ttu-id="816df-106">Para ver como isso funciona, abra o arquivo Client.cs.</span><span class="sxs-lookup"><span data-stu-id="816df-106">To see how this works, open the Client.cs file.</span></span> <span data-ttu-id="816df-107">Observe o <xref:System.ServiceModel.Discovery.DiscoveryClient> objeto tem dois delegados anexados para seus manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="816df-107">Note the <xref:System.ServiceModel.Discovery.DiscoveryClient> object has two delegates attached to its event handlers.</span></span> <span data-ttu-id="816df-108">Um delegado é chamado quando um <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> é gerado e outro chamado sempre que uma <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> é gerado.</span><span class="sxs-lookup"><span data-stu-id="816df-108">One delegate is called when a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is raised and another is called each time a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> event is raised.</span></span> <span data-ttu-id="816df-109">O exemplo mostra como você pode utilizar esse padrão em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="816df-109">The sample shows how you can utilize this pattern in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="816df-110">Este exemplo usa pontos de extremidade HTTP e para executar, ACLs adequadas de URL deve ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="816df-110">This sample uses HTTP endpoints and to run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="816df-111">[Configurando HTTP e HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="816df-111"> [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="816df-112">Executando o seguinte comando em um privilégio elevado deve adicionar as ACLs corretas.</span><span class="sxs-lookup"><span data-stu-id="816df-112">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="816df-113">Convém substituir seu domínio e nome de usuário para os argumentos a seguir se o comando não funcionar como está.</span><span class="sxs-lookup"><span data-stu-id="816df-113">You may want to substitute your domain and username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="816df-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="816df-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="816df-115">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o AsyncFind.sln.</span><span class="sxs-lookup"><span data-stu-id="816df-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the AsyncFind.sln.</span></span>  
  
2.  <span data-ttu-id="816df-116">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="816df-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="816df-117">Abra um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando e navegue até o diretório \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug ou \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug e executar Service.exe.</span><span class="sxs-lookup"><span data-stu-id="816df-117">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug or \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug directory and run Service.exe.</span></span>  
  
4.  <span data-ttu-id="816df-118">Depois que o serviço foi iniciado, navegue até o diretório de WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug ou \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug e executar Client.exe.</span><span class="sxs-lookup"><span data-stu-id="816df-118">After the service has started, navigate to the \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug or WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug directory and run Client.exe.</span></span>  
  
5.  <span data-ttu-id="816df-119">Observe que o cliente é capaz de localizar e chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="816df-119">Observe the client is able to locate and call the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="816df-120">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="816df-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="816df-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="816df-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="816df-122">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="816df-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="816df-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="816df-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a><span data-ttu-id="816df-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="816df-124">See Also</span></span>