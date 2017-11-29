---
title: Estilos e modelos TextBox
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f5cfd1c0715c7f9610f85201cd40a3973a2be64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="20a4c-102">Estilos e modelos TextBox</span><span class="sxs-lookup"><span data-stu-id="20a4c-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="20a4c-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="20a4c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="20a4c-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="20a4c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="20a4c-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="20a4c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="20a4c-106">Partes da caixa de texto</span><span class="sxs-lookup"><span data-stu-id="20a4c-106">TextBox Parts</span></span>  
 <span data-ttu-id="20a4c-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="20a4c-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="20a4c-108">Parte</span><span class="sxs-lookup"><span data-stu-id="20a4c-108">Part</span></span>|<span data-ttu-id="20a4c-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="20a4c-109">Type</span></span>|<span data-ttu-id="20a4c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="20a4c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="20a4c-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="20a4c-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="20a4c-112">Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="20a4c-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="20a4c-113">O texto do <xref:System.Windows.Controls.TextBox> é exibido neste elemento.</span><span class="sxs-lookup"><span data-stu-id="20a4c-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="20a4c-114">Estados de caixa de texto</span><span class="sxs-lookup"><span data-stu-id="20a4c-114">TextBox States</span></span>  
 <span data-ttu-id="20a4c-115">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="20a4c-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="20a4c-116">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="20a4c-116">VisualState Name</span></span>|<span data-ttu-id="20a4c-117">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="20a4c-117">VisualStateGroup Name</span></span>|<span data-ttu-id="20a4c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="20a4c-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="20a4c-119">Normal</span><span class="sxs-lookup"><span data-stu-id="20a4c-119">Normal</span></span>|<span data-ttu-id="20a4c-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="20a4c-120">CommonStates</span></span>|<span data-ttu-id="20a4c-121">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="20a4c-121">The default state.</span></span>|  
|<span data-ttu-id="20a4c-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="20a4c-122">MouseOver</span></span>|<span data-ttu-id="20a4c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="20a4c-123">CommonStates</span></span>|<span data-ttu-id="20a4c-124">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="20a4c-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="20a4c-125">Disabled</span><span class="sxs-lookup"><span data-stu-id="20a4c-125">Disabled</span></span>|<span data-ttu-id="20a4c-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="20a4c-126">CommonStates</span></span>|<span data-ttu-id="20a4c-127">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="20a4c-127">The control is disabled.</span></span>|  
|<span data-ttu-id="20a4c-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="20a4c-128">ReadOnly</span></span>|<span data-ttu-id="20a4c-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="20a4c-129">CommonStates</span></span>|<span data-ttu-id="20a4c-130">O usuário não pode alterar o texto de <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="20a4c-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="20a4c-131">Focalizado</span><span class="sxs-lookup"><span data-stu-id="20a4c-131">Focused</span></span>|<span data-ttu-id="20a4c-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="20a4c-132">FocusStates</span></span>|<span data-ttu-id="20a4c-133">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="20a4c-133">The control has focus.</span></span>|  
|<span data-ttu-id="20a4c-134">Sem foco</span><span class="sxs-lookup"><span data-stu-id="20a4c-134">Unfocused</span></span>|<span data-ttu-id="20a4c-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="20a4c-135">FocusStates</span></span>|<span data-ttu-id="20a4c-136">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="20a4c-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="20a4c-137">Válido</span><span class="sxs-lookup"><span data-stu-id="20a4c-137">Valid</span></span>|<span data-ttu-id="20a4c-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="20a4c-138">ValidationStates</span></span>|<span data-ttu-id="20a4c-139">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="20a4c-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="20a4c-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="20a4c-140">InvalidFocused</span></span>|<span data-ttu-id="20a4c-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="20a4c-141">ValidationStates</span></span>|<span data-ttu-id="20a4c-142">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="20a4c-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="20a4c-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="20a4c-143">InvalidUnfocused</span></span>|<span data-ttu-id="20a4c-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="20a4c-144">ValidationStates</span></span>|<span data-ttu-id="20a4c-145">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="20a4c-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="20a4c-146">Exemplo de ControlTemplate de caixa de texto</span><span class="sxs-lookup"><span data-stu-id="20a4c-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="20a4c-147">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="20a4c-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="20a4c-148">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="20a4c-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="20a4c-149">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="20a4c-149">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a4c-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20a4c-150">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="20a4c-151">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="20a4c-151">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="20a4c-152">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="20a4c-152">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="20a4c-153">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="20a4c-153">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="20a4c-154">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="20a4c-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)