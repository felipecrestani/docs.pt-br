---
title: "Ponto de extremidade: mensagens confiáveis do sistema de mensagens descartadas por segundo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: db61701fabbea99bdf8a8dfc599f6cf9b7e21bb1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="c2b2a-102">Ponto de extremidade: mensagens confiáveis do sistema de mensagens descartadas por segundo</span><span class="sxs-lookup"><span data-stu-id="c2b2a-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="c2b2a-103">Nome do contador: Sessões de mensagens confiáveis descartadas por segundo.</span><span class="sxs-lookup"><span data-stu-id="c2b2a-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c2b2a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2b2a-104">Description</span></span>  
 <span data-ttu-id="c2b2a-105">Número total de mensagens confiáveis que foram ignoradas neste ponto de extremidade em um segundo.</span><span class="sxs-lookup"><span data-stu-id="c2b2a-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="c2b2a-106">Esse contador é do tipo de contador de desempenho [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), cujo valor é calculado usando a fórmula a seguir.</span><span class="sxs-lookup"><span data-stu-id="c2b2a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c2b2a-107">(1 - N 0 N) / ((D - 1D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="c2b2a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>