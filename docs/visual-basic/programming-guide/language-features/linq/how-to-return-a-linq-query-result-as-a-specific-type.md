---
title: Como retornar um resultado de consulta LINQ como um tipo específico (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: e0b7e402fba4fb51afb60ad0ae7698bd4947b2f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Como retornar um resultado de consulta LINQ como um tipo específico (Visual Basic)
Consulta integrada à linguagem (LINQ) facilita o acesso a informações de banco de dados e executar consultas. Por padrão, consultas LINQ retornam uma lista de objetos como um tipo anônimo. Você também pode especificar que uma consulta retorne uma lista de um tipo específico usando o `Select` cláusula.  
  
 O exemplo a seguir mostra como criar um novo aplicativo que executa consultas em um banco de dados do SQL Server e projeta os resultados como um tipo específico. Para obter mais informações, consulte [tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) e [cláusula Select](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
 Os exemplos neste tópico usam o banco de dados de exemplo Northwind. Se você não tiver o banco de dados de exemplo Northwind no computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site da Web. Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Para criar uma conexão para um banco de dados  
  
1.  No Visual Studio, abra **Server Explorer**/**Pesquisador de objetos de banco de dados** clicando **Server Explorer**/**banco de dados Gerenciador de** no **exibição** menu.  
  
2.  Clique com botão direito **conexões de dados** na **Server Explorer**/**Pesquisador de objetos de banco de dados** e, em seguida, clique em **Adicionar Conexão**.  
  
3.  Especifique uma conexão válida para o banco de dados de exemplo Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Para adicionar um projeto que contém um arquivo LINQ to SQL  
  
1.  No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**. Selecione Visual Basic **aplicativo do Windows Forms** como o tipo de projeto.  
  
2.  No menu **Projeto**, clique em **Adicionar Novo Item**. Selecione o **Classes LINQ to SQL** modelo de item.  
  
3.  Dê o nome `northwind.dbml` para o arquivo. Clique em **Adicionar**. O Object Relational Designer (O/R Designer) é aberto para o arquivo dbml.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Para adicionar tabelas de consulta para o O/R Designer  
  
1.  Em **Server Explorer**/**Pesquisador de objetos de banco de dados**, expanda a conexão ao banco de dados Northwind. Expanda o **tabelas** pasta.  
  
     Se você fechou o Object Relational Designer, você poderá reabri-lo clicando no arquivo dbml que você adicionou anteriormente.  
  
2.  Clique na tabela clientes e arraste-o no painel esquerdo do designer.  
  
     O designer cria um novo `Customer` objeto para o seu projeto. Você pode projetar um resultado de consulta como o `Customer` tipo ou como um tipo que você criar. Este exemplo criará um novo tipo em um procedimento posterior e um resultado de consulta como esse tipo de projeto.  
  
3.  Salve suas alterações e fechar o designer.  
  
4.  Salve seu projeto.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Para adicionar código para consultar o banco de dados e exibir os resultados  
  
1.  Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.DataGridView> controle para o Windows Form padrão para seu projeto, Form1.  
  
2.  Clique duas vezes em Form1 para modificar a classe Form1.  
  
3.  Após o `End Class` declaração da classe Form1, adicione o seguinte código para criar um `CustomerInfo` para conter os resultados da consulta para esse exemplo.  
  
     [!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]  
  
4.  Quando você adicionar tabelas ao / R Designer, o designer adicionará um <xref:System.Data.Linq.DataContext> objeto ao seu projeto. Este objeto contém o código que você deve ter para acessar essas tabelas e para acessar objetos individuais e coleções para cada tabela. O <xref:System.Data.Linq.DataContext> objeto para seu projeto é nomeado com base no nome do seu arquivo dbml. Para este projeto, o <xref:System.Data.Linq.DataContext> objeto é nomeado `northwindDataContext`.  
  
     Você pode criar uma instância do <xref:System.Data.Linq.DataContext> no seu código e consultar as tabelas especificadas pelo / R Designer.  
  
     No `Load` evento da classe Form1, adicione o seguinte código para consultar as tabelas que são expostas como propriedades de seu contexto de dados. O `Select` cláusula de consulta criará uma nova `CustomerInfo` tipo em vez de um tipo anônimo para cada item do resultado da consulta.  
  
     [!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]  
  
5.  Pressione F5 para executar seu projeto e exibir os resultados.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Métodos de DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
