---
title: "Transformações XSLT sobre diferentes armazena"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2b642a1f2c29c6b4143b3f520a3df47328fcb41d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-transformations-over-different-stores"></a>Transformações XSLT sobre diferentes armazena
> [!NOTE]
>  A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>. Confira [Usar a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [Migrar da classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para saber mais.  
  
 O ADO.NET e as classes XML em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fornecem um modelo de programação unificado de acesso a dados. Os dados são representados como os dados XML, que são texto delimitado por marcas, e os dados relacionais, que são tabelas que consiste em linhas e em colunas. XML em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ler dados XML do fluxo de dados em árvores do nó de (DOM) o modelo de objeto de documento, onde os dados podem ser acessados por meio de programação, quando o ADO.NET fornecer os meios para acessar e manipular os dados relacionais dentro de <xref:System.Data.DataSet> objeto.  
  
 Os DOM XML fornecem acesso a dados em documentos XML e classes adicionais para ler, gravar, e navega em documentos XML. Essas classes são suportadas no espaço de <xref:System.Xml> , que também unifica os DOM XML com os serviços de acesso a dados fornecidos pelo ADO.NET. <xref:System.Xml.XmlDataDocument> fornece acesso a dados relacional. <xref:System.Xml.XmlDataDocument> mapeia XML para dados relacionais no ADO.NET <xref:System.Data.DataSet>. Qualquer aplicativo baseado em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]pode usar as classes no namespace de <xref:System.Xml> para acessar e manipular documentos XML e dados relacionais em <xref:System.Xml.XmlDataDocument>. Essa implementação suporta arquiteturas n- múltiplas para coletando dados e de distribuição. Para saber mais, confira [Integração XML com dados relacionais e ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Consulte também  
 [A classe XslTransform implementa o processador XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
