---
title: Método ICLRMetaHost::EnumerateLoadedRuntimes
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8342b18d0fb4163112aafd483bc452a3538aa5c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a>Método ICLRMetaHost::EnumerateLoadedRuntimes
Retorna uma enumeração que inclui uma opção válida [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ponteiro de interface para cada versão do common language runtime (CLR) que é carregado em um determinado processo. Esse método substitui o [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `hndProcess`  
 [in] O identificador do processo para inspecionar os tempos de execução carregados.  
  
 `ppEnumerator`  
 [out] Um <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` enumeração de [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces correspondente a cada CLR que é carregado pelo processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`ppEnumerator` é nulo.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é carregado lista todos os tempos de execução, mesmo se eles foram carregados com funções preteridas como [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
