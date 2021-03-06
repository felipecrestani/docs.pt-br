---
title: Método ICorProfilerInfo::GetAssemblyInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3579020ce268cd59a091e685fae2e97b3191c55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a>Método ICorProfilerInfo::GetAssemblyInfo
Aceita uma ID de assembly e retorna o nome do assembly e a ID do seu módulo de manifesto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `assemblyId`  
 [in] O identificador do assembly.  
  
 `cchName`  
 [in] O comprimento, em caracteres, de `szName`.  
  
 `pcchName`  
 [out] Um ponteiro para o total de caracteres do nome do assembly.  
  
 `szName`  
 [out] Um buffer de caractere largo fornecida pelo chamador. Quando a função retorna, ele conterá o nome do assembly.  
  
 `pAppDomainId`  
 [out] Um ponteiro para a ID do domínio do aplicativo que contém o assembly.  
  
 `pModuleId`  
 [out] Um ponteiro para a ID do módulo de manifesto do assembly.  
  
## <a name="remarks"></a>Comentários  
 Depois que este método retorna, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do assembly. Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor de `cchName` parâmetro. Se `pcchName` aponta para um valor que é maior do que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo tamanho maior e chame `GetAssemblyInfo` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetAssemblyInfo` com um comprimento zero `szName` buffer para obter o tamanho do buffer correto. Em seguida, você pode ajustar o tamanho do buffer com base no valor retornado em `pcchName` e chame `GetAssemblyInfo` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
