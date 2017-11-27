---
title: Como localizar um TreeViewItem em um TreeView
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
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a231f5eae92bff8e3d525579dae865aaa0d7e496
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a><span data-ttu-id="6643c-102">Como localizar um TreeViewItem em um TreeView</span><span class="sxs-lookup"><span data-stu-id="6643c-102">How to: Find a TreeViewItem in a TreeView</span></span>
<span data-ttu-id="6643c-103">O <xref:System.Windows.Controls.TreeView> controle fornece uma maneira conveniente de exibir dados hierárquicos.</span><span class="sxs-lookup"><span data-stu-id="6643c-103">The <xref:System.Windows.Controls.TreeView> control provides a convenient way to display hierarchical data.</span></span> <span data-ttu-id="6643c-104">Se seu <xref:System.Windows.Controls.TreeView> está associado a uma fonte de dados, o <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriedade fornece uma maneira conveniente para recuperar rapidamente o objeto de dados selecionado.</span><span class="sxs-lookup"><span data-stu-id="6643c-104">If your <xref:System.Windows.Controls.TreeView> is bound to a data source, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property provides a convenient way for you to quickly retrieve the selected data object.</span></span> <span data-ttu-id="6643c-105">É geralmente a melhor trabalhar com o objeto de dados subjacente, mas, às vezes, talvez seja necessário manipular programaticamente os dados que contém <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="6643c-105">It is typically best to work with the underlying data object, but sometimes you may need to programmatically manipulate the data's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="6643c-106">Por exemplo, talvez seja necessário expandir programaticamente o <xref:System.Windows.Controls.TreeViewItem>, ou selecione um item diferente no <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="6643c-106">For example, you may need to programmatically expand the <xref:System.Windows.Controls.TreeViewItem>, or select a different item in the <xref:System.Windows.Controls.TreeView>.</span></span>  
  
 <span data-ttu-id="6643c-107">Para localizar um <xref:System.Windows.Controls.TreeViewItem> que contém um objeto de dados específico, você deve percorrer cada nível do <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="6643c-107">To find a <xref:System.Windows.Controls.TreeViewItem> that contains a specific data object, you must traverse each level of the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="6643c-108">Os itens em uma <xref:System.Windows.Controls.TreeView> também podem ser virtualizadas para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="6643c-108">The items in a <xref:System.Windows.Controls.TreeView> can also be virtualized to improve performance.</span></span> <span data-ttu-id="6643c-109">No caso em que os itens podem ser virtualizados, você também deve obter um <xref:System.Windows.Controls.TreeViewItem> para verificar se ele contém o objeto de dados.</span><span class="sxs-lookup"><span data-stu-id="6643c-109">In the case where items might be virtualized, you also must realize a <xref:System.Windows.Controls.TreeViewItem> to check whether it contains the data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6643c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6643c-110">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="6643c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="6643c-111">Description</span></span>  
 <span data-ttu-id="6643c-112">O exemplo seguinte pesquisa uma <xref:System.Windows.Controls.TreeView> para um objeto específico e retorna o objeto que contém <xref:System.Windows.Controls.TreeViewItem>.</span><span class="sxs-lookup"><span data-stu-id="6643c-112">The following example searches a <xref:System.Windows.Controls.TreeView> for a specific object and returns the object's containing <xref:System.Windows.Controls.TreeViewItem>.</span></span> <span data-ttu-id="6643c-113">O exemplo garante que cada <xref:System.Windows.Controls.TreeViewItem> é instanciada para que seus itens filho podem ser pesquisados.</span><span class="sxs-lookup"><span data-stu-id="6643c-113">The example ensures that each <xref:System.Windows.Controls.TreeViewItem> is instantiated so that its child items can be searched.</span></span> <span data-ttu-id="6643c-114">Este exemplo também funciona se o <xref:System.Windows.Controls.TreeView> não usa itens virtualizados.</span><span class="sxs-lookup"><span data-stu-id="6643c-114">This example also works if the <xref:System.Windows.Controls.TreeView> does not use virtualized items.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6643c-115">O exemplo a seguir funciona para qualquer <xref:System.Windows.Controls.TreeView>, independentemente do modelo de dados subjacente e pesquisas cada <xref:System.Windows.Controls.TreeViewItem> até que o objeto for encontrado.</span><span class="sxs-lookup"><span data-stu-id="6643c-115">The following example works for any <xref:System.Windows.Controls.TreeView>, regardless of the underlying data model, and searches every <xref:System.Windows.Controls.TreeViewItem> until the object is found.</span></span> <span data-ttu-id="6643c-116">Outra técnica que tem um desempenho melhor é pesquisar o modelo de dados para o objeto especificado, manter o controle de seu local dentro da hierarquia de dados e, em seguida, localizar correspondente <xref:System.Windows.Controls.TreeViewItem> no <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="6643c-116">Another technique that has better performance is to search the data model for the specified object, keep track of its location within the data hierarchy, and then find the corresponding <xref:System.Windows.Controls.TreeViewItem> in the <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="6643c-117">No entanto, a técnica que tem um desempenho melhor requer conhecimento sobre o modelo de dados e não pode ser generalizada para qualquer dado <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="6643c-117">However, the technique that has better performance requires knowledge of the data model and cannot be generalized for any given <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="6643c-118">Código</span><span class="sxs-lookup"><span data-stu-id="6643c-118">Code</span></span>  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 <span data-ttu-id="6643c-119">O código anterior se baseia em um personalizado <xref:System.Windows.Controls.VirtualizingStackPanel> que expõe um método chamado `BringIntoView`.</span><span class="sxs-lookup"><span data-stu-id="6643c-119">The previous code relies on a custom <xref:System.Windows.Controls.VirtualizingStackPanel> that exposes a method named `BringIntoView`.</span></span> <span data-ttu-id="6643c-120">O código a seguir define personalizado <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="6643c-120">The following code defines the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 <span data-ttu-id="6643c-121">O XAML a seguir mostra como criar um <xref:System.Windows.Controls.TreeView> que usa personalizado <xref:System.Windows.Controls.VirtualizingStackPanel>.</span><span class="sxs-lookup"><span data-stu-id="6643c-121">The following XAML shows how to create a <xref:System.Windows.Controls.TreeView> that uses the custom <xref:System.Windows.Controls.VirtualizingStackPanel>.</span></span>  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6643c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6643c-122">See Also</span></span>  
 [<span data-ttu-id="6643c-123">Melhorar o desempenho de um TreeView</span><span class="sxs-lookup"><span data-stu-id="6643c-123">Improve the Performance of a TreeView</span></span>](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)