---
title: Enumeração CorImportOptions
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7078b2eb98c15b7229132076da8af4691032bb08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corimportoptions-enumeration"></a>Enumeração CorImportOptions
Contém valores de sinalizadores que controlam o comportamento durante a importação de um assembly fora do escopo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`MDImportOptionDefault`|Indica o comportamento padrão, que é ignorar os registros excluídos.|  
|`MDImportOptionAll`|Indica que todos os metadados devem ser enumerados.|  
|`MDImportOptionAllTypeDefs`|Indica que todas as definições de tipo, incluindo aquelas excluído, devem ser enumeradas.|  
|`MDImportOptionAllMethodDefs`|Indica que todos os MethodDefs, incluindo aquelas excluído, deve ser enumerados.|  
|`MDImportOptionAllFieldDefs`|Indica que todos os FieldDefs, incluindo aquelas excluído, deve ser enumerados.|  
|`MDImportOptionAllProperties`|Indica que todos os PropertyDefs, incluindo aquelas excluído, deve ser enumerados.|  
|`MDImportOptionAllEvents`|Indica que todos os EventDefs, incluindo aquelas excluído, deve ser enumerados.|  
|`MDImportOptionAllCustomAttributes`|Indica que todos os atributos personalizados, incluindo aquelas excluído, devem ser enumerados.|  
|`MDImportOptionAllExportedTypes`|Indica que todos os tipos exportados, incluindo aquelas excluído, devem ser enumerados.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
