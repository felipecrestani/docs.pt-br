---
title: "Método ICorProfilerInfo::GetAppDomainInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAppDomainInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c31d3c61a868bf741213f6e505d91524cc925207
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="8671b-102">Método ICorProfilerInfo::GetAppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="8671b-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="8671b-103">Aceita uma ID de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8671b-103">Accepts an application domain ID.</span></span> <span data-ttu-id="8671b-104">Retorna um nome de domínio de aplicativo e a ID do processo que o contém.</span><span class="sxs-lookup"><span data-stu-id="8671b-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8671b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8671b-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8671b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8671b-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="8671b-107">[in] A ID do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8671b-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8671b-108">[in] O comprimento, em caracteres, do `szName` buffer de retorno.</span><span class="sxs-lookup"><span data-stu-id="8671b-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8671b-109">[out] Um ponteiro para o total de caracteres do nome de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8671b-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="8671b-110">[out] Um buffer de caractere largo fornecida pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="8671b-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="8671b-111">Quando o método retorna, `szName` conterá o nome de domínio de aplicativo completo ou parcial.</span><span class="sxs-lookup"><span data-stu-id="8671b-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="8671b-112">[out] Um ponteiro para a ID do processo que contém o domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8671b-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8671b-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8671b-113">Remarks</span></span>  
 <span data-ttu-id="8671b-114">Depois que este método retorna, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8671b-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="8671b-115">Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor de `cchName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8671b-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="8671b-116">Se `pcchName` aponta para um valor que é maior do que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo tamanho maior e chame `GetAppDomainInfo` novamente.</span><span class="sxs-lookup"><span data-stu-id="8671b-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="8671b-117">Como alternativa, você pode primeiro chamar `GetAppDomainInfo` com um comprimento zero `szName` buffer para obter o tamanho do buffer correto.</span><span class="sxs-lookup"><span data-stu-id="8671b-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="8671b-118">Você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chame `GetAppDomainInfo` novamente.</span><span class="sxs-lookup"><span data-stu-id="8671b-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8671b-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8671b-119">Requirements</span></span>  
 <span data-ttu-id="8671b-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8671b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8671b-121">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8671b-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8671b-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8671b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8671b-123">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8671b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8671b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8671b-124">See Also</span></span>  
 [<span data-ttu-id="8671b-125">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="8671b-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="8671b-126">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8671b-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="8671b-127">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="8671b-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)