---
title: "Instruções passo a passo: mapeando propriedades usando o controle ElementHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dae954012d15431d2019d3d9cbe61747a8646d4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="4a64b-102">Instruções passo a passo: mapeando propriedades usando o controle ElementHost</span><span class="sxs-lookup"><span data-stu-id="4a64b-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>
<span data-ttu-id="4a64b-103">Este passo a passo mostra como usar o <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> propriedade mapear [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] propriedades às propriedades correspondentes em hospedado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemento.</span><span class="sxs-lookup"><span data-stu-id="4a64b-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>  
  
 <span data-ttu-id="4a64b-104">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="4a64b-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="4a64b-105">Criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="4a64b-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="4a64b-106">Definir um novo mapeamento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4a64b-106">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="4a64b-107">Remover um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="4a64b-107">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="4a64b-108">Estender um mapeamento de propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="4a64b-108">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="4a64b-109">Para ver uma listagem de código completa de todas tarefas ilustradas nesta instrução passo a passo, consulte [Mapeando propriedades usando o exemplo de controle ElementHost](http://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="4a64b-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](http://go.microsoft.com/fwlink/?LinkID=160018).</span></span>  
  
 <span data-ttu-id="4a64b-110">Quando você terminar, poderá mapear propriedades [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] para as propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondentes em um elemento hospedado.</span><span class="sxs-lookup"><span data-stu-id="4a64b-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4a64b-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4a64b-111">Prerequisites</span></span>  
 <span data-ttu-id="4a64b-112">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="4a64b-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="4a64b-113">.</span><span class="sxs-lookup"><span data-stu-id="4a64b-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="4a64b-114">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="4a64b-114">Creating the Project</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="4a64b-115">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="4a64b-115">To create the project</span></span>  
  
1.  <span data-ttu-id="4a64b-116">Crie um projeto de aplicativo [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] chamado `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="4a64b-116">Create a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project named `PropertyMappingWithElementHost`.</span></span> <span data-ttu-id="4a64b-117">Para obter mais informações, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="4a64b-117">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="4a64b-118">No Gerenciador de Soluções, adicione referências aos assemblies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a seguir.</span><span class="sxs-lookup"><span data-stu-id="4a64b-118">In Solution Explorer, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>  
  
    -   <span data-ttu-id="4a64b-119">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="4a64b-119">PresentationCore</span></span>  
  
    -   <span data-ttu-id="4a64b-120">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="4a64b-120">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="4a64b-121">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="4a64b-121">WindowsBase</span></span>  
  
    -   <span data-ttu-id="4a64b-122">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="4a64b-122">WindowsFormsIntegration</span></span>  
  
3.  <span data-ttu-id="4a64b-123">Copie o seguinte código na parte superior do arquivo de código `Form1`.</span><span class="sxs-lookup"><span data-stu-id="4a64b-123">Copy the following code into the top of the `Form1` code file.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="4a64b-124">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="4a64b-124">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="4a64b-125">Clique duas vezes no formulário para adicionar um manipulador de eventos para o <xref:System.Windows.Forms.Form.Load> evento.</span><span class="sxs-lookup"><span data-stu-id="4a64b-125">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
5.  <span data-ttu-id="4a64b-126">Retornar ao Designer de formulários do Windows e adicionar um manipulador de eventos para o formulário <xref:System.Windows.Forms.Control.Resize> eventos.</span><span class="sxs-lookup"><span data-stu-id="4a64b-126">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="4a64b-127">Para obter mais informações, consulte [Como criar manipuladores de eventos usando o Designer](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).</span><span class="sxs-lookup"><span data-stu-id="4a64b-127">For more information, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>  
  
6.  <span data-ttu-id="4a64b-128">Declarar um <xref:System.Windows.Forms.Integration.ElementHost> campo o `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="4a64b-128">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a><span data-ttu-id="4a64b-129">Definindo novos mapeamentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="4a64b-129">Defining New Property Mappings</span></span>  
 <span data-ttu-id="4a64b-130">O <xref:System.Windows.Forms.Integration.ElementHost> controle fornece vários propriedade mapeamentos padrão.</span><span class="sxs-lookup"><span data-stu-id="4a64b-130">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="4a64b-131">Você adiciona um novo mapeamento de propriedade chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> método o <xref:System.Windows.Forms.Integration.ElementHost> do controle <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a64b-131">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-new-property-mappings"></a><span data-ttu-id="4a64b-132">Definir novos mapeamentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="4a64b-132">To define new property mappings</span></span>  
  
1.  <span data-ttu-id="4a64b-133">Copie o código a seguir para a definição da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="4a64b-133">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     <span data-ttu-id="4a64b-134">O `AddMarginMapping` método adiciona um novo mapeamento para o <xref:System.Windows.Forms.Control.Margin%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4a64b-134">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>  
  
     <span data-ttu-id="4a64b-135">O `OnMarginChange` método converte o <xref:System.Windows.Forms.Control.Margin%2A> propriedade para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4a64b-135">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>  
  
2.  <span data-ttu-id="4a64b-136">Copie o código a seguir para a definição da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="4a64b-136">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     <span data-ttu-id="4a64b-137">O `AddRegionMapping` método adiciona um novo mapeamento para o <xref:System.Windows.Forms.Control.Region%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4a64b-137">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="4a64b-138">O `OnRegionChange` método converte o <xref:System.Windows.Forms.Control.Region%2A> propriedade para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4a64b-138">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="4a64b-139">O `Form1_Resize` método trata do formulário <xref:System.Windows.Forms.Control.Resize> eventos e dimensiona a região de recorte para encaixar o elemento hospedado.</span><span class="sxs-lookup"><span data-stu-id="4a64b-139">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="4a64b-140">Removendo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="4a64b-140">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="4a64b-141">Remover um mapeamento de propriedade padrão chamando o <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> método sobre o <xref:System.Windows.Forms.Integration.ElementHost> do controle <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a64b-141">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="4a64b-142">Remover um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="4a64b-142">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="4a64b-143">Copie o código a seguir para a definição da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="4a64b-143">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     <span data-ttu-id="4a64b-144">O `RemoveCursorMapping` método exclui o mapeamento padrão para o <xref:System.Windows.Forms.Control.Cursor%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4a64b-144">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="4a64b-145">Estendendo um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="4a64b-145">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="4a64b-146">Você pode usar um mapeamento de propriedade padrão e também estendê-lo com seu próprio mapeamento.</span><span class="sxs-lookup"><span data-stu-id="4a64b-146">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="4a64b-147">Estender um mapeamento de propriedade padrão</span><span class="sxs-lookup"><span data-stu-id="4a64b-147">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="4a64b-148">Copie o código a seguir para a definição da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="4a64b-148">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     <span data-ttu-id="4a64b-149">O `ExtendBackColorMapping` método adiciona um tradutor de propriedade personalizada para existente <xref:System.Windows.Forms.Control.BackColor%2A> mapeamento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4a64b-149">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>  
  
     <span data-ttu-id="4a64b-150">O `OnBackColorChange` método define uma imagem específica para o controle hospedado <xref:System.Windows.Controls.Control.Background%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4a64b-150">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="4a64b-151">O método `OnBackColorChange` é chamado depois que o mapeamento de propriedade padrão é aplicado.</span><span class="sxs-lookup"><span data-stu-id="4a64b-151">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="4a64b-152">Inicializando seus mapeamentos de propriedades</span><span class="sxs-lookup"><span data-stu-id="4a64b-152">Initializing Your Property Mappings</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="4a64b-153">Inicializar seus mapeamentos de propriedades</span><span class="sxs-lookup"><span data-stu-id="4a64b-153">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="4a64b-154">Copie o código a seguir para a definição da classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="4a64b-154">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     <span data-ttu-id="4a64b-155">O `Form1_Load` método trata o <xref:System.Windows.Forms.Form.Load> eventos e realiza a seguinte inicialização.</span><span class="sxs-lookup"><span data-stu-id="4a64b-155">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="4a64b-156">Cria um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> elemento.</span><span class="sxs-lookup"><span data-stu-id="4a64b-156">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>  
  
    -   <span data-ttu-id="4a64b-157">Chama os métodos definidos anteriormente no passo a passo para configurar os mapeamentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4a64b-157">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="4a64b-158">Atribui valores iniciais para as propriedades mapeadas.</span><span class="sxs-lookup"><span data-stu-id="4a64b-158">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="4a64b-159">Pressione F5 para compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a64b-159">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a64b-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a64b-160">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="4a64b-161">Windows Forms e mapeamento de propriedade do WPF</span><span class="sxs-lookup"><span data-stu-id="4a64b-161">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="4a64b-162">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="4a64b-162">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="4a64b-163">Passo a passo: hospedando um controle composto do WPF no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4a64b-163">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)