---
title: Número de registro incorreto
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 400879ba37c6b3215d9570ca6eb8eaa06edea03b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="bad-record-number"></a>Número de registro incorreto
O número do registro em `a FileGet`, `FilePut`, `FileGetObject`, ou `FilePutObject` instrução é menor ou igual a zero.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique os cálculos usados para gerar o número do registro. Verifique se as variáveis que contém o número de registro ou usada no cálculo de números de registro. Um nome de variável digitado incorretamente é implicitamente declarado e inicializado como zero, a menos que você usou `Option Explicit On` no módulo.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Option Explicit](../../visual-basic/language-reference/statements/option-explicit-statement.md)
