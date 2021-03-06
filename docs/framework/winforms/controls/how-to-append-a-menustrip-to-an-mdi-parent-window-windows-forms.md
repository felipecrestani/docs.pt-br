---
title: Como acrescentar um MenuStrip a uma janela pai MDI (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 048add340a81856cd30482c52c93c76bbf6181f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>Como acrescentar um MenuStrip a uma janela pai MDI (Windows Forms)
Em alguns aplicativos, o tipo de uma janela filho MDI (interface de vários documentos) pode ser diferente da janela MDI pai. Por exemplo, a MDI pai pode ser uma planilha e a MDI filho pode ser um gráfico. Nesse caso, é recomendável atualizar o conteúdo do menu da MDI pai com o conteúdo do menu da MDI filho, visto que janelas MDI filho de tipos diferentes são ativadas.  
  
 O procedimento a seguir usa o <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, e <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> propriedades para acrescentar o menu filho MDI ao menu MDI pai. Fechar a janela filho MDI remove o menu acrescentado do MDI pai.  
  
 Consulte também [Aplicativos MDI (Interface de Vários Documentos)](http://msdn.microsoft.com/library/xyhh2e7e\(v=vs.110\)).  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>Acrescentar um item de menu a um pai MDI  
  
1.  Criar um formulário e defina seu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade `true`.  
  
2.  Adicionar um <xref:System.Windows.Forms.MenuStrip> para `Form1` e defina o <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> propriedade o <xref:System.Windows.Forms.MenuStrip> para `true`.  
  
3.  Definir o <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade o `Form1` <xref:System.Windows.Forms.MenuStrip> para `false`.  
  
4.  Adicionar um item de menu de nível superior para o `Form1` <xref:System.Windows.Forms.MenuStrip> e defina seu <xref:System.Windows.Forms.Control.Text%2A> propriedade `&File`.  
  
5.  Adicionar um item de submenu a `&File` item de menu e defina seu <xref:System.Windows.Forms.Form.Text%2A> propriedade `&Open`.  
  
6.  Adicionar um formulário para o projeto, adicione um <xref:System.Windows.Forms.MenuStrip> para o formulário e o <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> propriedade do `Form2` <xref:System.Windows.Forms.MenuStrip> para `true`.  
  
7.  Adicionar um item de menu de nível superior para o `Form2` <xref:System.Windows.Forms.MenuStrip> e defina seu <xref:System.Windows.Forms.Form.Text%2A> propriedade `&Special`.  
  
8.  Adicionar dois itens de submenu para o `&Special` item de menu e defina seus <xref:System.Windows.Forms.Form.Text%2A> propriedades `Command&1` e `Command&2`, respectivamente.  
  
9. Definir o <xref:System.Windows.Forms.MergeAction> propriedade o `&Special`, `Command&1`, e `Command&2` itens de menu <xref:System.Windows.Forms.MergeAction.Append>.  
  
10. Criar um manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> evento o `&New` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. No manipulador de eventos, insira um código semelhante ao exemplo de código a seguir para criar e exibir novas instâncias de `Form2` como filhos MDI de `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. Coloque o código semelhante ao exemplo de código a seguir no `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> para registrar o manipulador de eventos.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Dois <xref:System.Windows.Forms.Form> controles denominados `Form1` e `Form2`.  
  
-   Um <xref:System.Windows.Forms.MenuStrip> control em `Form1` chamado `menuStrip1`e um <xref:System.Windows.Forms.MenuStrip> control em `Form2` chamado `menuStrip2`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.
