---
title: Como agrupar controles com o controle do painel dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1d4a49f36ac294199871075a04b7e682bd5613b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="1bded-102">Como agrupar controles com o controle do painel dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="1bded-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="1bded-103">Windows Forms <xref:System.Windows.Forms.Panel> controles são usados para agrupar outros controles.</span><span class="sxs-lookup"><span data-stu-id="1bded-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="1bded-104">Há três razões para agrupar controles.</span><span class="sxs-lookup"><span data-stu-id="1bded-104">There are three reasons to group controls.</span></span> <span data-ttu-id="1bded-105">Uma delas é o agrupamento visual de elementos de formulários relacionados para uma interface do usuário clara; a outra é o agrupamento programático dos botões de opção, por exemplo; a última é para mover os controles como uma unidade em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="1bded-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bded-106">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="1bded-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1bded-107">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="1bded-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1bded-108">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1bded-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="1bded-109">Para criar um grupo de controles</span><span class="sxs-lookup"><span data-stu-id="1bded-109">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="1bded-110">Arraste um <xref:System.Windows.Forms.Panel> controlar do **Windows Forms** guia da caixa de ferramentas para um formulário.</span><span class="sxs-lookup"><span data-stu-id="1bded-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2.  <span data-ttu-id="1bded-111">Adicione outros controles ao painel desenhando cada um deles dentro do painel.</span><span class="sxs-lookup"><span data-stu-id="1bded-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="1bded-112">Se você tiver controles existentes que você deseja incluir em um painel, você pode selecionar todos os controles, recortá-los para a área de transferência, selecione o <xref:System.Windows.Forms.Panel> de controle e, em seguida, cole-os para o painel.</span><span class="sxs-lookup"><span data-stu-id="1bded-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="1bded-113">Você também pode arrastá-los para o painel.</span><span class="sxs-lookup"><span data-stu-id="1bded-113">You can also drag them into the panel.</span></span>  
  
3.  <span data-ttu-id="1bded-114">(Opcional) Se você deseja adicionar uma borda a um painel, defina seu <xref:System.Windows.Forms.BorderStyle> propriedade.</span><span class="sxs-lookup"><span data-stu-id="1bded-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="1bded-115">Há três opções: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, e <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="1bded-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bded-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bded-116">See Also</span></span>  
 [<span data-ttu-id="1bded-117">Controle de painel</span><span class="sxs-lookup"><span data-stu-id="1bded-117">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="1bded-118">Visão geral do controle Panel</span><span class="sxs-lookup"><span data-stu-id="1bded-118">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="1bded-119">Como definir a tela de fundo de um painel</span><span class="sxs-lookup"><span data-stu-id="1bded-119">How to: Set the Background of a Panel</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)