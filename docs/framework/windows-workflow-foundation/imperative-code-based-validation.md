---
title: Validação classe base imperativa
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 87585050d7ab8c9adc5f0ac4ac5396862975cc25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imperative-code-based-validation"></a>Validação classe base imperativa
A validação classe base imperativa fornece uma maneira simples para uma atividade fornece validação sobre se, e está disponível para as atividades que derivam de <xref:System.Activities.CodeActivity>, de <xref:System.Activities.AsyncCodeActivity>, e de <xref:System.Activities.NativeActivity>. O código de validação que determina os erros ou avisos de validação é adicionado à atividade.  
  
## <a name="using-code-based-validation"></a>Usando a validação classe base  
 a validação classe base é suportada por atividades que derivam de <xref:System.Activities.CodeActivity>, de <xref:System.Activities.AsyncCodeActivity>, e de <xref:System.Activities.NativeActivity>. O código de validação pode ser colocado em uma substituição de <xref:System.Activities.CodeActivity.CacheMetadata%2A> , e os erros ou avisos de validação podem ser adicionados ao argumento de metadados. No exemplo a seguir, retirado de [validação básica](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) de exemplo, se o `Cost` é maior do que o `Price`, um erro de validação é adicionado aos metadados.  
  
> [!NOTE]
>  Observe que `Cost` e `Price` não são argumentos a atividade, mas é propriedades que são definidas em tempo de design. É por isso que seus valores podem ser validados em uma substituição de <xref:System.Activities.CodeActivity.CacheMetadata%2A> . O valor dos dados que correm através de um argumento não pode ser validado em tempo de design porque os dados não usam até o tempo de execução, mas os argumentos de atividade podem ser validados para garantir que estão associados usando os grupos de atributo e a sobrecarga de `RequiredArgument` . Esse código de exemplo considera o atributo de `RequiredArgument` para o argumento de `Description` , e se não está associado em um erro de validação é gerado. Os argumentos necessários são abordados em [argumentos necessários e grupos de sobrecarga](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error   
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 Por padrão, um erro de validação é adicionado aos metadados quando <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> é chamado. Para adicionar um aviso de validação, use a sobrecarga de <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> que leva <xref:System.Activities.Validation.ValidationError>, e especifica que <xref:System.Activities.Validation.ValidationError> representa um aviso definindo a propriedade de <xref:System.Activities.Validation.ValidationError.IsWarning%2A> .  
  
 A validação ocorre quando um trabalho são alterados no designer de trabalho e todos os erros ou avisos de validação são exibidos no designer de fluxo de trabalho. Validação também ocorre em tempo de execução quando um fluxo de trabalho é chamado e se qualquer erro de validação ocorre, <xref:System.Activities.InvalidWorkflowException> é acionada pela lógica padrão de validação. Para obter mais informações sobre invocando a validação e acessar quaisquer erros ou avisos de validação, consulte [invocando a validação de atividades](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
 Nenhuma exceções que são geradas de <xref:System.Activities.CodeActivity.CacheMetadata%2A> não são tratados como erros de validação. Essas exceções escaparão de chamada para <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> e devem ser tratadas pelo chamador.  
  
 a validação classe base é útil para validar a atividade que contém o código, mas não tem a visibilidade nas outras atividades no fluxo de trabalho. Validação de restrições declarativas fornece a capacidade de validar as relações entre uma atividade e outras atividades no fluxo de trabalho e é abordada no [restrições declarativas](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) tópico.
