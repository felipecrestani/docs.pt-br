---
title: "Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64a43640d08acbab0bcf505cc8a5850784ff18ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="8de43-102">Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream</span><span class="sxs-lookup"><span data-stu-id="8de43-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="8de43-103">Obtém um ponteiro para um [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) objeto que contém dados de identidade de assembly para os assemblies referenciados pelo assembly do fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="8de43-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de43-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8de43-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8de43-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8de43-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="8de43-106">[in] Um ponteiro de interface para um `IStream` que contém o assembly a ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="8de43-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8de43-107">[in] Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="8de43-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="8de43-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor que suporta a versão atual do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8de43-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="8de43-109">[in] Um ponteiro para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objeto que contém dados de identidade de assembly para assemblies a serem excluídas do `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="8de43-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="8de43-110">[out] Um ponteiro para o endereço de um `ICLRReferenceAssemblyEnum` objeto que contém dados de identidade de assembly para assemblies referenciados pelo assembly no `pStream`, exceto os assemblies no `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="8de43-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8de43-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8de43-111">Return Value</span></span>  
  
|<span data-ttu-id="8de43-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8de43-112">HRESULT</span></span>|<span data-ttu-id="8de43-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8de43-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8de43-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8de43-114">S_OK</span></span>|<span data-ttu-id="8de43-115">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8de43-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="8de43-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8de43-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8de43-117">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8de43-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8de43-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8de43-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8de43-119">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="8de43-119">The call timed out.</span></span>|  
|<span data-ttu-id="8de43-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8de43-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8de43-121">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8de43-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8de43-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8de43-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8de43-123">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="8de43-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8de43-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8de43-124">E_FAIL</span></span>|<span data-ttu-id="8de43-125">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8de43-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8de43-126">Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="8de43-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8de43-127">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8de43-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8de43-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="8de43-128">Remarks</span></span>  
 <span data-ttu-id="8de43-129">O chamador pode optar por excluir um conjunto de referências de assembly conhecidos da lista retornada.</span><span class="sxs-lookup"><span data-stu-id="8de43-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="8de43-130">Este conjunto é definido pela `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="8de43-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8de43-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8de43-131">Requirements</span></span>  
 <span data-ttu-id="8de43-132">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8de43-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8de43-133">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8de43-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8de43-134">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="8de43-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8de43-135">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8de43-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de43-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8de43-136">See Also</span></span>  
 [<span data-ttu-id="8de43-137">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="8de43-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="8de43-138">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="8de43-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="8de43-139">Interface ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="8de43-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)