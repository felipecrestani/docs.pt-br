---
title: "Exemplos de sintaxe da consulta com base em método: Projeção (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0fc2c8f0-1967-4f30-8b20-39b8dccfb82f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6d6ab77a362808a099d12b6698dfd3aca6e5ca84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="method-based-query-syntax-examples-projection-linq-to-dataset"></a><span data-ttu-id="dcb87-102">Exemplos de sintaxe da consulta com base em método: Projeção (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="dcb87-102">Method-Based Query Syntax Examples: Projection (LINQ to DataSet)</span></span>
<span data-ttu-id="dcb87-103">Os exemplos neste tópico demonstram como usar os métodos de <xref:System.Linq.Enumerable.Select%2A> e de <xref:System.Linq.Enumerable.SelectMany%2A> para ver <xref:System.Data.DataSet> usando a sintaxe da consulta com base em método.</span><span class="sxs-lookup"><span data-stu-id="dcb87-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the method-based query syntax.</span></span>  
  
 <span data-ttu-id="dcb87-104">O `FillDataSet` método usado nesses exemplos é especificado em [carregar dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="dcb87-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="dcb87-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="dcb87-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="dcb87-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="dcb87-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="dcb87-107">Para obter mais informações, consulte [como: criar um LINQ to DataSet de projeto no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="dcb87-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="dcb87-108">Selecionar</span><span class="sxs-lookup"><span data-stu-id="dcb87-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="dcb87-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dcb87-109">Example</span></span>  
 <span data-ttu-id="dcb87-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.Select%2A> para projetar `Name`, `ProductNumber`, e propriedades de `ListPrice` como uma sequência de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="dcb87-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to project the `Name`, `ProductNumber`, and `ListPrice` properties to a sequence of anonymous types.</span></span>  <span data-ttu-id="dcb87-111">A propriedade de `ListPrice` é renomeada também a `Price` no tipo resultante.</span><span class="sxs-lookup"><span data-stu-id="dcb87-111">The `ListPrice` property is also renamed to `Price` in the resulting type.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="dcb87-112">SelectMany</span><span class="sxs-lookup"><span data-stu-id="dcb87-112">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="dcb87-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dcb87-113">Example</span></span>  
 <span data-ttu-id="dcb87-114">Este exemplo usa o método de <xref:System.Linq.Enumerable.SelectMany%2A> para selecionar todos os pedidos onde `TotalDue` é menor que 500,00.</span><span class="sxs-lookup"><span data-stu-id="dcb87-114">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="dcb87-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dcb87-115">Example</span></span>  
 <span data-ttu-id="dcb87-116">Este exemplo usa o método de <xref:System.Linq.Enumerable.SelectMany%2A> para selecionar todos os pedidos na ordem foi feito o 1º de outubro de 2002 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="dcb87-116">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="dcb87-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcb87-117">See Also</span></span>  
 [<span data-ttu-id="dcb87-118">Carregar dados em um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="dcb87-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="dcb87-119">LINQ para exemplos de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="dcb87-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="dcb87-120">Visão Geral de Operadores de Consulta Padrão</span><span class="sxs-lookup"><span data-stu-id="dcb87-120">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)