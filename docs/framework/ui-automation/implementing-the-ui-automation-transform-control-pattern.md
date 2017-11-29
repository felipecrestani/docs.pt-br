---
title: "Implementando o Padrão de Controle de Transformação de Automação de IU"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: df871c7f7214a6135db2493972dd76f41ce31aaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a><span data-ttu-id="c752d-102">Implementando o Padrão de Controle de Transformação de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="c752d-102">Implementing the UI Automation Transform Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="c752d-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="c752d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c752d-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="c752d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="c752d-105">Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.ITransformProvider>, incluindo informações sobre propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="c752d-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="c752d-106">Links para referências adicionais são listadas no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="c752d-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="c752d-107">O <xref:System.Windows.Automation.TransformPattern> padrão de controle é usado para oferecer suporte aos controles que podem ser movidos, redimensionados ou girados em um espaço bidimensional.</span><span class="sxs-lookup"><span data-stu-id="c752d-107">The <xref:System.Windows.Automation.TransformPattern> control pattern is used to support controls that can be moved, resized, or rotated within a two-dimensional space.</span></span> <span data-ttu-id="c752d-108">Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c752d-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="c752d-109">Convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="c752d-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="c752d-110">Ao implementar o padrão de controle de transformação, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="c752d-110">When implementing the Transform control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="c752d-111">Suporte para esse padrão de controle não está limitado a objetos na área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c752d-111">Support for this control pattern is not limited to objects on the desktop.</span></span> <span data-ttu-id="c752d-112">Esse padrão de controle também deve ser suportado pelos filhos de um objeto contêiner se os filhos podem ser movidos, redimensionados ou girados livremente dentro dos limites do contêiner.</span><span class="sxs-lookup"><span data-stu-id="c752d-112">This control pattern must also be supported by the children of a container object if the children can be moved, resized, or rotated freely within the boundaries of the container.</span></span>  
  
-   <span data-ttu-id="c752d-113">Um objeto não pode ser movido, redimensionado ou girado, de modo que seu local de tela resultante deve ser completamente fora das coordenadas de seu contêiner e portanto inacessíveis ao teclado ou mouse (por exemplo, quando uma janela de nível superior é movida de fora da tela ou um objeto filho é movido para fora dos limites do visor do contêiner).</span><span class="sxs-lookup"><span data-stu-id="c752d-113">An object cannot be moved, resized, or rotated such that its resulting screen location would be completely outside the coordinates of its container and therefore inaccessible to the keyboard or mouse (for example, when a top-level window is moved off-screen or a child object is moved outside the boundaries of the container's viewport).</span></span> <span data-ttu-id="c752d-114">Nesses casos, o objeto será colocado mais próximo das coordenadas de tela solicitada possível com as coordenadas superior ou esquerdas substituídas para ser dentro dos limites do contêiner.</span><span class="sxs-lookup"><span data-stu-id="c752d-114">In these cases, the object is placed as close to the requested screen coordinates as possible with the top or left coordinates overridden to be within the container boundaries.</span></span>  
  
-   <span data-ttu-id="c752d-115">Para sistemas de vários monitores, se um objeto for movido, redimensionada ou girada completamente fora das coordenadas de tela de desktop combinado, o objeto é colocado no monitor principal mais próximo das coordenadas solicitadas quanto possível.</span><span class="sxs-lookup"><span data-stu-id="c752d-115">For multi-monitor systems, if an object is moved, resized, or rotated completely outside the combined desktop screen coordinates, the object is placed on the primary monitor as close to the requested coordinates as possible.</span></span>  
  
-   <span data-ttu-id="c752d-116">Todos os parâmetros e valores de propriedade são absolutos e independentes de localidade.</span><span class="sxs-lookup"><span data-stu-id="c752d-116">All parameters and property values are absolute and independent of locale.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a><span data-ttu-id="c752d-117">Membros necessários para ITransformProvider</span><span class="sxs-lookup"><span data-stu-id="c752d-117">Required Members for ITransformProvider</span></span>  
 <span data-ttu-id="c752d-118">As propriedades e métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.ITransformProvider>.</span><span class="sxs-lookup"><span data-stu-id="c752d-118">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>.</span></span>  
  
|<span data-ttu-id="c752d-119">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="c752d-119">Required members</span></span>|<span data-ttu-id="c752d-120">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="c752d-120">Member type</span></span>|<span data-ttu-id="c752d-121">Observações</span><span class="sxs-lookup"><span data-stu-id="c752d-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|<span data-ttu-id="c752d-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c752d-122">Property</span></span>|<span data-ttu-id="c752d-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c752d-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|<span data-ttu-id="c752d-124">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c752d-124">Property</span></span>|<span data-ttu-id="c752d-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c752d-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|<span data-ttu-id="c752d-126">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c752d-126">Property</span></span>|<span data-ttu-id="c752d-127">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c752d-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|<span data-ttu-id="c752d-128">Método</span><span class="sxs-lookup"><span data-stu-id="c752d-128">Method</span></span>|<span data-ttu-id="c752d-129">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c752d-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|<span data-ttu-id="c752d-130">Método</span><span class="sxs-lookup"><span data-stu-id="c752d-130">Method</span></span>|<span data-ttu-id="c752d-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c752d-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|<span data-ttu-id="c752d-132">Método</span><span class="sxs-lookup"><span data-stu-id="c752d-132">Method</span></span>|<span data-ttu-id="c752d-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c752d-133">None</span></span>|  
  
 <span data-ttu-id="c752d-134">Esse padrão de controle não possui eventos associados.</span><span class="sxs-lookup"><span data-stu-id="c752d-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="c752d-135">Exceções</span><span class="sxs-lookup"><span data-stu-id="c752d-135">Exceptions</span></span>  
 <span data-ttu-id="c752d-136">Provedores devem lançar as exceções a seguir.</span><span class="sxs-lookup"><span data-stu-id="c752d-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="c752d-137">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="c752d-137">Exception Type</span></span>|<span data-ttu-id="c752d-138">Condição</span><span class="sxs-lookup"><span data-stu-id="c752d-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> <span data-ttu-id="c752d-139">-Se a <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> é false.</span><span class="sxs-lookup"><span data-stu-id="c752d-139">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> <span data-ttu-id="c752d-140">-Se a <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> é false.</span><span class="sxs-lookup"><span data-stu-id="c752d-140">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> <span data-ttu-id="c752d-141">-Se a <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> é false.</span><span class="sxs-lookup"><span data-stu-id="c752d-141">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> is false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c752d-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c752d-142">See Also</span></span>  
 [<span data-ttu-id="c752d-143">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c752d-143">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="c752d-144">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c752d-144">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="c752d-145">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="c752d-145">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="c752d-146">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c752d-146">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="c752d-147">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c752d-147">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)