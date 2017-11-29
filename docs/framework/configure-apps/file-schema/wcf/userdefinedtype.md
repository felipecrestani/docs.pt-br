---
title: '&lt;userDefinedType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0baac8dc6a9899261a490a257dbae0e7eb4d2ced
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserdefinedtypegt"></a>&lt;userDefinedType&gt;
Representa um tipo definido pelo usuário (UDT) que deve ser incluído no contrato de serviço.  
  
 \<sistema. ServiceModel >  
\<comContracts >  
\<comContract >  
\<userDefinedTypes >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<comContracts>  
  <comContract>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Um atributo opcional que contém uma cadeia de caracteres que fornece o nome de tipo legível. Isso não é usado pelo tempo de execução, mas ajuda a um leitor para distinguir os tipos.|  
|`TypeDefID`|Uma cadeia de caracteres GUID que identifica o tipo UDT específico dentro da biblioteca de tipos registrada.|  
|`TypeLibID`|Uma cadeia de caracteres GUID que identifica a biblioteca de tipos registrada que define o tipo.|  
|`TypeLibVersion`|Uma cadeia de caracteres que identifica a versão da biblioteca de tipo que define o tipo.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`userDefinedTypes`|Uma coleção de `userDefinedType` elementos.|  
  
## <a name="remarks"></a>Comentários  
 O tempo de execução de integração COM+ cria serviços inspecionando a biblioteca de tipos. Quando um componente COM+ contém métodos que passam um tipo VARIANT, o sistema não pode determinar os tipos reais a serem passados antes do tempo de execução. Portanto, quando você tentar passar um usuário definido pelo tipo (UDT) dentro de um tipo VARIANT, ele falha porque não é um tipo conhecido para serialização.  
  
 Para contornar esse problema, você pode adicionar os UDTs para o arquivo de configuração para que eles podem ser incluídos como tipos conhecidos no contrato de serviço apropriado. Para fazer isso, você precisa identificar exclusivamente o UDT e o contrato (s), ou seja, as COM interfaces originais que utiliza.  
  
 O exemplo a seguir demonstra como adicionar dois UDTs específicos para o <`userDefinedTypes`> seção do arquivo de configuração para essa finalidade.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <userDefinedTypes>  
         <userDefinedType name="CustomerType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">  
         </userDefinedType>  
         <userDefinedType name="AddressType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">  
         </userDefinedType>  
      </userDefinedTypes>  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 Quando o serviço é inicializado, o tempo de execução de integração procura os tipos especificados e os adiciona à coleção de tipos conhecidos para contratos especificados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>  
 <xref:System.ServiceModel.Configuration.ComUdtElementCollection>  
 <xref:System.ServiceModel.Configuration.ComUdtElement>  
 [\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [Integrando aplicativos COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Como: definir configurações de serviço COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)