---
title: "Implementando uma transação implícita, usando o escopo da transação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 49d1706a-1e0c-4c85-9704-75c908372eb9
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d33e055e9d73e786d822df2659bc490bc8646b9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-an-implicit-transaction-using-transaction-scope"></a>Implementando uma transação implícita, usando o escopo da transação
O <xref:System.Transactions.TransactionScope> classe fornece uma maneira simples para marcar um bloco de código como participar de uma transação, sem a necessidade de interagir com a própria transação. Selecione um escopo de transação e gerenciar a transação ambiente automaticamente. Devido à sua facilidade de uso e a eficiência, é recomendável que você use o <xref:System.Transactions.TransactionScope> classe ao desenvolver um aplicativo de transação.  
  
 Além disso, você não precisa conseguir recursos explicitamente com a transação. Qualquer <xref:System.Transactions> Gerenciador de recursos (como o SQL Server 2005) pode detectar a existência de uma transação ambiente criada pelo escopo e inscrever-se automaticamente.  
  
## <a name="creating-a-transaction-scope"></a>Criar um escopo de transação  
 O exemplo a seguir mostra um uso simple do <xref:System.Transactions.TransactionScope> classe.  
  
 [!code-csharp[TransactionScope#1](../../../../samples/snippets/csharp/VS_Snippets_Remoting/TransactionScope/cs/ScopeWithSQL.cs#1)]
 [!code-vb[TransactionScope#1](../../../../samples/snippets/visualbasic/VS_Snippets_Remoting/TransactionScope/vb/ScopeWithSQL.vb#1)]  
  
 O escopo da transação é iniciado quando você cria um novo <xref:System.Transactions.TransactionScope> objeto.  Conforme ilustrado no exemplo de código, é recomendável que você crie escopos com um **usando** instrução. O **usando** instrução está disponível em c# e no Visual Basic, e funciona como um **try... finally** bloco para garantir que o escopo é descartado corretamente.  
  
 Quando você cria uma instância <xref:System.Transactions.TransactionScope>, o Gerenciador de transações determina qual transação para participar. Uma vez determinado, o escopo sempre participa dessa transação. A decisão se baseia em dois fatores: se houver uma transação de ambiente e o valor da **TransactionScopeOption** parâmetro no construtor. A transação ambiente é a transação na qual o código é executado. Você pode obter uma referência para a transação de ambiente chamando estático <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> propriedade o <xref:System.Transactions.Transaction> classe. Para obter mais informações sobre como esse parâmetro é usado, consulte o [Gerenciando o fluxo de transações usando TransactionScopeOption](#ManageTxFlow) seção deste tópico.  
  
## <a name="completing-a-transaction-scope"></a>Concluindo um escopo de transação  
 Quando seu aplicativo conclui todo o trabalho que deseja executar em uma transação, você deve chamar o <xref:System.Transactions.TransactionScope.Complete%2A?displayProperty=nameWIthType> método apenas uma vez para informar o Gerenciador de transações que é aceitável para confirmar a transação. É muito bom colocar a chamada para <xref:System.Transactions.TransactionScope.Complete%2A> como a última instrução no **usando** bloco.  
  
 Falha ao chamar este método anula a transação, porque o Gerenciador de transações interpreta como uma falha do sistema, ou equivalente a uma exceção gerada dentro do escopo da transação. No entanto, chamar este método não garante que a transação será ser confirmada. É simplesmente uma maneira de informar o Gerenciador de transações do seu status. Depois de chamar o <xref:System.Transactions.TransactionScope.Complete%2A> método, você não pode acessar a transação de ambiente usando o <xref:System.Transactions.Transaction.Current%2A> propriedade e tentar fazer isso resultará em uma exceção é lançada.  
  
 Se o <xref:System.Transactions.TransactionScope> objeto criou a transação inicialmente, o trabalho real da confirmação da transação pelo Gerenciador de transações ocorre após a última linha do código no **usando** bloco. Se ele não criou a transação, a confirmação ocorre sempre que <xref:System.Transactions.CommittableTransaction.Commit%2A> é chamado pelo proprietário do <xref:System.Transactions.CommittableTransaction> objeto. Nesse ponto o Gerenciador de transações chama o recurso de gerentes e informa a confirmação ou reversão, com base em se o <xref:System.Transactions.TransactionScope.Complete%2A> método foi chamado no <xref:System.Transactions.TransactionScope> objeto.  
  
 O **usando** instrução garante que o <xref:System.Transactions.TransactionScope.Dispose%2A> método o <xref:System.Transactions.TransactionScope> objeto é chamado, mesmo que ocorra uma exceção. O <xref:System.Transactions.TransactionScope.Dispose%2A> método marca o final do escopo da transação. Exceções que ocorrem depois de chamar esse método não podem afetar a transação. Esse método também restaura a transação de ambiente para ele estado anterior.  
  
 Um <xref:System.Transactions.TransactionAbortedException> será lançada se o escopo cria a transação e a transação for anulada. Um <xref:System.Transactions.TransactionInDoubtException> será lançada se o Gerenciador de transações não pode chegar a uma decisão de confirmação. Nenhuma exceção é gerada se a transação for confirmada.  
  
## <a name="rolling-back-a-transaction"></a>Reverter uma transação  
 Se você quiser reverter uma transação, você não deve chamar o <xref:System.Transactions.TransactionScope.Complete%2A> método dentro do escopo da transação. Por exemplo, você pode lançar uma exceção dentro do escopo. A transação na qual participa também será revertida.  
  
##  <a name="ManageTxFlow"></a>Gerenciando o fluxo de transações usando TransactionScopeOption  
 Escopo da transação pode ser aninhado, chamando um método que usa um <xref:System.Transactions.TransactionScope> de dentro de um método que usa seu próprio escopo, como é o caso com o `RootMethod` método no exemplo a seguir,  
  
```csharp  
void RootMethod()  
{  
     using(TransactionScope scope = new TransactionScope())  
     {  
          /* Perform transactional work here */  
          SomeMethod();  
          scope.Complete();  
     }  
}  
  
void SomeMethod()  
{  
     using(TransactionScope scope = new TransactionScope())  
     {  
          /* Perform transactional work here */  
          scope.Complete();  
     }  
}  
```  
  
 O escopo da transação mais alto é conhecido como o escopo raiz.  
  
 O <xref:System.Transactions.TransactionScope> classe fornece vários construtores sobrecarregados que aceitam uma enumeração do tipo <xref:System.Transactions.TransactionScopeOption>, que define o comportamento transacional do escopo.  
  
 Um <xref:System.Transactions.TransactionScope> objeto tem três opções:  
  
-   Una a transação de ambiente ou criar um novo caso não exista.  
  
-   Ser um novo escopo de raiz, ou seja, iniciar uma nova transação e ter essa transação com a nova transação ambiente dentro de seu próprio escopo.  
  
-   Não fazer parte de uma transação, todo. Como resultado, há uma transação de ambiente.  
  
 Se o escopo é instanciado com <xref:System.Transactions.TransactionScopeOption.Required>e uma transação de ambiente estiver presente, o escopo une a transação. Se, por outro lado, não há nenhuma transação de ambiente, o escopo cria uma nova transação e se tornar o escopo raiz. Este é o valor padrão. Quando <xref:System.Transactions.TransactionScopeOption.Required> é usado, o código dentro do escopo não precisa ter um comportamento diferente seja a raiz ou apenas associando a transação de ambiente. Ele deve operar identicamente em ambos os casos.  
  
 Se o escopo é instanciado com <xref:System.Transactions.TransactionScopeOption.RequiresNew>, é sempre o escopo raiz. Ele inicia uma nova transação, e sua transação se torna a nova transação ambiente dentro do escopo.  
  
 Se o escopo é instanciado com <xref:System.Transactions.TransactionScopeOption.Suppress>, ele nunca faz parte de uma transação, independentemente de se uma transação de ambiente está presente. Um escopo instanciado com esse valor sempre ter **nulo** como sua transação de ambiente.  
  
 As opções acima são resumidas na tabela a seguir.  
  
|TransactionScopeOption|Transação de ambiente|O escopo faz parte do|  
|----------------------------|-------------------------|-----------------------------|  
|Obrigatório|Não|Nova transação (será a raiz)|  
|Requer novo|Não|Nova transação (será a raiz)|  
|Suprimir|Não|Nenhuma transação|  
|Obrigatório|Sim|Transação de ambiente|  
|Requer novo|Sim|Nova transação (será a raiz)|  
|Suprimir|Sim|Nenhuma transação|  
  
 Quando um <xref:System.Transactions.TransactionScope> objeto ingressa em uma transação ambiente existente, descarte o objeto de escopo não pode terminar a transação, a menos que o escopo anula a transação. Se a transação ambiente criada por um escopo de raiz, somente quando o escopo raiz é descartado, não <xref:System.Transactions.CommittableTransaction.Commit%2A> chamado na transação. Se a transação foi criada manualmente, a transação termina quando ele é anulado ou confirmado pelo seu criador.  
  
 A exemplo a seguir mostra um <xref:System.Transactions.TransactionScope> que cria três objetos de escopo aninhado, cada instanciados com outro objeto <xref:System.Transactions.TransactionScopeOption> valor.  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())   
//Default is Required   
{   
     using(TransactionScope scope2 = new   
      TransactionScope(TransactionScopeOption.Required))   
     {  
     ...  
     }   
  
     using(TransactionScope scope3 = new TransactionScope(TransactionScopeOption.RequiresNew))   
     {  
     ...  
     }   
  
     using(TransactionScope scope4 = new   
        TransactionScope(TransactionScopeOption.Suppress))   
    {  
     ...  
    }   
}  
```  
  
 O exemplo mostra um bloco de código sem qualquer transação ambiente criando um novo escopo (`scope1`) com <xref:System.Transactions.TransactionScopeOption.Required>. O escopo `scope1` é um escopo de raiz quando ele cria uma nova transação (uma transação) e faz com que a transação A transação de ambiente. `Scope1`em seguida, cria três mais objetos, cada um com outro <xref:System.Transactions.TransactionScopeOption> valor. Por exemplo, `scope2` é criado com <xref:System.Transactions.TransactionScopeOption.Required>, e como há uma transação de ambiente, ele adiciona a primeira transação criada pelo `scope1`. Observe que `scope3` é o escopo da raiz de uma nova transação e que `scope4` não tem nenhuma transação de ambiente.  
  
 Embora o padrão e mais comumente usado o valor de <xref:System.Transactions.TransactionScopeOption> é <xref:System.Transactions.TransactionScopeOption.Required>, cada um dos outros valores tem sua finalidade exclusiva.  
  
 <xref:System.Transactions.TransactionScopeOption.Suppress>é útil quando você quiser preservar as operações executadas pela seção de código e não desejar anular a transação ambiente se as operações de falham. Por exemplo, quando você deseja executar um log ou operações de auditoria ou quando desejar publicar eventos para assinantes, independentemente de se a transação de ambiente confirma ou anula. Esse valor permite que você tenha uma seção de código não-transacional dentro de um escopo de transação, como mostrado no exemplo a seguir.  
  
```csharp  
using(TransactionScope scope1 = new TransactionScope())  
{  
     try  
     {  
          //Start of non-transactional section   
          using(TransactionScope scope2 = new  
             TransactionScope(TransactionScopeOption.Suppress))  
          {  
               //Do non-transactional work here  
          }  
          //Restores ambient transaction here  
   }  
     catch  
     {}  
   //Rest of scope1  
}  
```  
  
### <a name="voting-inside-a-nested-scope"></a>Votação dentro de um escopo aninhado  
 Embora um escopo aninhado pode unir a transação de ambiente do escopo raiz, chamar <xref:System.Transactions.TransactionScope.Complete%2A> no escopo aninhado não tem nenhum efeito sobre o escopo raiz. Somente se todos os escopos do escopo raiz até o último escopo aninhado votam para confirmar a transação, a transação será confirmada. Não chamar <xref:System.Transactions.TransactionScope.Complete%2A> em um escopo aninhado afetará o escopo raiz como a transação ambiente imediatamente será anulada.  
  
## <a name="setting-the-transactionscope-timeout"></a>Definir o tempo limite de TransactionScope  
 Alguns dos construtores sobrecarregados de <xref:System.Transactions.TransactionScope> aceitar um valor do tipo <xref:System.TimeSpan>, que é usado para controlar o tempo limite da transação. Um tempo limite definido como zero significa um tempo limite infinito. Tempo limite infinito é útil principalmente para depuração, quando quiser isolar um problema em sua lógica de negócios, percorrendo seu código, e você não deseja que a transação que você depurar tempo limite durante a tentativa de localizar o problema. Ser extremamente cauteloso ao usar o valor de tempo limite infinito em todos os outros casos, porque ele substitui as proteções contra bloqueios de transação.  
  
 Você normalmente define o <xref:System.Transactions.TransactionScope> tempo limite para valores que não seja padrão nos dois casos. A primeira é durante o desenvolvimento, quando você deseja testar a maneira como o seu aplicativo manipula transações anuladas. Definindo o tempo limite como um valor pequeno (como um milissegundo), você fazer com que a transação falhar e, portanto, pode observar o código de tratamento de erros. O segundo caso em que você definir o valor como menor que o tempo limite padrão é quando você acreditar que o escopo está envolvido na contenção de recursos, resultando em bloqueios. Nesse caso, você deseja anular a transação assim que possível e aguarda o tempo limite padrão expirar.  
  
 Quando um escopo ingressa em uma transação de ambiente, mas Especifica um tempo limite menor do que a transação ambiente é definida como, o tempo limite de novo e mais curto é imposto no <xref:System.Transactions.TransactionScope> objeto e o escopo devem terminar no tempo aninhado especificado ou a transação é cancelada automaticamente. Se o tempo limite do escopo aninhado é maior do que a transação de ambiente, ele não tem efeito.  
  
## <a name="setting-the-transactionscope-isolation-level"></a>Definindo o nível de isolamento de TransactionScope  
 Alguns dos construtores sobrecarregados de <xref:System.Transactions.TransactionScope> aceitar uma estrutura do tipo <xref:System.Transactions.TransactionOptions> para especificar um nível de isolamento, além de um valor de tempo limite. Por padrão, a transação será executado com nível de isolamento definido como <xref:System.Transactions.IsolationLevel.Serializable>. Selecionando um nível de isolamento diferente de <xref:System.Transactions.IsolationLevel.Serializable> é normalmente usado para sistemas com uso intensivo de leitura. Isso requer uma compreensão sólida da teoria e a semântica da própria transação, os problemas de simultaneidade envolvidos e as conseqüências de consistência do sistema de processamento de transações.  
  
 Além disso, nem todos os gerenciadores de recursos oferecer suporte a todos os níveis de isolamento, e eles podem optar por fazer parte de transação em um nível mais alto que o configurado.  
  
 Cada nível de isolamento além <xref:System.Transactions.IsolationLevel.Serializable> é suscetível a inconsistência resultantes de outras transações que acessam as mesmas informações. É a diferença entre os diferentes níveis de isolamento da forma leitura e gravação bloqueios são usados. Um bloqueio pode ser mantido somente quando a transação acessa os dados no Gerenciador de recursos, ou pode ser mantida até que a transação é confirmada ou anulada. O primeiro é melhor taxa de transferência, o segundo para manter a consistência. Os dois tipos de bloqueios e os dois tipos de operações (leitura/gravação) oferecem quatro níveis de isolamento básico. Consulte <xref:System.Transactions.IsolationLevel> para obter mais informações.  
  
 Quando usando aninhadas <xref:System.Transactions.TransactionScope> objetos, todos os escopos aninhados devem ser configurados para usar exatamente o mesmo nível de isolamento se deseja unir a transação de ambiente. Se um aninhada <xref:System.Transactions.TransactionScope> objeto tentar unir a transação ambiente ainda Especifica um nível de isolamento diferente, um <xref:System.ArgumentException> é lançada.  
  
## <a name="interop-with-com"></a>Interoperação com COM+  
 Quando você cria um novo <xref:System.Transactions.TransactionScope> instância, você pode usar o <xref:System.Transactions.EnterpriseServicesInteropOption> enumeração em um dos construtores para especificar como interagir com COM+. Para obter mais informações sobre isso, consulte [interoperabilidade com serviços da empresa e transações COM+](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Transactions.Transaction.Clone%2A>  
 <xref:System.Transactions.TransactionScope>