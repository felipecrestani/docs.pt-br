---
title: Como especificar o modo de edição do controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 5117dfe2e017cf4af1d352fdbf23c6599c0e56a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Como especificar o modo de edição do controle DataGridView dos Windows Forms
Por padrão, os usuários podem editar o conteúdo do atual <xref:System.Windows.Forms.DataGridView> célula da caixa de texto digitando nele ou pressionando F2. Isso colocará a célula no modo de edição se todas as condições a seguir forem atendidas:  
  
-   A fonte de dados subjacente der suporte à edição.  
  
-   O <xref:System.Windows.Forms.DataGridView> controle está habilitado.  
  
-   O valor da propriedade <xref:System.Windows.Forms.DataGridView.EditMode%2A> não é <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
-   As propriedade `ReadOnly` de célula, linha, coluna e controle estiverem definidas como `false`.  
  
 No modo de edição, o usuário pode alterar o valor da célula e pressionar ENTER para confirmar a alteração ou ESC para reverter a célula para seu valor original.  
  
 Você pode configurar um <xref:System.Windows.Forms.DataGridView> controlar de forma que uma célula entra em modo de edição assim que ele se torna a célula atual. O comportamento das teclas ENTER e ESC fica inalterado nesse caso, mas a célula permanece no modo de edição depois que o valor é confirmado ou revertido. Você também pode configurar o controle para que as células entrem no modo de edição somente quando os usuários digitam na célula ou quando pressionam F2. Por fim, você pode impedir que as células no modo de edição, exceto quando você chama o <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> método.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>Para alterar o modo de edição de um controle DataGridView  
  
-   Definir o <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> propriedade apropriada <xref:System.Windows.Forms.DataGridViewEditMode> enumeração.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Referências aos assemblies <xref:System> e <xref:System.Windows.Forms>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [Entrada de Dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
