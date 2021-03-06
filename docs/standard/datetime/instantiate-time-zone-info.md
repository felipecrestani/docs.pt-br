---
title: 'Como: instanciar um objeto TimeZoneInfo'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e15e7f8968d7edf87ae3cd709d8fb26a2f49826a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Como: instanciar um objeto TimeZoneInfo

A maneira mais comum para instanciar um <xref:System.TimeZoneInfo> objeto é para recuperar informações sobre ele no registro. Este tópico aborda como instanciar um <xref:System.TimeZoneInfo> objeto do registro do sistema local.

### <a name="to-instantiate-a-timezoneinfo-object"></a>Para instanciar um objeto TimeZoneInfo

1. Declarar uma <xref:System.TimeZoneInfo> objeto.

2. Chamar o `static` (`Shared` no Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> método.

3. Manipule as exceções geradas pelo método, particularmente o <xref:System.TimeZoneNotFoundException> que é gerada se o fuso horário não está definido no registro.

## <a name="example"></a>Exemplo

O código a seguir recupera um <xref:System.TimeZoneInfo> objeto que representa o fuso horário padrão do Leste e exibe a hora padrão que corresponde à hora local.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

O <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> único parâmetro do método é o identificador do fuso horário que você deseja recuperar, que corresponde ao objeto de <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> propriedade. O identificador do fuso horário é um campo de chave que identifica exclusivamente o fuso horário. Enquanto a maioria das chaves são relativamente curtas, o identificador de fuso horário é comparativamente longo. Na maioria dos casos, seu valor corresponde do <xref:System.TimeZoneInfo.StandardName%2A> propriedade de um <xref:System.TimeZoneInfo> objeto, que é usado para fornecer o nome do padrão de tempo do fuso horário. No entanto, há exceções. A melhor maneira de certificar-se de que você forneça um identificador válido é enumerar os fusos horários disponíveis no sistema e observar os identificadores dos fusos horários presentes nele. Para obter uma ilustração, consulte [como: enumerar os fusos horários presentes em um computador](../../../docs/standard/datetime/enumerate-time-zones.md). O tópico [Encontrando os fusos horários definidos em um sistema local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) também contém uma lista de identificadores de fuso horário selecionados.

Se o fuso horário for encontrado, o método retorna seu <xref:System.TimeZoneInfo> objeto. Se o fuso horário não for encontrado, o método gera uma <xref:System.TimeZoneNotFoundException>. Se o fuso horário for encontrado, mas seus dados estão corrompidos ou incompletos, o método gera uma <xref:System.InvalidTimeZoneException>.

Se seu aplicativo depende de um fuso horário que deve estar presente, primeiro você deve chamar o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método para recuperar as informações de fuso horário do registro. Se a chamada de método falhar, o manipulador de exceção deve, em seguida, criar uma nova instância da zona de tempo ou recriá-la desserializando um serializado <xref:System.TimeZoneInfo> objeto. Consulte [como: restaurar fusos horários de um recurso incorporado](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) para obter um exemplo.

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
[encontrando os fusos horários definidos em um sistema local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[como: acessar os objetos de zona predefinidos UTC e a hora local](../../../docs/standard/datetime/access-utc-and-local.md)
