---
title: Como ancorar e encaixar controles filho em um controle TableLayoutPanel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: eee67d739de13b125aa1eb8ee86de19ba645a2f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Como ancorar e encaixar controles filho em um controle TableLayoutPanel
O <xref:System.Windows.Forms.TableLayoutPanel> controle oferece suporte a <xref:System.Windows.Forms.Control.Anchor%2A> e <xref:System.Windows.Forms.Control.Dock%2A> propriedades em seus controles filhos.  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>Alinhar um controle filho a uma célula TableLayoutPanel  
  
1.  Criar um <xref:System.Windows.Forms.TableLayoutPanel> controle do formulário.  
  
2.  Defina o valor da <xref:System.Windows.Forms.TableLayoutPanel> do controle <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> e <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> propriedades **1**.  
  
3.  Criar um <xref:System.Windows.Forms.Button> controlar o <xref:System.Windows.Forms.TableLayoutPanel> controle. O <xref:System.Windows.Forms.Button> ocupe o canto superior esquerdo da célula.  
  
4.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Left`. O <xref:System.Windows.Forms.Button> move o controle para alinhar com a borda esquerda da célula.  
  
    > [!NOTE]
    >  Esse comportamento difere do comportamento de outras caixas de controles. Em outros controles de contêiner, o controle filho não move quando o <xref:System.Windows.Forms.Control.Anchor%2A> está definida e a distância entre o controle ancorado e limites do contêiner pai é fixo no momento em que o <xref:System.Windows.Forms.Control.Anchor%2A> está definida.  
  
5.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Left`. O <xref:System.Windows.Forms.Button> move o controle para ocupar o canto superior esquerdo da célula.  
  
6.  Repita a etapa 5 com um valor de `Top, Right` para mover o <xref:System.Windows.Forms.Button> controle para o canto superior direito da célula. Repita com valores de `Bottom, Left` e `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>Alongar um controle filho em uma célula TableLayoutPanel  
  
1.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Left, Right`. O <xref:System.Windows.Forms.Button> controle é redimensionado para alongar para a célula.  
  
    > [!NOTE]
    >  Esse comportamento difere do comportamento de outras caixas de controles. Em outros controles de contêiner, o controle filho não é redimensionado quando o <xref:System.Windows.Forms.Control.Anchor%2A> está definida como `Left, Right` ou `Top, Bottom`.  
  
2.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Bottom`. O <xref:System.Windows.Forms.Button> controle é redimensionado para alongar da parte superior para a parte inferior da célula.  
  
3.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `Top, Bottom, Left, Right`. O <xref:System.Windows.Forms.Button> controle é redimensionado para preencher a célula.  
  
4.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade `None`. O <xref:System.Windows.Forms.Button> controle é redimensionado e centralizado na célula.  
  
5.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Left>. O <xref:System.Windows.Forms.Button> move o controle para alinhar com a borda esquerda da célula. O <xref:System.Windows.Forms.Button> controle retém sua largura, mas sua altura é redimensionada para preencher a célula verticalmente.  
  
    > [!NOTE]
    >  Esse é o mesmo comportamento que ocorre em outras caixas de controle.  
  
6.  Alterar o valor da <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>. O <xref:System.Windows.Forms.Button> controle é redimensionado para preencher a célula.  
  
## <a name="example"></a>Exemplo  
 A ilustração a seguir mostra cinco botões ancorado em cinco separada <xref:System.Windows.Forms.TableLayoutPanel> células.  
  
 ![Ancoragem TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 A ilustração a seguir mostra quatro botões ancorado nos cantos do separado quatro <xref:System.Windows.Forms.TableLayoutPanel> células.  
  
 ![Ancoragem TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 A ilustração a seguir mostra três botões ampliados por ancoragem em três separada <xref:System.Windows.Forms.TableLayoutPanel> células.  
  
 ![Ancoragem TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 O exemplo de código a seguir demonstra todas as combinações de <xref:System.Windows.Forms.Control.Anchor%2A> valores de propriedades de um <xref:System.Windows.Forms.Button> controlar um <xref:System.Windows.Forms.TableLayoutPanel> controle.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Controle TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
