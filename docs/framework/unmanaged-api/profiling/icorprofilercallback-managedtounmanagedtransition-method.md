---
title: "Método ICorProfilerCallback::ManagedToUnmanagedTransition"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ManagedToUnmanagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9da8dd44d5b87cd1c65b8b8837c9dd378039d332
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="813b5-102">Método ICorProfilerCallback::ManagedToUnmanagedTransition</span><span class="sxs-lookup"><span data-stu-id="813b5-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="813b5-103">Notifica o criador de perfil que ocorreu uma transição de código gerenciado para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="813b5-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="813b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="813b5-104">Syntax</span></span>  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="813b5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="813b5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="813b5-106">[in] A ID da função que está sendo chamada.</span><span class="sxs-lookup"><span data-stu-id="813b5-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="813b5-107">[in] Um valor de [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeração que indica se a transição ocorreu devido a uma chamada para código não gerenciado de código gerenciado, ou devido a um retorno de uma função gerenciada chamado por um não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="813b5-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="813b5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="813b5-108">Remarks</span></span>  
 <span data-ttu-id="813b5-109">Se o valor de `reason` é COR_PRF_TRANSITION_CALL, a função ID é que a função não gerenciado, que nunca foram compilado usando o compilador just-in-time.</span><span class="sxs-lookup"><span data-stu-id="813b5-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="813b5-110">Funções não gerenciadas têm informações básicas associadas a eles, como um nome e alguns metadados.</span><span class="sxs-lookup"><span data-stu-id="813b5-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="813b5-111">Se a função não gerenciada foi chamada com o uso de plataforma implícita invocar (PInvoke), o tempo de execução não é possível determinar o destino da chamada e o valor de `functionId` será nulo.</span><span class="sxs-lookup"><span data-stu-id="813b5-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="813b5-112">Para obter mais informações sobre PInvoke implícita, consulte [usando Interop C++ (PInvoke implícito)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="813b5-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="813b5-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="813b5-113">Requirements</span></span>  
 <span data-ttu-id="813b5-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="813b5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="813b5-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="813b5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="813b5-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="813b5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="813b5-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="813b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="813b5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="813b5-118">See Also</span></span>  
 [<span data-ttu-id="813b5-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="813b5-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="813b5-120">Método UnmanagedToManagedTransition</span><span class="sxs-lookup"><span data-stu-id="813b5-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)  
 [<span data-ttu-id="813b5-121">Usando PInvoke explícito no C++ (atributo DllImport)</span><span class="sxs-lookup"><span data-stu-id="813b5-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)