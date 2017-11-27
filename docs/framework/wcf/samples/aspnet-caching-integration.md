---
title: "Integração de cache ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8830f1c19b7a91d6c22d3b5955624c7d8a86f5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="cc108-102">Integração de cache ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cc108-102">ASP.NET Caching Integration</span></span>
<span data-ttu-id="cc108-103">Este exemplo demonstra como utilizar o cache de saída do ASP.NET com o modelo de programação WCF WEB HTTP.</span><span class="sxs-lookup"><span data-stu-id="cc108-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="cc108-104">Consulte o [serviço básico do recurso](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo para uma versão auto-hospedado deste cenário que aborda a implementação de serviço em camadas.</span><span class="sxs-lookup"><span data-stu-id="cc108-104">Please see the [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) sample for a self-hosted version of this scenario that discusses the service implementation in depth.</span></span> <span data-ttu-id="cc108-105">Este tópico enfoca o recurso de integração de cache de saída do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cc108-105">This topic focuses on the ASP.NET output cache integration feature.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="cc108-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="cc108-106">Demonstrates</span></span>  
 <span data-ttu-id="cc108-107">Integração com o Cache de saída ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cc108-107">Integration with the ASP.NET Output Cache</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cc108-108">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cc108-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cc108-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cc108-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cc108-110">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="cc108-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc108-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cc108-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a><span data-ttu-id="cc108-112">Discussão</span><span class="sxs-lookup"><span data-stu-id="cc108-112">Discussion</span></span>  
 <span data-ttu-id="cc108-113">O exemplo usa o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ASP.NET de utilizar o cache de saída com o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span><span class="sxs-lookup"><span data-stu-id="cc108-113">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="cc108-114">O <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> é aplicada às operações de serviço e fornece o nome de um perfil de cache em um arquivo de configuração que deve ser aplicado às respostas da operação de determinada.</span><span class="sxs-lookup"><span data-stu-id="cc108-114">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>  
  
 <span data-ttu-id="cc108-115">No arquivo Service.cs do projeto de serviço de exemplo, tanto o `GetCustomer` e `GetCustomers` operações são marcadas com o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, que fornece o nome do perfil de cache "CacheFor60Seconds".</span><span class="sxs-lookup"><span data-stu-id="cc108-115">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="cc108-116">No arquivo Web. config do projeto de serviço, o perfil de cache "CacheFor60Seconds" é fornecido com o <`caching`> elemento <`system.web`>.</span><span class="sxs-lookup"><span data-stu-id="cc108-116">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="cc108-117">Para este perfil de cache, o valor de `duration` atributo é "60", que as respostas associadas ao perfil são armazenados em cache no cache de saída ASP.NET por 60 segundos.</span><span class="sxs-lookup"><span data-stu-id="cc108-117">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="cc108-118">Além disso, para este perfil de cache, o `varmByParam` atributo é definido como "formato" caso solicitações com valores diferentes para o `format` consulta parâmetro de cadeia de caracteres, suas respostas em cache separadamente.</span><span class="sxs-lookup"><span data-stu-id="cc108-118">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="cc108-119">Por fim, o perfil de cache `varyByHeader` atributo é definido como "Aceitar", para solicitações com diferentes valores de cabeçalho Accept tenham suas respostas em cache separadamente.</span><span class="sxs-lookup"><span data-stu-id="cc108-119">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>  
  
 <span data-ttu-id="cc108-120">Program.cs no projeto do cliente demonstra como o cliente pode ser criados usando <xref:System.Net.HttpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="cc108-120">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="cc108-121">Observe que isso é apenas uma maneira de acessar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="cc108-121">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="cc108-122">Também é possível acessar o serviço usando outras classes do .NET Framework, como o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fábrica de canais e <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="cc108-122">It is also possible to access the service using other .NET Framework classes like the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="cc108-123">Outros exemplos no SDK (como o [serviço básico de HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) exemplo e o [seleção automática de formato](../../../../docs/framework/wcf/samples/automatic-format-selection.md) exemplo) ilustram como usar essas classes para se comunicar com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="cc108-123">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample and the [Automatic Format Selection](../../../../docs/framework/wcf/samples/automatic-format-selection.md) sample) illustrate how to use these classes to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
## <a name="to-run-the-sample"></a><span data-ttu-id="cc108-124">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="cc108-124">To run the sample</span></span>  
 <span data-ttu-id="cc108-125">O exemplo consiste em três projetos:</span><span class="sxs-lookup"><span data-stu-id="cc108-125">The sample consists of three projects:</span></span>  
  
-   <span data-ttu-id="cc108-126">**Serviço**: projeto de um aplicativo da Web que inclui um serviço HTTP do WCF hospedado no ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cc108-126">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>  
  
-   <span data-ttu-id="cc108-127">**Cliente**: um projeto de aplicativo de console que faz chamadas ao serviço.</span><span class="sxs-lookup"><span data-stu-id="cc108-127">**Client**: A console application project that makes calls to the service.</span></span>  
  
-   <span data-ttu-id="cc108-128">**Comuns**: uma biblioteca compartilhada que contém o tipo de cliente usado pelo cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="cc108-128">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>  
  
 <span data-ttu-id="cc108-129">Quando o aplicativo de console do cliente é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes entre as respostas para a janela do console.</span><span class="sxs-lookup"><span data-stu-id="cc108-129">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="cc108-130">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="cc108-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="cc108-131">Abra a solução para o exemplo de integração de cache ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cc108-131">Open the solution for the ASP.NET Caching Integration Sample.</span></span>  
  
2.  <span data-ttu-id="cc108-132">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="cc108-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="cc108-133">Se o **Solution Explorer** janela não ainda estiver aberta, pressione CTRL + W + S.</span><span class="sxs-lookup"><span data-stu-id="cc108-133">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>  
  
4.  <span data-ttu-id="cc108-134">Do **Solution Explorer** janela, o botão direito do mouse o **Service** do projeto e selecione **iniciar uma nova instância**.</span><span class="sxs-lookup"><span data-stu-id="cc108-134">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="cc108-135">Isso inicia o ASP.NET development server, que hospeda o serviço.</span><span class="sxs-lookup"><span data-stu-id="cc108-135">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="cc108-136">Do **Solution Explorer** janela, o botão direito do mouse o **cliente** do projeto e selecione **iniciar uma nova instância**.</span><span class="sxs-lookup"><span data-stu-id="cc108-136">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="cc108-137">A janela de console do cliente é exibida e fornece o URI do serviço em execução e o URI do HTML ajuda a página para o serviço em execução.</span><span class="sxs-lookup"><span data-stu-id="cc108-137">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="cc108-138">A qualquer momento, você pode exibir a página de ajuda HTML digitando o URI da página de Ajuda em um navegador.</span><span class="sxs-lookup"><span data-stu-id="cc108-138">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="cc108-139">Como o exemplo é executado, o cliente grava o status da atividade atual.</span><span class="sxs-lookup"><span data-stu-id="cc108-139">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="cc108-140">Pressione qualquer tecla para fechar o aplicativo de console de cliente.</span><span class="sxs-lookup"><span data-stu-id="cc108-140">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="cc108-141">Pressione SHIFT + F5 para parar a depuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="cc108-141">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="cc108-142">Na área de notificação do Windows, clique com botão direito no ícone do servidor de desenvolvimento ASP.NET e selecione **parar**.</span><span class="sxs-lookup"><span data-stu-id="cc108-142">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>