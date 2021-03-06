---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 65bcc1ccd357fb7f331665aefbd975b11a2378cd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowidlegt"></a>&lt;workflowIdle&gt;
Um comportamento de serviço que controla quando instâncias de fluxo de trabalho ocioso são descarregadas e persistidas.  
  
\<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<workflowIdle >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|timeToPersist|Um valor Timespan que especifica a duração entre a hora em que o fluxo de trabalho se torna ocioso e é mantido. O valor padrão é TimeSpan. MaxValue.<br /><br /> A duração começa a decorrer quando a instância de fluxo de trabalho fica ociosa. Esse atributo é útil se você quiser manter uma instância de fluxo de trabalho mais agressiva enquanto mantém a instância na memória por tempo possível. Esse atributo só é válido se o valor for menor do que o **timeToUnload** atributo. Se for maior, ela será ignorada. Se esse atributo decorrer antes do valor especificado pelo **timeToUnload** atributo, persistência deve concluir antes do fluxo de trabalho é descarregado. Isso significa que a operação pode ser atrasada até que o fluxo de trabalho é mantido. A camada de persistência é responsável por gerenciar quaisquer tentativas de erros transitórios e apenas lança exceções em erros não recuperáveis. Portanto, todas as exceções geradas durante a persistência são tratadas como fatal e a instância de fluxo de trabalho será anulada.|  
|timeToUnload|Um valor de Timespan que especifica a duração entre o momento em que o fluxo de trabalho fica ocioso e é descarregado. O valor padrão é 1 minuto.<br /><br /> Descarregar um fluxo de trabalho significa que ele também é mantido. Se esse atributo for definido como zero, a instância de fluxo de trabalho é mantida e carregada imediatamente após o fluxo de trabalho se torna ocioso. Definir esse atributo como TimeSpan. MaxValue efetivamente desabilita a operação. Instâncias de fluxo de trabalho ocioso nunca são descarregadas.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento > de \<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Especifica um elemento de comportamento.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
