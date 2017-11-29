---
title: Como exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b92fec7565aad2a881f714f9232eae10bf7633c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="a1c91-102">Como exibir uma data em um formato personalizado com o controle DateTimePicker dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a1c91-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="a1c91-103">Windows Forms <xref:System.Windows.Forms.DateTimePicker> controle oferece flexibilidade na formatação de exibição de datas e horas no controle.</span><span class="sxs-lookup"><span data-stu-id="a1c91-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="a1c91-104">O <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriedade permite que você selecione um dos formatos predefinidos, listados no <xref:System.Windows.Forms.DateTimePickerFormat>.</span><span class="sxs-lookup"><span data-stu-id="a1c91-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="a1c91-105">Se nenhum desses for adequada para suas finalidades, você pode criar seu próprio estilo de formato usando caracteres de formato listados na <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1c91-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="a1c91-106">Para exibir um formato personalizado</span><span class="sxs-lookup"><span data-stu-id="a1c91-106">To display a custom format</span></span>  
  
1.  <span data-ttu-id="a1c91-107">Defina a propriedade <xref:System.Windows.Forms.DateTimePicker.Format%2A> como `DateTimePickerFormat.Custom`.</span><span class="sxs-lookup"><span data-stu-id="a1c91-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2.  <span data-ttu-id="a1c91-108">Definir o <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> propriedade como uma cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="a1c91-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="a1c91-109">Para adicionar texto ao valor formatado</span><span class="sxs-lookup"><span data-stu-id="a1c91-109">To add text to the formatted value</span></span>  
  
1.  <span data-ttu-id="a1c91-110">Use aspas simples para incluir qualquer caractere que não seja um caractere de formato como "M" ou um delimitador como ":".</span><span class="sxs-lookup"><span data-stu-id="a1c91-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="a1c91-111">Por exemplo, a cadeia de formato a seguir exibe a data atual com o formato "hoje é: 05:30:31 sexta-feira 02 de março de 2012" em inglês (Estados Unidos).</span><span class="sxs-lookup"><span data-stu-id="a1c91-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     <span data-ttu-id="a1c91-112">Dependendo da configuração de cultura, todos os caracteres que não estiverem entre aspas simples poderão ser alterados.</span><span class="sxs-lookup"><span data-stu-id="a1c91-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="a1c91-113">Por exemplo, a cadeia de formato acima exibe a data atual com o formato "hoje é: 05:30:31 sexta-feira 02 de março de 2012" em inglês (Estados Unidos).</span><span class="sxs-lookup"><span data-stu-id="a1c91-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="a1c91-114">Observe que a primeira vírgula é colocada entre aspas simples, porque não se pretende que ela seja um caractere delimitador como em "hh:mm:ss".</span><span class="sxs-lookup"><span data-stu-id="a1c91-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="a1c91-115">Em outra cultura, o formato pode ser exibido como "hoje é: 05.30.31 sexta-feira, 02 de março de 2012".</span><span class="sxs-lookup"><span data-stu-id="a1c91-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c91-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1c91-116">See Also</span></span>  
 [<span data-ttu-id="a1c91-117">Controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="a1c91-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="a1c91-118">Como definir e retornar datas com o controle DateTimePicker dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a1c91-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)