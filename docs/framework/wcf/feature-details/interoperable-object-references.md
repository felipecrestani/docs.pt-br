---
title: Referências de objeto de interoperabilidade
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: eeedd39ec14a6758395aee1f4c3b8ab26a0c2ffd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="interoperable-object-references"></a>Referências de objeto de interoperabilidade
Por padrão o <xref:System.Runtime.Serialization.DataContractSerializer> serializa objetos por valor. Você pode usar o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> propriedade para instruir o serializador de contrato de dados para preservar as referências de objeto ao serializar objetos do tipo.  
  
## <a name="generated-xml"></a>XML gerado  
 Por exemplo, considere o seguinte objeto:  
  
```  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass   
{  
}  
```  
  
 Com <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido como `false` (o padrão), o XML a seguir é gerado:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 Com <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definida como `true`, o XML a seguir é gerado:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 No entanto, <xref:System.Runtime.Serialization.XsdDataContractExporter> não descreve o `id` e `ref` atributos em seu esquema, mesmo quando o `preserveObjectReferences` está definida como `true`.  
  
## <a name="using-isreference"></a>Usando IsReference  
 Para gerar informações de referência de objeto é válidas de acordo com o esquema que descreve a ele, aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> para um tipo de atributo e definir o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> sinalizador como `true`. Usando `IsReference` na classe do exemplo anterior `X`:  
  
 `[DataContract(IsReference=true)] public class X`  
  
 `{`  
  
 `SomeClass someInstance = new SomeClass();`  
  
 `[DataMember]`  
  
 `public SomeClass A = someInstance;`  
  
 `[DataMember]`  
  
 `public SomeClass B = someInstance;`  
  
 `}`  
  
 `public class SomeClass`  
  
 `{`  
  
 `}`  
  
 O XML gerado é o seguinte:  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 Usando `IsReference` garante conformidade no ciclo de mensagem. Sem ele, quando um tipo é gerado do esquema, o que é enviado de volta como XML para que o tipo não é necessariamente compatível com o esquema originalmente assumido. Em outras palavras, embora o `id` e `ref` atributos foram serializados, o esquema original pode ter bloqueadas esses atributos (ou todos os atributos) ocorra no XML. Com `IsReference` aplicado a um membro de dados, o membro continua a ser reconhecido como "pode ser referenciado" quando roundtripped.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
