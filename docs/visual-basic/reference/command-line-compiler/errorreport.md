---
title: -errorreport
ms.date: 03/10/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8c6a81d3491f4876cfbca80aa8fda6640187176
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-errorreport"></a>-errorreport
Especifica como o compilador do Visual Basic deve relatar erros do compilador interno.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>Comentários  
 Essa opção fornece uma maneira conveniente para relatar um erro interno do compilador do Visual Basic (ICE) para a equipe do Visual Basic na Microsoft. Por padrão, o compilador não envia nenhuma informação à Microsoft. No entanto, se você encontrar um erro interno do compilador, esta opção permite que você relate o erro à Microsoft. Essas informações ajudam os engenheiros da Microsoft a identificar a causa e podem ajudar a melhorar a próxima versão do Visual Basic.  
  
 Capacidade de um usuário para enviar relatórios depende de permissões de política de computador e de usuário.  
  
 A tabela a seguir resume o efeito do `-errorreport` opção.  
  
|Opção|Comportamento|  
|---|---|  
|`prompt`|Se ocorrer um erro interno do compilador, uma caixa de diálogo aparece para que você pode exibir os dados exatos que o compilador coletado. Você pode determinar se não houver nenhuma informação confidencial no relatório de erros e tomar uma decisão sobre se deseja enviá-lo à Microsoft. Se você optar por enviá-lo, e as configurações de política de computador e usuário permitirem, o compilador envia os dados à Microsoft.|  
|`queue`|Enfileira o relatório de erros. Quando você faz logon com privilégios de administrador, você pode relatar falhas desde a última vez em que você estava logado (você não precisará enviar relatórios de falhas mais de uma vez a cada três dias). Esse é o comportamento padrão quando o `-errorreport` opção não for especificada.|  
|`send`|Se ocorrer um erro interno do compilador, e as configurações de política de computador e usuário permitirem, o compilador envia os dados à Microsoft.<br /><br /> A opção `-errorreport:send` tenta enviar automaticamente informações de erro à Microsoft. Essa opção depende do registro. Para obter mais informações sobre como definir os valores apropriados no registro, consulte [como ativar o relatório de erros automático em ferramentas de linha de comando do Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695).|  
|`none`|Se ocorrer um erro interno do compilador, ele não será coletado ou enviado à Microsoft.|  
  
 O compilador envia os dados que incluem a pilha no momento do erro, que geralmente inclui alguns código-fonte. Se `-errorreport` é usado com o [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, em seguida, o arquivo de origem inteiro é enviado.  
  
 Essa opção é melhor usada com a [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, pois ela permite que os engenheiros da Microsoft mais facilmente reproduza o erro.  
  
> [!NOTE]
>  O `-errorreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir tenta compilar `T2.vb`, e se o compilador encontra um erro interno do compilador, ele solicitará a enviar o relatório de erros à Microsoft.  
  
```  
vbc -errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
