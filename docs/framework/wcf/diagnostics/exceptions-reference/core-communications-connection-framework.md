---
title: "Comunicações principais: estrutura de conexão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c485c05c1c54a19a102a8378dc79c908a29aa658
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="core-communications-connection-framework"></a><span data-ttu-id="af5fc-102">Comunicações principais: estrutura de conexão</span><span class="sxs-lookup"><span data-stu-id="af5fc-102">Core Communications: Connection Framework</span></span>
<span data-ttu-id="af5fc-103">Este tópico lista todas as exceções geradas pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Framework de Conexão.</span><span class="sxs-lookup"><span data-stu-id="af5fc-103">This topic lists all exceptions generated by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Connection Framework.</span></span>  
  
## <a name="exception-list"></a><span data-ttu-id="af5fc-104">Lista de exceções</span><span class="sxs-lookup"><span data-stu-id="af5fc-104">Exception List</span></span>  
  
|<span data-ttu-id="af5fc-105">Código do recurso</span><span class="sxs-lookup"><span data-stu-id="af5fc-105">Resource Code</span></span>|<span data-ttu-id="af5fc-106">Cadeia de caracteres de recurso</span><span class="sxs-lookup"><span data-stu-id="af5fc-106">Resource String</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="af5fc-107">CloseTimedOut</span><span class="sxs-lookup"><span data-stu-id="af5fc-107">CloseTimedOut</span></span>|<span data-ttu-id="af5fc-108">O método Close atingiu o tempo limite após o período especificado.</span><span class="sxs-lookup"><span data-stu-id="af5fc-108">The Close method timed out after the specified time.</span></span> <span data-ttu-id="af5fc-109">Aumente o valor de tempo limite que é passado para a chamada para fechar ou aumente o valor de CloseTimeout na associação.</span><span class="sxs-lookup"><span data-stu-id="af5fc-109">Increase the timeout value that is passed to the call to Close or increase the CloseTimeout value on the binding.</span></span> <span data-ttu-id="af5fc-110">O tempo determinado para essa operação pode ter sido uma parte de um tempo limite maior.</span><span class="sxs-lookup"><span data-stu-id="af5fc-110">The time allotted to this operation may have been a portion of a longer timeout.</span></span>|  
|<span data-ttu-id="af5fc-111">ContentTypeMismatch</span><span class="sxs-lookup"><span data-stu-id="af5fc-111">ContentTypeMismatch</span></span>|<span data-ttu-id="af5fc-112">O tipo de conteúdo especificado foi enviado a um serviço que estava esperando especificado.</span><span class="sxs-lookup"><span data-stu-id="af5fc-112">The specified content type was sent to a service that was expecting the specified.</span></span> <span data-ttu-id="af5fc-113">As associações de cliente e serviço talvez não sejam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="af5fc-113">The client and service bindings may be mismatched.</span></span>|  
|<span data-ttu-id="af5fc-114">DuplexChannelAbortedDuringOpen</span><span class="sxs-lookup"><span data-stu-id="af5fc-114">DuplexChannelAbortedDuringOpen</span></span>|<span data-ttu-id="af5fc-115">O canal duplex para especificado foi finalizado durante o processo de abertura.</span><span class="sxs-lookup"><span data-stu-id="af5fc-115">The duplex channel to the specified terminated during the Open process.</span></span>|  
|<span data-ttu-id="af5fc-116">FramingValueNotAvailable</span><span class="sxs-lookup"><span data-stu-id="af5fc-116">FramingValueNotAvailable</span></span>|<span data-ttu-id="af5fc-117">O valor não pode ser acessado porque ele não é totalmente decodificado.</span><span class="sxs-lookup"><span data-stu-id="af5fc-117">The value cannot be accessed because it is not fully decoded.</span></span>|  
|<span data-ttu-id="af5fc-118">OperationAbortedDuringConnectionEstablishment</span><span class="sxs-lookup"><span data-stu-id="af5fc-118">OperationAbortedDuringConnectionEstablishment</span></span>|<span data-ttu-id="af5fc-119">A operação foi encerrada ao estabelecer uma conexão especificado.</span><span class="sxs-lookup"><span data-stu-id="af5fc-119">The operation was terminated while establishing a connection to the specified.</span></span>|  
|<span data-ttu-id="af5fc-120">ReceiveTimedOut2</span><span class="sxs-lookup"><span data-stu-id="af5fc-120">ReceiveTimedOut2</span></span>|<span data-ttu-id="af5fc-121">A operação de recebimento expirou após o período especificado.</span><span class="sxs-lookup"><span data-stu-id="af5fc-121">The receive operation has timed out after the specified time.</span></span> <span data-ttu-id="af5fc-122">O tempo determinado para essa operação pode ter sido uma parte de um tempo limite maior.</span><span class="sxs-lookup"><span data-stu-id="af5fc-122">The time allotted to this operation may have been a portion of a longer timeout.</span></span>|  
|<span data-ttu-id="af5fc-123">SendCannotBeCalledAfterCloseOutputSession</span><span class="sxs-lookup"><span data-stu-id="af5fc-123">SendCannotBeCalledAfterCloseOutputSession</span></span>|<span data-ttu-id="af5fc-124">Você não pode enviar mensagens em um canal após CloseOutputSession ter sido chamado.</span><span class="sxs-lookup"><span data-stu-id="af5fc-124">You cannot send messages on a channel after CloseOutputSession has been called.</span></span>|