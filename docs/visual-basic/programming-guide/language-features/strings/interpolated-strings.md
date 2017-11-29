---
title: Cadeias de caracteres interpoladas (Visual Basic)
ms.date: 10/31/2017
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f865d5a7167847bf869d70a39570413dac271a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="e3073-102">Cadeias de caracteres interpoladas (referência do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3073-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="e3073-103">Usado para construir cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e3073-103">Used to construct strings.</span></span>  <span data-ttu-id="e3073-104">Uma cadeia de caracteres interpolada é semelhante a uma cadeia de caracteres de modelo que contém *expressões interpoladas*.</span><span class="sxs-lookup"><span data-stu-id="e3073-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="e3073-105">Uma cadeia de caracteres interpolada retorna uma cadeia de caracteres que substitui as expressões interpoladas que ela contém por suas representações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e3073-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="e3073-106">Este recurso está disponível no Visual Basic 14 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="e3073-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="e3073-107">Os argumentos de uma cadeia de caracteres interpolada são mais fáceis de entender do que uma [cadeia de caracteres de formato composto](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="e3073-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="e3073-108">Por exemplo, a cadeia de caracteres interpolada</span><span class="sxs-lookup"><span data-stu-id="e3073-108">For example, the interpolated string</span></span>  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
<span data-ttu-id="e3073-109">contém duas expressões interpoladas, "{name}" e "{hours:hh}".</span><span class="sxs-lookup"><span data-stu-id="e3073-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="e3073-110">A cadeia de caracteres de formato composto equivalente é:</span><span class="sxs-lookup"><span data-stu-id="e3073-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="e3073-111">A estrutura de uma cadeia de caracteres interpolada é:</span><span class="sxs-lookup"><span data-stu-id="e3073-111">The structure of an interpolated string is:</span></span>  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="e3073-112">em que:</span><span class="sxs-lookup"><span data-stu-id="e3073-112">where:</span></span> 

- <span data-ttu-id="e3073-113">*field-width* é um inteiro com sinal que indica o número de caracteres no campo.</span><span class="sxs-lookup"><span data-stu-id="e3073-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="e3073-114">Se ele for positivo, o campo será alinhado à direita. Se for negativo, será alinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="e3073-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="e3073-115">*format-string* é uma cadeia de caracteres de formato apropriada para o tipo do objeto que está sendo formatado.</span><span class="sxs-lookup"><span data-stu-id="e3073-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="e3073-116">Por exemplo, para um <xref:System.DateTime> valor, ele pode ser um [cadeia de caracteres de formato de data e hora padrão](~/docs/standard/base-types/standard-date-and-time-format-strings.md) como "D" ou "d".</span><span class="sxs-lookup"><span data-stu-id="e3073-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](~/docs/standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3073-117">Você não pode ter qualquer espaço em branco entre a `$` e `"` que inicia a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e3073-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="e3073-118">Isso faz com que um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="e3073-118">Doing so causes a compiler error.</span></span>

 <span data-ttu-id="e3073-119">Você pode usar uma cadeia de caracteres interpolada em qualquer lugar em que pode usar um literal de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e3073-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="e3073-120">A cadeia de caracteres interpolada é avaliada sempre que o código com a cadeia de caracteres interpolada for executado.</span><span class="sxs-lookup"><span data-stu-id="e3073-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="e3073-121">Isso permite que você separe a definição e a avaliação de uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="e3073-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="e3073-122">Para incluir uma chave ("{" ou "}") em uma cadeia de caracteres interpolada, use duas chaves, "{{" ou "}}".</span><span class="sxs-lookup"><span data-stu-id="e3073-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="e3073-123">Consulte a seção sobre Conversões implícitas para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="e3073-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="e3073-124">Se a cadeia de caracteres interpolada contiver outros caracteres com significado especial em uma cadeia de caracteres interpolada, como aspas ("), dois-pontos (:) ou vírgulas (,), eles devem ser substituídos se ocorrerem no texto literal ou devem ser incluídos em uma expressão delimitada por parênteses se forem elementos de linguagem incluídos em uma expressão interpolada.</span><span class="sxs-lookup"><span data-stu-id="e3073-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="e3073-125">O exemplo a seguir ignora as aspas para incluí-las na cadeia de caracteres de resultado e usa parênteses para delimitar a expressão `(age == 1 ? "" : "s")`, de modo que os dois-pontos não sejam interpretados como o início de uma cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="e3073-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a><span data-ttu-id="e3073-126">Conversões implícitas</span><span class="sxs-lookup"><span data-stu-id="e3073-126">Implicit Conversions</span></span>  

<span data-ttu-id="e3073-127">Há três conversões de tipo implícitas de uma cadeia de caracteres interpolada:</span><span class="sxs-lookup"><span data-stu-id="e3073-127">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="e3073-128">Conversão de uma cadeia de caracteres interpolada em um <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e3073-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="e3073-129">O exemplo a seguir retorna uma cadeia de caracteres cujas expressões de cadeia de caracteres interpolada foram substituídas por suas representações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e3073-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="e3073-130">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e3073-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   <span data-ttu-id="e3073-131">Esse é o resultado final de uma interpretação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e3073-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="e3073-132">Todas as ocorrências de chaves duplas ("{{" e "}}") serão convertidas em uma chave única.</span><span class="sxs-lookup"><span data-stu-id="e3073-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="e3073-133">Conversão de uma cadeia de caracteres interpolada em uma variável <xref:System.IFormattable> que permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura de uma única instância <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="e3073-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="e3073-134">Isso é útil para incluir itens como os formatos de número e data corretos para culturas individuais.</span><span class="sxs-lookup"><span data-stu-id="e3073-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="e3073-135">Todas as ocorrências de chaves duplas ("{{" e "}}") permanecem como chaves duplas até que você formate a cadeia de caracteres explícita ou implicitamente chamando o método <xref:System.Object.ToString>.</span><span class="sxs-lookup"><span data-stu-id="e3073-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="e3073-136">Todas as expressões de interpolação contidas são convertidas em {0}, {1} e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="e3073-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="e3073-137">O exemplo a seguir usa reflexão para exibir os membros, bem como os valores de campo e propriedade de uma variável <xref:System.IFormattable> criada de uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="e3073-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="e3073-138">Ele também passa o <xref:System.IFormattable> variável para o <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="e3073-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   <span data-ttu-id="e3073-139">Observe que a cadeia de caracteres interpolada pode ser inspecionada somente usando a reflexão.</span><span class="sxs-lookup"><span data-stu-id="e3073-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="e3073-140">Se ele é passado para uma cadeia de caracteres de formatação, como o método, <xref:System.Console.WriteLine(System.String)>, seus itens de formato são resolvidos e a cadeia de caracteres de resultado retornado.</span><span class="sxs-lookup"><span data-stu-id="e3073-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="e3073-141">Conversão de uma cadeia de caracteres interpolada um <xref:System.FormattableString> variável que representa uma cadeia de caracteres de formato composto.</span><span class="sxs-lookup"><span data-stu-id="e3073-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="e3073-142">Inspecionar a cadeia de caracteres de formato composto e como ela é renderizada como uma cadeia de caracteres de resultado pode, por exemplo, ajudar a proteger contra um ataque de injeção se você estiver criando uma consulta.</span><span class="sxs-lookup"><span data-stu-id="e3073-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="e3073-143">Um <xref:System.FormattableString> também inclui:</span><span class="sxs-lookup"><span data-stu-id="e3073-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="e3073-144">Um <xref:System.FormattableString.ToString> sobrecarga que produz uma cadeia de caracteres de resultado para o <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="e3073-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      
      - <span data-ttu-id="e3073-145">Um <xref:System.FormattableString.Invariant%2A> método que produz uma cadeia de caracteres para o <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="e3073-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      
      - <span data-ttu-id="e3073-146">Um <xref:System.FormattableString.ToString(System.IFormatProvider)> método que produz uma cadeia de caracteres de resultado para uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="e3073-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span> 
  
    <span data-ttu-id="e3073-147">Todas as ocorrências de chaves duplas ("{{" e "}}") permanecem como chaves duplas até você formatar.</span><span class="sxs-lookup"><span data-stu-id="e3073-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="e3073-148">Todas as expressões de interpolação contidas são convertidas em {0}, {1} e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="e3073-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a><span data-ttu-id="e3073-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3073-149">See Also</span></span>  
<span data-ttu-id="e3073-150">f<xref:System.IFormattable?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e3073-150">f <xref:System.IFormattable?displayProperty=nameWithType></span></span>   
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="e3073-151">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3073-151">Visual Basic Language Reference</span></span>](index.md)  
 