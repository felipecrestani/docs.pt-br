---
title: Método ICorProfilerInfo::SetILInstrumentedCodeMap
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ecb80de1ae46b072df4bab8357e78e7a22ae298
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>Método ICorProfilerInfo::SetILInstrumentedCodeMap
Define um mapa de código para a função especificada usando entradas do mapa especificadas Microsoft intermediate language (MSIL).  
  
> [!NOTE]
>  No .NET Framework versão 2.0, chamando `SetILInstrumentedCodeMap` em um `FunctionID` que representa um genérico de função em um domínio de aplicativo específico afetará todas as instâncias dessa função no domínio do aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função para o qual definir o mapa de código.  
  
 `fStartJit`  
 [in] Um valor booliano que indica se a chamada para o `SetILInstrumentedCodeMap` método é o primeiro para um determinado `FunctionID`. Definir `fStartJit` para `true` na primeira chamada para `SetILInstrumentedCodeMap` para um determinado `FunctionID`e `false` depois disso.  
  
 `cILMapEntries`  
 [in] O número de elementos a `cILMapEntries` matriz.  
  
 `rgILMapEntries`  
 [in] Uma matriz de estruturas COR_IL_MAP, cada uma delas Especifica um deslocamento MSIL.  
  
## <a name="remarks"></a>Comentários  
 Um criador de perfil geralmente insere instruções no código-fonte de um método para instrumentar o método (por exemplo, para notificar quando uma linha de origem especificado é atingida). `SetILInstrumentedCodeMap` permite que um criador de perfil mapear as instruções da MSIL originais para seus novos locais. Um criador de perfil pode usar o [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) método para obter o deslocamento MSIL original para um determinado deslocamento nativo.  
  
 O depurador pressupõem que cada deslocamento antigo se refere a um MSIL deslocamento dentro do código MSIL original, sem modificações, e cada novo deslocamento refere-se para o deslocamento MSIL dentro do código instrumentado, novo. O mapa deve ser classificado em ordem crescente. Para passar para funcionar corretamente, siga estas diretrizes:  
  
-   Não reordena código MSIL instrumentado.  
  
-   Não remova o código MSIL original.  
  
-   Inclua entradas para todos os pontos de sequência do arquivo de programa (PDB) de banco de dados no mapa. O mapa não interpolar entradas ausentes. Assim, considerando o mapa a seguir:  
  
     (0 antigo, 0 novo)  
  
     (5 antigo, 10 novo)  
  
     (9 old, 20 novo)  
  
    -   Um deslocamento antigo de 0, 1, 2, 3 ou 4 será mapeado para o novo deslocamento de 0.  
  
    -   Um deslocamento antigo de 5, 6, 7 ou 8 será mapeado para o novo deslocamento de 10.  
  
    -   Um deslocamento antigo de 9 ou superior será mapeado para o novo deslocamento 20.  
  
    -   Um novo deslocamento de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 será mapeado para o antigo deslocamento de 0.  
  
    -   Um novo deslocamento de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 será mapeado para o deslocamento antigo 5.  
  
    -   Um novo deslocamento de 20 ou maior será mapeado para deslocamento antigo 9.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
