---
title: "Função CorBindToCurrentRuntime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: HeaderDef
f1_keywords: CorBindToCurrentRuntime
helpviewer_keywords: CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 630dab4fec8c37bd776b68870a53ab20e4050e06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="b3046-102">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="b3046-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="b3046-103">Carrega o common language runtime (CLR) em um processo usando informações de versão armazenadas em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="b3046-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="b3046-104">O formato do arquivo XML é modelado após o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="b3046-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="b3046-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3046-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="b3046-106">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b3046-106">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="b3046-107">Consulte [carregar o Common Language Runtime em um processo](http://msdn.microsoft.com/en-us/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span><span class="sxs-lookup"><span data-stu-id="b3046-107">See [Loading the Common Language Runtime into a Process](http://msdn.microsoft.com/en-us/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3046-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3046-108">Syntax</span></span>  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3046-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3046-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="b3046-110">[in] O nome de um arquivo de configuração de aplicativo que especifica a versão do CLR para carregar.</span><span class="sxs-lookup"><span data-stu-id="b3046-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="b3046-111">Se o nome do arquivo não está totalmente qualificado, supõe-se de estar no mesmo diretório que o executável fazendo a chamada.</span><span class="sxs-lookup"><span data-stu-id="b3046-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="b3046-112">A versão do tempo de execução a ser carregado é descrita pelo atributo na versão de [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b3046-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="b3046-113">Se nenhuma versão for especificada, ou se o `<requiredRuntime>` elemento não pode ser encontrado, a versão mais recente do CLR que está instalado na máquina é carregada.</span><span class="sxs-lookup"><span data-stu-id="b3046-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="b3046-114">[in] O `CLSID` da coclass que implemente tanto o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="b3046-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="b3046-115">Valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="b3046-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="b3046-116">[in] O `IID` da interface que você está solicitando.</span><span class="sxs-lookup"><span data-stu-id="b3046-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="b3046-117">Valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="b3046-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="b3046-118">[out] O ponteiro de interface retornado.</span><span class="sxs-lookup"><span data-stu-id="b3046-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3046-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3046-119">Requirements</span></span>  
 <span data-ttu-id="b3046-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3046-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3046-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3046-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3046-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3046-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3046-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3046-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3046-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3046-124">See Also</span></span>  
 [<span data-ttu-id="b3046-125">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="b3046-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="b3046-126">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="b3046-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="b3046-127">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="b3046-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="b3046-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="b3046-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="b3046-129">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="b3046-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="b3046-130">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="b3046-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)