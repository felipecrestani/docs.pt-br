---
title: Função SpawnInstance (referência de API não gerenciada)
description: A função SpawnInstance cria uma nova instância de uma classe.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f8189f0adb62aa32cd0b85ca5a653aa466c7032
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="spawninstance-function"></a>Função SpawnInstance
Cria uma nova instância de uma classe.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.

`lFlags`  
[in] Reservado. Esse parâmetro deve ser 0.

`ppNewInstance`  
[out] Recebe o ponteiro para a nova instância da classe. Se ocorrer um erro, um novo objeto não é retornado, e `ppNewInstance` é esquerda sem modificações.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr` não é uma definição de classe válido e não é possível gerar novas instâncias. O está incompleto ou não foi registrado com o Windows Management chamando [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` é `null`. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemclassObject:: SpawnInstance](https://msdn.microsoft.com/library/aa391458(v=vs.85).aspx) método.

`ptr` deve ser uma definição de classe obtida do gerenciamento do Windows. (Observe que há suporte para a geração de uma instância de uma instância, mas a instância retornada está vazia). Você usar essa definição de classe para criar novas instâncias. Uma chamada para o [PutInstanceWmi](putinstancewmi.md) função é necessária se você pretende gravar a instância de gerenciamento do Windows.




O novo objeto retornado `ppNewClass` automaticamente se torna uma subclasse do objeto atual. Esse comportamento não pode ser substituído. Não há nenhum outro método pelo qual as subclasses (classes derivadas) podem ser criadas.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
