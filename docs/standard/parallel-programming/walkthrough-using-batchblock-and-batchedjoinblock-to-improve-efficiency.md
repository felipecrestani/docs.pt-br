---
title: "Explicação passo a passo: Usando BatchBlock e BatchedJoinBlock para aumentar a eficiência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc74b4acc5b29395c05e7c8302caefeb51718282
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="ead56-102">Explicação passo a passo: Usando BatchBlock e BatchedJoinBlock para aumentar a eficiência</span><span class="sxs-lookup"><span data-stu-id="ead56-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="ead56-103">A biblioteca de fluxo de dados TPL fornece o <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> para que possa receber e buffer de dados de uma ou mais fontes e propagadas esses dados em buffer como uma coleção de classes.</span><span class="sxs-lookup"><span data-stu-id="ead56-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="ead56-104">Este mecanismo de envio em lote é útil quando você coleta dados de uma ou mais fontes e, em seguida, processar vários elementos de dados como um lote.</span><span class="sxs-lookup"><span data-stu-id="ead56-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="ead56-105">Por exemplo, considere um aplicativo que usa o fluxo de dados para inserir registros em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ead56-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="ead56-106">Essa operação pode ser mais eficiente se vários itens são inseridos sequencialmente ao mesmo tempo, em vez de um de cada vez.</span><span class="sxs-lookup"><span data-stu-id="ead56-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="ead56-107">Este documento descreve como usar o <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> operações de inserção de classe para melhorar a eficiência desse banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ead56-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="ead56-108">Ele também descreve como usar o <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> classe para capturar os resultados e todas as exceções que ocorrem quando o programa lê de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ead56-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="ead56-109">A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ead56-109">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="ead56-110">Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.</span><span class="sxs-lookup"><span data-stu-id="ead56-110">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ead56-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ead56-111">Prerequisites</span></span>  
  
1.  <span data-ttu-id="ead56-112">Ler a seção blocos ingressar o [fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) documento antes de começar este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="ead56-112">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="ead56-113">Certifique-se de que você tenha uma cópia do banco de dados Northwind, Northwind. sdf, disponível em seu computador.</span><span class="sxs-lookup"><span data-stu-id="ead56-113">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="ead56-114">Normalmente, esse arquivo está localizado na pasta % programa Files%\Microsoft SQL Server Compact Edition\v3.5\Samples.\\.</span><span class="sxs-lookup"><span data-stu-id="ead56-114">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ead56-115">Em algumas versões do Windows, você não pode se conectar a Northwind. sdf se [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] está em execução em um modo não administrador.</span><span class="sxs-lookup"><span data-stu-id="ead56-115">In some versions of Windows, you cannot connect to Northwind.sdf if [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] is running in a non-administrator mode.</span></span> <span data-ttu-id="ead56-116">Para se conectar a Northwind. sdf, iniciar [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou um [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] prompt de comando no **executar como administrador** modo.</span><span class="sxs-lookup"><span data-stu-id="ead56-116">To connect to Northwind.sdf, start [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] command prompt in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="ead56-117">Este passo a passo contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="ead56-117">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="ead56-118">Criando o aplicativo de Console</span><span class="sxs-lookup"><span data-stu-id="ead56-118">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="ead56-119">Definição da classe do funcionário</span><span class="sxs-lookup"><span data-stu-id="ead56-119">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="ead56-120">Definindo as operações de banco de dados de funcionário</span><span class="sxs-lookup"><span data-stu-id="ead56-120">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="ead56-121">Adicionando dados de funcionário no banco de dados sem o uso de buffer</span><span class="sxs-lookup"><span data-stu-id="ead56-121">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="ead56-122">Usando o armazenamento em buffer para adicionar dados de funcionário no banco de dados</span><span class="sxs-lookup"><span data-stu-id="ead56-122">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="ead56-123">Usando a associação em buffer para ler dados de funcionário do banco de dados</span><span class="sxs-lookup"><span data-stu-id="ead56-123">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="ead56-124">O exemplo completo</span><span class="sxs-lookup"><span data-stu-id="ead56-124">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="ead56-125">Criando o Aplicativo de Console</span><span class="sxs-lookup"><span data-stu-id="ead56-125">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="ead56-126">Em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], criar um Visual c# ou Visual Basic **aplicativo de Console** projeto.</span><span class="sxs-lookup"><span data-stu-id="ead56-126">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="ead56-127">Neste documento, o projeto é denominado `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="ead56-127">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="ead56-128">No seu projeto, adicione uma referência ao SqlServerCe e uma referência a System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="ead56-128">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="ead56-129">Certifique-se de que Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contém o seguinte `using` (`Imports` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) instruções.</span><span class="sxs-lookup"><span data-stu-id="ead56-129">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="ead56-130">Adicionar os seguintes membros de dados para o `Program` classe.</span><span class="sxs-lookup"><span data-stu-id="ead56-130">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="ead56-131">Definição da classe do funcionário</span><span class="sxs-lookup"><span data-stu-id="ead56-131">Defining the Employee Class</span></span>  
 <span data-ttu-id="ead56-132">Adicionar ao `Program` classe o `Employee` classe.</span><span class="sxs-lookup"><span data-stu-id="ead56-132">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="ead56-133">O `Employee` classe contém três propriedades, `EmployeeID`, `LastName`, e `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="ead56-133">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="ead56-134">Essas propriedades correspondem ao `Employee ID`, `Last Name`, e `First Name` colunas o `Employees` tabela no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="ead56-134">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="ead56-135">Para esta demonstração, o `Employee` classe também define o `Random` método, que cria um `Employee` objeto que tem valores aleatórios para suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="ead56-135">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="ead56-136">Definindo as operações de banco de dados de funcionário</span><span class="sxs-lookup"><span data-stu-id="ead56-136">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="ead56-137">Adicionar ao `Program` classe o `InsertEmployees`, `GetEmployeeCount`, e `GetEmployeeID` métodos.</span><span class="sxs-lookup"><span data-stu-id="ead56-137">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="ead56-138">O `InsertEmployees` método adiciona novos registros de funcionário no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ead56-138">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="ead56-139">O `GetEmployeeCount` método recupera o número de entradas na `Employees` tabela.</span><span class="sxs-lookup"><span data-stu-id="ead56-139">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="ead56-140">O `GetEmployeeID` método recupera o identificador do primeiro funcionário que tem o nome fornecido.</span><span class="sxs-lookup"><span data-stu-id="ead56-140">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="ead56-141">Cada um desses métodos usa uma cadeia de caracteres de conexão para o banco de dados Northwind e usa a funcionalidade de `System.Data.SqlServerCe` namespace para se comunicar com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ead56-141">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="ead56-142">Adicionando dados de funcionário no banco de dados sem o uso de buffer</span><span class="sxs-lookup"><span data-stu-id="ead56-142">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="ead56-143">Adicionar ao `Program` classe o `AddEmployees` e `PostRandomEmployees` métodos.</span><span class="sxs-lookup"><span data-stu-id="ead56-143">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="ead56-144">O `AddEmployees` método adiciona dados de funcionário aleatória para o banco de dados usando o fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="ead56-144">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="ead56-145">Ele cria um <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto que chama o `InsertEmployees` método para adicionar uma entrada de funcionário no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ead56-145">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="ead56-146">O `AddEmployees` , em seguida, chama um método de `PostRandomEmployees` método para postar vários `Employee` objetos para o <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto.</span><span class="sxs-lookup"><span data-stu-id="ead56-146">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="ead56-147">O `AddEmployees` método espera para todas as operações para terminar de inserção.</span><span class="sxs-lookup"><span data-stu-id="ead56-147">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="ead56-148">Usando o armazenamento em buffer para adicionar dados de funcionário no banco de dados</span><span class="sxs-lookup"><span data-stu-id="ead56-148">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="ead56-149">Adicionar ao `Program` classe o `AddEmployeesBatched` método.</span><span class="sxs-lookup"><span data-stu-id="ead56-149">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="ead56-150">Esse método é semelhante `AddEmployees`, exceto que ele também usa o <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> classe para armazenar em buffer vários `Employee` objetos antes de enviar esses objetos para o <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto.</span><span class="sxs-lookup"><span data-stu-id="ead56-150">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="ead56-151">Porque o <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> classe propaga vários elementos em uma coleção, o <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto é modificado para funcionar em uma matriz de `Employee` objetos.</span><span class="sxs-lookup"><span data-stu-id="ead56-151">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="ead56-152">Como no `AddEmployees` método, `AddEmployeesBatched` chamadas a `PostRandomEmployees` método para postar vários `Employee` objetos; no entanto, `AddEmployeesBatched` envia esses objetos para o <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objeto.</span><span class="sxs-lookup"><span data-stu-id="ead56-152">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="ead56-153">O `AddEmployeesBatched` método também aguarda para todas as operações para terminar de inserção.</span><span class="sxs-lookup"><span data-stu-id="ead56-153">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="ead56-154">Usando a associação em buffer para ler dados de funcionário do banco de dados</span><span class="sxs-lookup"><span data-stu-id="ead56-154">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="ead56-155">Adicionar ao `Program` classe o `GetRandomEmployees` método.</span><span class="sxs-lookup"><span data-stu-id="ead56-155">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="ead56-156">Esse método imprime as informações sobre funcionários aleatórios para o console.</span><span class="sxs-lookup"><span data-stu-id="ead56-156">This method prints information about random employees to the console.</span></span> <span data-ttu-id="ead56-157">Ele cria vários aleatório `Employee` objetos e chama o `GetEmployeeID` método para recuperar o identificador exclusivo para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="ead56-157">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="ead56-158">Porque o `GetEmployeeID` método lançará uma exceção se não houver nenhum funcionário correspondência com nomes e sobrenomes determinados, o `GetRandomEmployees` método usa o <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> classe para armazenar `Employee` objetos para chamada bem-sucedida a `GetEmployeeID` e <xref:System.Exception?displayProperty=nameWithType> objetos para chamadas com falha.</span><span class="sxs-lookup"><span data-stu-id="ead56-158">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="ead56-159">O <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto neste exemplo age em uma <xref:System.Tuple%602> objeto que contém uma lista de `Employee` objetos e uma lista de <xref:System.Exception> objetos.</span><span class="sxs-lookup"><span data-stu-id="ead56-159">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="ead56-160">O <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objeto propaga esse dados quando a soma de recebido `Employee` e <xref:System.Exception> contagens de objeto é igual ao tamanho de lote.</span><span class="sxs-lookup"><span data-stu-id="ead56-160">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="ead56-161">O Exemplo Completo</span><span class="sxs-lookup"><span data-stu-id="ead56-161">The Complete Example</span></span>  
 <span data-ttu-id="ead56-162">O exemplo a seguir mostra o código completo.</span><span class="sxs-lookup"><span data-stu-id="ead56-162">The following example shows the complete code.</span></span> <span data-ttu-id="ead56-163">O `Main` método compara a hora em que é necessário para executar inserções em lotes do banco de dados em comparação com o tempo para executar as inserções do banco de dados sem lote.</span><span class="sxs-lookup"><span data-stu-id="ead56-163">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="ead56-164">Ele também demonstra o uso de junção em buffer para ler dados de funcionário do banco de dados e também informar erros.</span><span class="sxs-lookup"><span data-stu-id="ead56-164">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="ead56-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ead56-165">See Also</span></span>  
 [<span data-ttu-id="ead56-166">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="ead56-166">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)