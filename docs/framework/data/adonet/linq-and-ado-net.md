---
title: LINQ e o ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a8b196dd7eda673d1bd5f436f708471c81a857eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-and-adonet"></a><span data-ttu-id="6ae32-102">LINQ e o ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6ae32-102">LINQ and ADO.NET</span></span>
<span data-ttu-id="6ae32-103">Atualmente, muitos desenvolvedores de negócios devem usar duas (ou mais) linguagens de programação: uma linguagem de alto nível para as camadas de lógica de negócios e de apresentação (como o [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ou o [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]), e uma linguagem de consulta para interagir com o banco de dados (como [!INCLUDE[tsql](../../../../includes/tsql-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="6ae32-103">Today, many business developers must use two (or more) programming languages: a high-level language for the business logic and presentation layers (such as [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] or [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]), and a query language to interact with the database (such as [!INCLUDE[tsql](../../../../includes/tsql-md.md)]).</span></span> <span data-ttu-id="6ae32-104">Isso exige que o desenvolvedor seja proficiente em várias linguagens para ser eficaz e também provoca incompatibilidades de linguagens no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="6ae32-104">This requires the developer to be proficient in several languages to be effective, and also causes language mismatches in the development environment.</span></span> <span data-ttu-id="6ae32-105">Por exemplo, um aplicativo que usa uma API de acesso a dados para executar uma consulta em um banco de dados especifica a consulta como um literal de cadeia de caracteres usando aspas.</span><span class="sxs-lookup"><span data-stu-id="6ae32-105">For example, an application that uses a data access API to execute a query against a database specifies the query as a string literal by using quotation marks.</span></span> <span data-ttu-id="6ae32-106">Essa cadeia de caracteres de consulta é ilegível para o compilador e os erros não são verificados, como sintaxe inválida ou se as colunas ou linhas referenciadas realmente existem.</span><span class="sxs-lookup"><span data-stu-id="6ae32-106">This query string is un-readable to the compiler and is not checked for errors, such as invalid syntax or whether the columns or rows it references actually exist.</span></span> <span data-ttu-id="6ae32-107">Não há nenhuma verificação do tipo dos parâmetros da consulta e também nenhum suporte do `IntelliSense`.</span><span class="sxs-lookup"><span data-stu-id="6ae32-107">There is no type checking of the query parameters and no `IntelliSense` support, either.</span></span>  
  
 <span data-ttu-id="6ae32-108">O [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] permite que os desenvolvedores formem consultas baseadas em conjuntos no código de seus aplicativos, sem precisar usar uma linguagem de consulta separada.</span><span class="sxs-lookup"><span data-stu-id="6ae32-108">[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] enables developers to form set-based queries in their application code, without having to use a separate query language.</span></span> <span data-ttu-id="6ae32-109">Você pode escrever consultas de [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] com várias fontes de dados enumeráveis (ou seja, uma fonte de dados que implemente a interface <xref:System.Collections.IEnumerable>), como estruturas de dados na memória, documentos XML, bancos de dados SQL e objetos <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="6ae32-109">You can write [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries against various enumerable data sources (that is, a data source that implements the <xref:System.Collections.IEnumerable> interface), such as in-memory data structures, XML documents, SQL databases, and <xref:System.Data.DataSet> objects.</span></span> <span data-ttu-id="6ae32-110">Embora essas fontes de dados enumeráveis sejam implementadas de várias maneiras, todas elas expõem as mesmas sintaxe e constructos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="6ae32-110">Although these enumerable data sources are implemented in various ways, they all expose the same syntax and language constructs.</span></span> <span data-ttu-id="6ae32-111">Como as consultas podem ser formadas na própria linguagem de programação, você não precisa usar outra linguagem de consulta que seja inserida como literais de cadeia de caracteres que não podem ser compreendidos ou verificados pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="6ae32-111">Because queries can be formed in the programming language itself, you do not have to use another query language that is embedded as string literals that cannot be understood or verified by the compiler.</span></span> <span data-ttu-id="6ae32-112">A integração de consultas na linguagem de programação também permite que os programadores do [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] sejam mais produtivos fornecendo verificação de tempo de compilação e da sintaxe e o `IntelliSense`.</span><span class="sxs-lookup"><span data-stu-id="6ae32-112">Integrating queries into the programming language also enables [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] programmers to be more productive by providing compile-time type and syntax checking, and `IntelliSense`.</span></span> <span data-ttu-id="6ae32-113">Esses recursos reduzem a necessidade de depuração da consulta e de correção de erros.</span><span class="sxs-lookup"><span data-stu-id="6ae32-113">These features reduce the need for query debugging and error fixing.</span></span>  
  
 <span data-ttu-id="6ae32-114">A transferência de dados de tabelas SQL para objetos na memória é geralmente tediosa e sujeita a erros.</span><span class="sxs-lookup"><span data-stu-id="6ae32-114">Transferring data from SQL tables into objects in memory is often tedious and error-prone.</span></span> <span data-ttu-id="6ae32-115">O provedor do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] implementado pelo [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] e pelo [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] converte os dados de origem em coleções de objetos baseados em <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="6ae32-115">The [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] provider implemented by [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] and [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] converts the source data into <xref:System.Collections.IEnumerable>-based object collections.</span></span> <span data-ttu-id="6ae32-116">O programador sempre exibe os dados como uma coleção de <xref:System.Collections.IEnumerable>, quando você consulta e quando você atualiza.</span><span class="sxs-lookup"><span data-stu-id="6ae32-116">The programmer always views the data as an <xref:System.Collections.IEnumerable> collection, both when you query and when you update.</span></span> <span data-ttu-id="6ae32-117">Suporte completo do `IntelliSense` é fornecido para escrever consultas nessas coleções.</span><span class="sxs-lookup"><span data-stu-id="6ae32-117">Full `IntelliSense` support is provided for writing queries against those collections.</span></span>  
  
 <span data-ttu-id="6ae32-118">Há três tecnologias separadas do [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] do ADO.NET: [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] e [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ae32-118">There are three separate ADO.NET [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] technologies: [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], and [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].</span></span> <span data-ttu-id="6ae32-119">O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] fornece consulta mais sofisticada e otimizada sobre o <xref:System.Data.DataSet>, e o [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] permite que você consulte diretamente esquemas de banco de dados do [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], e o [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] permite que você consulte um [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ae32-119">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] provides richer, optimized querying over the <xref:System.Data.DataSet> and [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] enables you to directly query [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] database schemas, and [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] allows you to query an [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].</span></span>  
  
 <span data-ttu-id="6ae32-120">O diagrama a seguir fornece uma visão geral de como as tecnologias LINQ do ADO.NET estão relacionadas às linguagens de programação de alto nível e às fontes de dados habilitadas para LINQ.</span><span class="sxs-lookup"><span data-stu-id="6ae32-120">The following diagram provides an overview of how the ADO.NET LINQ technologies relate to high-level programming languages and LINQ-enabled data sources.</span></span>  
  
 <span data-ttu-id="6ae32-121">![LINQ para visão geral do ADO.NET](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="6ae32-121">![LINQ to ADO.NET overview](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")</span></span>  
  
 <span data-ttu-id="6ae32-122">Para obter informações gerais sobre os recursos de linguagem LINQ, consulte [Introdução ao LINQ](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e).</span><span class="sxs-lookup"><span data-stu-id="6ae32-122">For general information on the LINQ language features, see [Introduction to LINQ](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e).</span></span> <span data-ttu-id="6ae32-123">Para obter informações sobre como usar o LINQ em seus aplicativos, consulte o [não está em compilação: guia de programação geral de LINQ](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049), que contém informações detalhadas sobre como usar tecnologias LINQ.</span><span class="sxs-lookup"><span data-stu-id="6ae32-123">For information about using LINQ in your applications, see the [NOT IN BUILD: LINQ General Programming Guide](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049), which contains detailed information about how to use LINQ technologies.</span></span>  
  
 <span data-ttu-id="6ae32-124">As seções a seguir fornecem mais informações sobre o [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], o [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] e o [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ae32-124">The following sections provide more information about [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], and [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].</span></span>  
  
## <a name="linq-to-dataset"></a><span data-ttu-id="6ae32-125">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="6ae32-125">LINQ to DataSet</span></span>  
 <span data-ttu-id="6ae32-126">O <xref:System.Data.DataSet> é um elemento chave do modelo de programação desconectado no qual o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] é baseado e é amplamente utilizado.</span><span class="sxs-lookup"><span data-stu-id="6ae32-126">The <xref:System.Data.DataSet> is a key element of the disconnected programming model that [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] is built on, and is widely used.</span></span> <span data-ttu-id="6ae32-127">O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] permite que os desenvolvedores criem mais recursos sofisticados de consulta no <xref:System.Data.DataSet> usando o mesmo mecanismo de formulação de consulta que está disponível para muitas outras fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="6ae32-127">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] enables developers to build richer query capabilities into <xref:System.Data.DataSet> by using the same query formulation mechanism that is available for many other data sources.</span></span> <span data-ttu-id="6ae32-128">Para obter mais informações, consulte [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="6ae32-128">For more information, see [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).</span></span>  
  
## <a name="linq-to-sql"></a><span data-ttu-id="6ae32-129">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6ae32-129">LINQ to SQL</span></span>  
 <span data-ttu-id="6ae32-130">O [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] é uma ferramenta útil para os desenvolvedores que não requerem mapeamento para um modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="6ae32-130">[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] is a useful tool for developers who do not require mapping to a conceptual model.</span></span> <span data-ttu-id="6ae32-131">Usando o [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], você pode usar o modelo de programação do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] diretamente sobre o esquema do banco de dados existente.</span><span class="sxs-lookup"><span data-stu-id="6ae32-131">By using [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programming model directly over existing database schema.</span></span> <span data-ttu-id="6ae32-132">O [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] permite que os desenvolvedores gerem classes do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] que representam dados.</span><span class="sxs-lookup"><span data-stu-id="6ae32-132">[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] enables developers to generate [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes that represent data.</span></span> <span data-ttu-id="6ae32-133">Em vez do mapeamento para um modelo de dados conceitual, essas classes geradas mapeiam diretamente para tabelas do banco de dados, modos de exibição, procedimentos armazenados e funções definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="6ae32-133">Rather than mapping to a conceptual data model, these generated classes map directly to database tables, views, stored procedures, and user-defined functions.</span></span>  
  
 <span data-ttu-id="6ae32-134">Com o [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], os desenvolvedores podem escrever código diretamente no esquema de armazenamento usando o mesmo padrão de programação do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] como coleções na memória e o <xref:System.Data.DataSet>, além de outras fontes de dados, como XML.</span><span class="sxs-lookup"><span data-stu-id="6ae32-134">With [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], developers can write code directly against the storage schema using the same [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programming pattern as in-memory collections and the <xref:System.Data.DataSet>, in addition to other data sources such as XML.</span></span> <span data-ttu-id="6ae32-135">Para obter mais informações, consulte [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="6ae32-135">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
## <a name="linq-to-entities"></a><span data-ttu-id="6ae32-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="6ae32-136">LINQ to Entities</span></span>  
 <span data-ttu-id="6ae32-137">Atualmente, maioria dos aplicativos são escritos sobre bancos de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="6ae32-137">Most applications are currently written on top of relational databases.</span></span> <span data-ttu-id="6ae32-138">Em algum ponto, esses aplicativos precisarão interagir com os dados representados em um formulário relacional.</span><span class="sxs-lookup"><span data-stu-id="6ae32-138">At some point, these applications will need to interact with the data represented in a relational form.</span></span> <span data-ttu-id="6ae32-139">Os esquemas de banco de dados não são sempre ideais para criar aplicativos, e os modelos conceituais do aplicativo não são os mesmos que os modelos lógicos de bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="6ae32-139">Database schemas are not always ideal for building applications, and the conceptual models of application are not the same as the logical models of databases.</span></span> <span data-ttu-id="6ae32-140">O [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] é um modelo de dados conceitual, que pode ser usado para modelar os dados de um domínio específico de modo que os aplicativos possam interagir com dados como objetos.</span><span class="sxs-lookup"><span data-stu-id="6ae32-140">The [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] is a conceptual data model that can be used to model the data of a particular domain so that applications can interact with data as objects.</span></span> <span data-ttu-id="6ae32-141">Consulte [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6ae32-141">See [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) for more information.</span></span>  
  
 <span data-ttu-id="6ae32-142">Por meio do [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)], os dados relacionais são expostos como objetos no ambiente .NET.</span><span class="sxs-lookup"><span data-stu-id="6ae32-142">Through the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)], relational data is exposed as objects in the .NET environment.</span></span> <span data-ttu-id="6ae32-143">Isso torna a camada do objeto um destino ideal para o suporte do [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] permitindo que os desenvolvedores formulem consultas no banco de dados na linguagem usada para criar a lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="6ae32-143">This makes the object layer an ideal target for [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] support, allowing developers to formulate queries against the database from the language used to build the business logic.</span></span> <span data-ttu-id="6ae32-144">Esse recurso é conhecido como [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ae32-144">This capability is known as [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].</span></span> <span data-ttu-id="6ae32-145">Consulte [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6ae32-145">See [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ae32-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ae32-146">See Also</span></span>  
 [<span data-ttu-id="6ae32-147">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="6ae32-147">LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset.md)  
 [<span data-ttu-id="6ae32-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6ae32-148">LINQ to SQL</span></span>](../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="6ae32-149">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="6ae32-149">LINQ to Entities</span></span>](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [<span data-ttu-id="6ae32-150">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="6ae32-150">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 <span data-ttu-id="6ae32-151">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="6ae32-151">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>