---
title: "Cabeçalhos de endereço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19a7291ce13221e85b49c6ef97c6b375b8b71014
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="address-headers"></a>Cabeçalhos de endereço
O exemplo de cabeçalhos de endereço demonstra como os clientes podem passar parâmetros de referência para um serviço usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 A especificação WS-Addressing define a noção de uma referência de ponto de extremidade como uma maneira de abordar um ponto de extremidade de serviço da Web específico. Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], referências de ponto de extremidade são modeladas usando o `EndpointAddress` classe - `EndpointAddress` é o tipo de campo de endereço do `ServiceEndpoint` classe.  
  
 Parte do modelo de referência de ponto de extremidade é que cada referência pode executar alguns parâmetros de referência que adicionar informações de identificação extra. Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], esses parâmetros de referência são modelados como instâncias de `AddressHeader` classe.  
  
 Neste exemplo, o cliente adiciona um parâmetro de referência para o `EndpointAddress` do ponto de extremidade do cliente. O serviço procura esse parâmetro de referência e usa seu valor na lógica de sua operação de serviço "Olá".  
  
## <a name="client"></a>Cliente  
 Para que o cliente envie um parâmetro de referência, ele deve adicionar um `AddressHeader` para o `EndpointAddress` do `ServiceEndpoint`. Porque o `EndpointAddress` classe é imutável, a modificação de um endereço de ponto de extremidade deve ser feita usando o `EndpointAddressBuilder` classe. O código a seguir inicializa o cliente para enviar um parâmetro de referência como parte de sua mensagem.  
  
```  
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 O código cria um `EndpointAddressBuilder` usando original `EndpointAddress` como um valor inicial. Em seguida, adiciona um cabeçalho de endereço recém-criado. a chamada para `CreateAddressHeadercreates` um cabeçalho com um nome específico, um namespace e um valor. Aqui, o valor é "John". Depois que o cabeçalho é adicionado ao construtor, o `ToEndpointAddress()` método converte o construtor (mutável) volta para um endereço de ponto de extremidade (imutáveis), que é atribuído para o campo de endereço do ponto de extremidade de cliente.  
  
 Agora quando o cliente chama `Console.WriteLine(client.Hello());`, o serviço é capaz de obter o valor desse parâmetro de endereço, como mostra a saída resultante do cliente.  
  
 `Hello, John`  
  
## <a name="server"></a>Servidor  
 A implementação da operação de serviço `Hello()` usa atual `OperationContext` para inspecionar os valores dos cabeçalhos na mensagem de entrada.  
  
```  
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h =   
        OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr =   
OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 O código itera em todos os cabeçalhos de mensagem de entrada, procurando os cabeçalhos que são parâmetros de referência com o nome específico e. Quando o parâmetro for encontrado, ele lê o valor do parâmetro e o armazena na variável "id".  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a>Consulte também