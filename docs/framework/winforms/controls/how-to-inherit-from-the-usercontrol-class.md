---
title: Como herdar da classe UserControl
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fbeb2712742ae4c500ccd14a19c397d5d411c73a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="a0471-102">Como herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="a0471-102">How to: Inherit from the UserControl Class</span></span>
<span data-ttu-id="a0471-103">Para combinar a funcionalidade de um ou mais controles do Windows Forms no modo personalizado, é possível criar um *controle de usuário*.</span><span class="sxs-lookup"><span data-stu-id="a0471-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="a0471-104">Os controles de usuário combinam rápido desenvolvimento de controle, a funcionalidade padrão de controle do Windows Forms e a versatilidade de propriedades e métodos personalizados.</span><span class="sxs-lookup"><span data-stu-id="a0471-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="a0471-105">Ao começar a criar um controle de usuário tomamos contato com um designer visível, sobre o qual é possível colocar controles padrão do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a0471-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="a0471-106">Esses controles mantêm todas suas funcionalidades inerentes, bem como a aparência e o comportamento (look and feel) dos controles padrão.</span><span class="sxs-lookup"><span data-stu-id="a0471-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="a0471-107">No entanto, uma vez que esses controles são incorporados no controle de usuário, eles não estão mais disponíveis por meio de código.</span><span class="sxs-lookup"><span data-stu-id="a0471-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="a0471-108">O controle de usuário faz sua própria pintura e também manipula toda a funcionalidade básica associada com controles.</span><span class="sxs-lookup"><span data-stu-id="a0471-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0471-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="a0471-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a0471-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a0471-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a0471-111">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="a0471-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-user-control"></a><span data-ttu-id="a0471-112">Para criar um controle de usuário</span><span class="sxs-lookup"><span data-stu-id="a0471-112">To create a user control</span></span>  
  
1.  <span data-ttu-id="a0471-113">Criar um novo projeto de **Biblioteca de Controle do Windows**.</span><span class="sxs-lookup"><span data-stu-id="a0471-113">Create a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="a0471-114">Um novo projeto é criado com um controle de usuário em branco.</span><span class="sxs-lookup"><span data-stu-id="a0471-114">A new project is created with a blank user control.</span></span>  
  
2.  <span data-ttu-id="a0471-115">Arraste os controles da aba **Windows Forms** da **Caixa de ferramentas** para o designer.</span><span class="sxs-lookup"><span data-stu-id="a0471-115">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>  
  
3.  <span data-ttu-id="a0471-116">Esses controles devem ser posicionados e projetados como se deseja que eles apareçam no controle de usuário final.</span><span class="sxs-lookup"><span data-stu-id="a0471-116">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="a0471-117">Se quiser permitir que os desenvolvedores acessem os controles constituintes, será preciso declará-los como públicos ou exibir seletivamente as propriedades do controle constituinte.</span><span class="sxs-lookup"><span data-stu-id="a0471-117">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="a0471-118">Para mais detalhes, consulte [Como expor propriedades de controles constituintes](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a0471-118">For details, see [How to: Expose Properties of Constituent Controls](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).</span></span>  
  
4.  <span data-ttu-id="a0471-119">Implemente os métodos ou propriedades personalizados que o controle incorporará.</span><span class="sxs-lookup"><span data-stu-id="a0471-119">Implement any custom methods or properties that your control will incorporate.</span></span>  
  
5.  <span data-ttu-id="a0471-120">Pressione F5 para compilar o projeto e executar o controle no **Contêiner de Teste de UserControl**.</span><span class="sxs-lookup"><span data-stu-id="a0471-120">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="a0471-121">Para obter mais informações, consulte [Como testar o comportamento em tempo de execução de um UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="a0471-121">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0471-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0471-122">See Also</span></span>  
 [<span data-ttu-id="a0471-123">Variedades de Controles Personalizados</span><span class="sxs-lookup"><span data-stu-id="a0471-123">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="a0471-124">Como herdar da classe de controle</span><span class="sxs-lookup"><span data-stu-id="a0471-124">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [<span data-ttu-id="a0471-125">Como herdar de controles dos Windows Forms existentes</span><span class="sxs-lookup"><span data-stu-id="a0471-125">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="a0471-126">Como Criar Controles para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0471-126">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="a0471-127">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0471-127">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="a0471-128">Como testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="a0471-128">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)