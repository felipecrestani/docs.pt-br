---
title: "Glossário do Windows Workflow Foundation para o .NET Framework 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Workflow Foundation [WF], glossary
- WF [WF], glossary
ms.assetid: ab682b2f-3779-45ca-b831-b7c03d7dbb3a
caps.latest.revision: "259"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0c1e6fa7eee64283dce20b24a1a957f1d2d8f8f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="windows-workflow-foundation-glossary-for-net-framework-45"></a><span data-ttu-id="80afb-102">Glossário do Windows Workflow Foundation para o .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="80afb-102">Windows Workflow Foundation Glossary for .NET Framework 4.5</span></span>
<span data-ttu-id="80afb-103">Os seguintes termos são usados na documentação do Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="80afb-103">The following terms are used in the Windows Workflow Foundation documentation.</span></span>  
  
## <a name="terms"></a><span data-ttu-id="80afb-104">Termos</span><span class="sxs-lookup"><span data-stu-id="80afb-104">Terms</span></span>  
  
|<span data-ttu-id="80afb-105">Termo</span><span class="sxs-lookup"><span data-stu-id="80afb-105">Term</span></span>|<span data-ttu-id="80afb-106">Definição</span><span class="sxs-lookup"><span data-stu-id="80afb-106">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="80afb-107">atividade</span><span class="sxs-lookup"><span data-stu-id="80afb-107">activity</span></span>|<span data-ttu-id="80afb-108">Uma unidade de comportamento de programa do Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="80afb-108">A unit of program behavior in Windows Workflow Foundation.</span></span> <span data-ttu-id="80afb-109">Atividades único podem ser compostas juntos em atividades mais complexas.</span><span class="sxs-lookup"><span data-stu-id="80afb-109">Single activities can be composed together into more complex activities.</span></span>|  
|<span data-ttu-id="80afb-110">ação de atividade</span><span class="sxs-lookup"><span data-stu-id="80afb-110">activity action</span></span>|<span data-ttu-id="80afb-111">Uma estrutura de dados usada para expor os retornos de chamada para execução de fluxo de trabalho e atividades.</span><span class="sxs-lookup"><span data-stu-id="80afb-111">A data structure used to expose callbacks for workflow and activity execution.</span></span>|  
|<span data-ttu-id="80afb-112">Argumento</span><span class="sxs-lookup"><span data-stu-id="80afb-112">argument</span></span>|<span data-ttu-id="80afb-113">Define o fluxo de dados dentro e fora de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="80afb-113">Defines the data flow into and out of an activity.</span></span> <span data-ttu-id="80afb-114">Cada argumento tem uma direção especificada:, ou em entrada/saída. Eles representam a entrada, saída e parâmetros de entrada/saída da atividade.</span><span class="sxs-lookup"><span data-stu-id="80afb-114">Each argument has a specified direction: in, out, or in/out. These represent the input, output, and input/output parameters of the activity.</span></span>|  
|<span data-ttu-id="80afb-115">Indicador</span><span class="sxs-lookup"><span data-stu-id="80afb-115">bookmark</span></span>|<span data-ttu-id="80afb-116">O ponto em que uma atividade pode pausar e aguarde a ser retomado.</span><span class="sxs-lookup"><span data-stu-id="80afb-116">The point at which an activity can pause and wait to be resumed.</span></span>|  
|<span data-ttu-id="80afb-117">compensação</span><span class="sxs-lookup"><span data-stu-id="80afb-117">compensation</span></span>|<span data-ttu-id="80afb-118">Um grupo de ações criadas para desfazer ou reduzir o efeito de anteriormente concluir o trabalho.</span><span class="sxs-lookup"><span data-stu-id="80afb-118">A group of actions designed to undo or mitigate the effect of previously completed work.</span></span>|  
|<span data-ttu-id="80afb-119">Correlação</span><span class="sxs-lookup"><span data-stu-id="80afb-119">correlation</span></span>|<span data-ttu-id="80afb-120">O mecanismo de roteamento de mensagens para uma instância de fluxo de trabalho ou serviço.</span><span class="sxs-lookup"><span data-stu-id="80afb-120">The mechanism for routing messages to a workflow or service instance.</span></span>|  
|<span data-ttu-id="80afb-121">expressão</span><span class="sxs-lookup"><span data-stu-id="80afb-121">expression</span></span>|<span data-ttu-id="80afb-122">Uma construção que entra em um ou mais argumentos, executa uma operação sobre os argumentos e retorna um único valor.</span><span class="sxs-lookup"><span data-stu-id="80afb-122">A construct that takes in one or more arguments, performs an operation on the arguments and returns a single value.</span></span> <span data-ttu-id="80afb-123">Expressões podem ser usadas em qualquer lugar que uma atividade pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="80afb-123">Expressions can be used anywhere an activity can be used.</span></span>|  
|<span data-ttu-id="80afb-124">fluxograma</span><span class="sxs-lookup"><span data-stu-id="80afb-124">flowchart</span></span>|<span data-ttu-id="80afb-125">Um paradigma de modelagem bem conhecido que representa os componentes de programa como símbolos vinculados junto com as setas direcionais.</span><span class="sxs-lookup"><span data-stu-id="80afb-125">A well-known modeling paradigm that represents program components as symbols linked together with directional arrows.</span></span>  <span data-ttu-id="80afb-126">No .NET Framework 4, os fluxos de trabalho podem ser modelados como fluxogramas usando a atividade do fluxograma.</span><span class="sxs-lookup"><span data-stu-id="80afb-126">In the .NET Framework 4, workflows can be modeled as flowcharts using the Flowchart activity.</span></span>|  
|<span data-ttu-id="80afb-127">processo de execução longa</span><span class="sxs-lookup"><span data-stu-id="80afb-127">long-running process</span></span>|<span data-ttu-id="80afb-128">Uma unidade de execução do programa que não retorna imediatamente e pode abranger reinicializações do sistema.</span><span class="sxs-lookup"><span data-stu-id="80afb-128">A unit of program execution that does not return immediately and may span system restarts.</span></span>|  
|<span data-ttu-id="80afb-129">persistência</span><span class="sxs-lookup"><span data-stu-id="80afb-129">persistence</span></span>|<span data-ttu-id="80afb-130">Salvar o estado de um fluxo de trabalho ou um serviço em uma mídia durável, para que possa ser descarregado da memória ou recuperado após uma falha do sistema.</span><span class="sxs-lookup"><span data-stu-id="80afb-130">Saving the state of a workflow or service to a durable medium, so that it can be unloaded from memory or recovered after a system failure.</span></span>|  
|<span data-ttu-id="80afb-131">máquina de estado</span><span class="sxs-lookup"><span data-stu-id="80afb-131">state machine</span></span>|<span data-ttu-id="80afb-132">Um paradigma de modelagem bem conhecido que representa os componentes de programa, como cada um dos Estados vinculado junto com as transições de estado controlada por evento.</span><span class="sxs-lookup"><span data-stu-id="80afb-132">A well-known modeling paradigm that represents program components as individual states linked together with event-driven state transitions.</span></span>  <span data-ttu-id="80afb-133">Fluxos de trabalho podem ser modelados como máquinas de estado usando a atividade de StateMachine.</span><span class="sxs-lookup"><span data-stu-id="80afb-133">Workflows can be modeled as state machines using the StateMachine activity.</span></span>|  
|<span data-ttu-id="80afb-134">substância</span><span class="sxs-lookup"><span data-stu-id="80afb-134">substance</span></span>|<span data-ttu-id="80afb-135">Representa um grupo de marcadores relacionados em um identificador comum e permite que o tempo de execução tomar decisões sobre se uma continuação de determinado indicador é válida ou se tornem válida.</span><span class="sxs-lookup"><span data-stu-id="80afb-135">Represents a group of related bookmarks under a common identifier and allows the runtime to make decisions about whether a particular bookmark resumption is valid or may become valid.</span></span>|  
|<span data-ttu-id="80afb-136">conversor de tipo</span><span class="sxs-lookup"><span data-stu-id="80afb-136">type converter</span></span>|<span data-ttu-id="80afb-137">Um tipo de CLR pode ser associado com um ou mais tipos derivados System.ComponentModel.TypeConverter que permitem converter instâncias do tipo da CLR e instâncias de outros tipos.</span><span class="sxs-lookup"><span data-stu-id="80afb-137">A CLR type can be associated with one or more System.ComponentModel.TypeConverter derived types that enable converting instances of the CLR type to and from instances of other types.</span></span> <span data-ttu-id="80afb-138">Um converterr de tipo é associado com um tipo de CLR usando o atributo System.ComponentModel.TypeConverterAttribute.</span><span class="sxs-lookup"><span data-stu-id="80afb-138">A type converterr is associated with a CLR type using the System.ComponentModel.TypeConverterAttribute attribute.</span></span>  <span data-ttu-id="80afb-139">Um TypeConverterAttribute pode ser especificado diretamente no tipo de CLR ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="80afb-139">A TypeConverterAttribute can be specified directly on the CLR type or on a property.</span></span> <span data-ttu-id="80afb-140">Um conversor de tipo especificado em uma propriedade sempre tem precedência sobre um conversor de tipo especificado no tipo de CLR de propriedade.</span><span class="sxs-lookup"><span data-stu-id="80afb-140">A type converter specified on a property always takes precedence over a type converter specified on the CLR type of the property.</span></span>|  
|<span data-ttu-id="80afb-141">variável</span><span class="sxs-lookup"><span data-stu-id="80afb-141">variable</span></span>|<span data-ttu-id="80afb-142">Representa o armazenamento de alguns dados que devem ser salvos e acessados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="80afb-142">Represents the storage of some data that must be saved and accessed later.</span></span>|  
|<span data-ttu-id="80afb-143">fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="80afb-143">workflow</span></span>|<span data-ttu-id="80afb-144">Uma única atividade ou árvore de atividades invocado por um processo de host.</span><span class="sxs-lookup"><span data-stu-id="80afb-144">A single activity or tree of activities invoked by a host process.</span></span>|  
|<span data-ttu-id="80afb-145">XAML</span><span class="sxs-lookup"><span data-stu-id="80afb-145">XAML</span></span>|<span data-ttu-id="80afb-146">extensible application marcação idioma</span><span class="sxs-lookup"><span data-stu-id="80afb-146">eXtensible Application Markup Language</span></span>|