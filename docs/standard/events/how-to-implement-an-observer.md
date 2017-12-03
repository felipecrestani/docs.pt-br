---
title: Como implementar um observador
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a964bd031f6f8a7fc029b2b209b9693b72e688af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="dc611-102">Como implementar um observador</span><span class="sxs-lookup"><span data-stu-id="dc611-102">How to: Implement an Observer</span></span>
<span data-ttu-id="dc611-103">O padrão de design do observador requer uma divisão entre um observador, que registra para notificações, e um provedor, que monitora os dados e envia notificações para um ou mais observadores.</span><span class="sxs-lookup"><span data-stu-id="dc611-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="dc611-104">Este tópico discute como criar um observador.</span><span class="sxs-lookup"><span data-stu-id="dc611-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="dc611-105">Um tópico relacionado, [como: implementar um provedor](../../../docs/standard/events/how-to-implement-a-provider.md), descreve como criar um provedor.</span><span class="sxs-lookup"><span data-stu-id="dc611-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="dc611-106">Para criar um observador</span><span class="sxs-lookup"><span data-stu-id="dc611-106">To create an observer</span></span>  
  
1.  <span data-ttu-id="dc611-107">Definir o observador, o que é um tipo que implementa o <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span><span class="sxs-lookup"><span data-stu-id="dc611-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="dc611-108">Por exemplo, o código a seguir define um tipo chamado `TemperatureReporter` que é um construído <xref:System.IObserver%601?displayProperty=nameWithType> implementação com um argumento de tipo genérico de `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="dc611-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  <span data-ttu-id="dc611-109">Se o observador pode interromper o recebimento de notificações antes de chamar o provedor seu <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementação, definir uma variável privada que armazenará o <xref:System.IDisposable> implementação retornada pelo provedor de <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="dc611-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dc611-110">Você também deve definir um método de assinatura que chama o provedor <xref:System.IObservable%601.Subscribe%2A> método e repositórios retornados <xref:System.IDisposable> objeto.</span><span class="sxs-lookup"><span data-stu-id="dc611-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="dc611-111">Por exemplo, o código a seguir define uma variável particular chamada `unsubscriber` e define uma `Subscribe` método que chama o provedor <xref:System.IObservable%601.Subscribe%2A> método e atribui o objeto retornado para o `unsubscriber` variável.</span><span class="sxs-lookup"><span data-stu-id="dc611-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  <span data-ttu-id="dc611-112">Definir um método que permite que o observador interromper o recebimento de notificações antes de chamar o provedor seu <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementação, se esse recurso é necessário.</span><span class="sxs-lookup"><span data-stu-id="dc611-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="dc611-113">O exemplo a seguir define um `Unsubscribe` método.</span><span class="sxs-lookup"><span data-stu-id="dc611-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  <span data-ttu-id="dc611-114">Fornecer implementações dos três métodos definidos pelo <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, e <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc611-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dc611-115">Dependendo do provedor e as necessidades do aplicativo, o <xref:System.IObserver%601.OnError%2A> e <xref:System.IObserver%601.OnCompleted%2A> métodos podem ser implementações de stub.</span><span class="sxs-lookup"><span data-stu-id="dc611-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="dc611-116">Observe que o <xref:System.IObserver%601.OnError%2A> método não deve tratar transmitido <xref:System.Exception> objeto como uma exceção e o <xref:System.IObserver%601.OnCompleted%2A> método é livre para chamar o provedor <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementação.</span><span class="sxs-lookup"><span data-stu-id="dc611-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="dc611-117">A exemplo a seguir mostra o <xref:System.IObserver%601> implementação de `TemperatureReporter` classe.</span><span class="sxs-lookup"><span data-stu-id="dc611-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="dc611-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc611-118">Example</span></span>  
 <span data-ttu-id="dc611-119">O exemplo a seguir contém o código-fonte completo para o `TemperatureReporter` classe, que fornece o <xref:System.IObserver%601> implementação para uma aplicativo de monitoramento de temperatura.</span><span class="sxs-lookup"><span data-stu-id="dc611-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="dc611-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc611-120">See Also</span></span>  
 <xref:System.IObserver%601>  
 [<span data-ttu-id="dc611-121">Padrão de design do observador</span><span class="sxs-lookup"><span data-stu-id="dc611-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
 [<span data-ttu-id="dc611-122">Como implementar um provedor</span><span class="sxs-lookup"><span data-stu-id="dc611-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [<span data-ttu-id="dc611-123">Práticas recomendadas para o padrão de design do observador</span><span class="sxs-lookup"><span data-stu-id="dc611-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)