---
title: Visão geral do componente PrintDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0b0e516364277133efc83e7324345ccea8328690
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="printdialog-component-overview-windows-forms"></a>Visão geral do componente PrintDialog (Windows Forms)
O componente [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) dos Windows Forms é uma caixa de diálogo pré-configurada usada para selecionar uma impressora, escolher as páginas a serem impressas e determinar outras configurações relacionadas à impressão em aplicativos baseados no Windows. Use-o como uma solução simples para seleção de impressora e de configurações relacionadas à impressão em vez de configurar sua própria caixa de diálogo. Você pode habilitar os usuários a imprimir muitas partes de seus documentos: imprimir tudo, imprimir um intervalo de páginas selecionadas ou uma seleção. Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários. O <xref:System.Windows.Forms.PrintDialog> componente herda o <xref:System.Windows.Forms.CommonDialog> classe.  
  
## <a name="working-with-the-component"></a>Como trabalhar com o componente  
 Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo em tempo de execução. Este componente tem propriedades relacionadas a um único trabalho de impressão (<xref:System.Drawing.Printing.PrintDocument> classe) ou as configurações de uma impressora individual (<xref:System.Drawing.Printing.PrinterSettings> classe). Um deles, por sua vez, pode ser compartilhado por várias impressoras.  
  
 Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.PrintDialog> componente aparece na bandeja de na parte inferior do Designer de formulários do Windows.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.PrintDialog>  
 [Componente PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
