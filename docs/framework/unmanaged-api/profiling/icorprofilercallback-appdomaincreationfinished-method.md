---
title: "Método ICorProfilerCallback::AppDomainCreationFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainCreationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d21198253e10434b37261d34cf12ef60c26f7e71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="02dad-102">Método ICorProfilerCallback::AppDomainCreationFinished</span><span class="sxs-lookup"><span data-stu-id="02dad-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="02dad-103">Notifica o criador de perfil que foi criado um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02dad-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02dad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02dad-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="02dad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02dad-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="02dad-106">[in] Identifica o domínio que foi criado.</span><span class="sxs-lookup"><span data-stu-id="02dad-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="02dad-107">[in] Um HRESULT que indica se a criação do domínio do aplicativo foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="02dad-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02dad-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="02dad-108">Remarks</span></span>  
 <span data-ttu-id="02dad-109">A ID do aplicativo não é válida para qualquer solicitação de informações até que o `AppDomainCreationFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="02dad-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="02dad-110">Algumas partes do carregamento de domínio do aplicativo podem continuar após o `AppDomainCreationFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="02dad-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="02dad-111">Uma falha de HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="02dad-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="02dad-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte da criação do domínio de aplicativo foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="02dad-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02dad-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02dad-113">Requirements</span></span>  
 <span data-ttu-id="02dad-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02dad-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02dad-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="02dad-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02dad-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02dad-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02dad-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02dad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02dad-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02dad-118">See Also</span></span>  
 [<span data-ttu-id="02dad-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="02dad-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)