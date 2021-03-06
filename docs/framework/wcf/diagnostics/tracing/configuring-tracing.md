---
title: Configurando o rastreamento
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: f9603f79992c31ad1af3b6c672b448ab031ba78d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-tracing"></a>Configurando o rastreamento
Este tópico descreve como você pode habilitar o rastreamento, configurar fontes de rastreamento para emitir rastreamentos e definir níveis de rastreamento, conjunto de rastreamento de atividades e propagação para oferecer suporte a correlação de rastreamento ponta a ponta e definir ouvintes de rastreamento para acessar rastreamentos.  
  
 Para obter recomendações de configurações de rastreamento no ambiente de produção ou depuração, consulte [configurações recomendadas para rastreamento e registro em log de mensagem](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
>  No Windows 8, você deve executar o aplicativo com privilégios elevados (Executar como administrador) para seu aplicativo gerar logs de rastreamento.  
  
## <a name="enabling-tracing"></a>A habilitação do rastreamento  
 Windows Communication Foundation (WCF) gera os seguintes dados para o rastreamento de diagnóstico:  
  
-   Código de rastreamentos para as etapas do processo em todos os componentes de aplicativos, como chamadas de operação, exceções, avisos e outros eventos de processamento significativo.  
  
-   Eventos de erro do Windows quando o recurso de rastreamento de falhas. Consulte [o log de eventos](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 Rastreamento de WCF baseia-se na parte superior do <xref:System.Diagnostics>. Para usar o rastreamento, você deve definir fontes de rastreamento no arquivo de configuração ou em código. O WCF define uma origem de rastreamento para cada assembly do WCF. O `System.ServiceModel` origem de rastreamento é a origem de rastreamento do WCF mais geral e etapas de processamento de registros na pilha de comunicação WCF, de transporte deixando/inserir inserindo/deixar o código do usuário. O `System.ServiceModel.MessageLogging` origem de rastreamento registra todas as mensagens que fluem através do sistema.  
  
 O rastreamento não está habilitado por padrão. Para ativar o rastreamento, você deve criar um ouvinte de rastreamento e definir um nível de rastreamento que não seja "Desativado" para a origem de rastreamento selecionado na configuração; Caso contrário, o WCF não gera qualquer rastreamentos. Se você não especificar um ouvinte, o rastreamento é desabilitado automaticamente. Se um ouvinte é definido, mas nenhum nível for especificado, o nível é definido como "Off" por padrão, o que significa que nenhum rastreamento é emitido.  
  
 Se você usar pontos de extensibilidade do WCF como chamadores de operação personalizado, você deve emitir seus próprios rastreamentos. Isso ocorre porque, se você implementar um ponto de extensibilidade, WCF não pode emitir os rastreamentos padrão no caminho padrão. Se você não implementa o suporte a rastreamento manual por emissão rastreamentos, você não verá os rastreamentos que você espera.  
  
 Você pode configurar o rastreamento, editando o arquivo de configuração do aplicativo — ou Web. config para aplicativos Web hospedados ou Appname.exe.config para aplicativos hospedados automaticamente. Este é um exemplo de tal editar. Para obter mais informações sobre essas configurações, consulte a seção "Configurando ouvintes de rastreamento para rastreamentos consumir".  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
>  Para editar o arquivo de configuração de um projeto de serviço do WCF no Visual Studio, clique com botão direito arquivo de configuração do aplicativo — ou Web. config para aplicativos Web hospedados ou Appname.exe.config para o aplicativo auto-hospedado no **Gerenciador de soluções** . Em seguida, escolha o **Editar configuração WCF** item de menu de contexto. Isso inicia o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), que permite que você modifique as definições de configuração para serviços WCF usando uma interface gráfica do usuário.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Configurando fontes de rastreamento para emitir rastreamentos  
 O WCF define uma origem de rastreamento para cada assembly. Gerado em um assembly de rastreamentos são acessados pelos ouvintes definidos para essa fonte. As seguintes fontes de rastreamento são definidas:  
  
-   System. ServiceModel: Registra todos os estágios do processamento de WCF, sempre que é ler a configuração, uma mensagem é processada no transporte, segurança de processamento, uma mensagem é enviada no código do usuário e assim por diante.  
  
-   MessageLogging: Registra todas as mensagens que fluem através do sistema.  
  
-   System. IdentityModel.  
  
-   System.ServiceModel.Activation.  
  
-   System.IO.Log: Registro em log para a interface do .NET Framework para o Common Log arquivo CLFS (sistema).  
  
-   Serialization: Logs quando objetos são lidos ou gravados.  
  
-   CardSpace.  
  
 Você pode configurar cada origem de rastreamento para usar o mesmo ouvinte (compartilhado), conforme indicado no exemplo de configuração a seguir.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 Além disso, você pode adicionar fontes de rastreamento definidos pelo usuário, como demonstrado pelo exemplo a seguir, para emitir rastreamentos de código do usuário.  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />   
</system.diagnostics>  
```  
  
 Para obter mais informações sobre como criar fontes de rastreamento definidos pelo usuário, consulte [estendendo rastreamento](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Configurando os ouvintes de rastreamento para consumir rastreamentos  
 Em tempo de execução, WCF feeds de dados de rastreamento para os ouvintes que processam os dados. O WCF fornece vários ouvintes predefinidos para <xref:System.Diagnostics>, que são diferentes no formato usado para saída. Você também pode adicionar tipos de ouvinte personalizado.  
  
 Você pode usar `add` para especificar o nome e o tipo do ouvinte de rastreamento que deseja usar. Em nosso exemplo de configuração, é chamado o ouvinte `traceListener` e a adição do ouvinte de rastreamento padrão do .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) como o tipo que você deseja usar. Você pode adicionar qualquer número de ouvintes de rastreamento para cada fonte. Se o ouvinte de rastreamento emite o rastreamento em um arquivo, você deve especificar o local do arquivo de saída e o nome no arquivo de configuração. Isso é feito definindo `initializeData` com o nome do arquivo para esse ouvinte. Se você não especificar um nome de arquivo, um nome de arquivo aleatório é gerado com base no tipo de ouvinte usado. Se <xref:System.Diagnostics.XmlWriterTraceListener> for usado, será gerado um nome de arquivo sem extensão. Se você implementar um ouvinte personalizado, você também pode usar esse atributo para receber dados de inicialização que não seja um nome de arquivo. Por exemplo, você pode especificar um identificador de banco de dados para este atributo.  
  
 Você pode configurar um ouvinte de rastreamento personalizado para enviar rastreamentos na conexão, por exemplo, para um banco de dados remoto. Como um implantador do aplicativo, você deve aplicar o controle de acesso apropriadas nos logs de rastreamento no computador remoto.  
  
 Você também pode configurar um ouvinte de rastreamento programaticamente. Para obter mais informações, consulte [como: criar e inicializar ouvintes de rastreamento](http://go.microsoft.com/fwlink/?LinkId=94648) e [criando um TraceListener personalizado](http://go.microsoft.com/fwlink/?LinkId=96239).  
  
> [!CAUTION]
>  Porque `System.Diagnostics.XmlWriterTraceListener` é não segura para thread, a origem de rastreamento pode bloquear recursos exclusivamente ao exibir rastreamentos. Quando vários threads de saída de rastreamentos em uma origem de rastreamento configurado para usar este ouvinte, pode ocorrer a contenção de recursos, que resulta em um problema de desempenho significativa. Para resolver esse problema, você deve implementar um ouvinte personalizado que é thread-safe.  
  
## <a name="trace-level"></a>Nível de rastreamento:  
 O nível de rastreamento é controlado pelo `switchValue` configuração da origem do rastreamento. Os níveis de rastreamento disponíveis são descritos na tabela a seguir.  
  
|Nível de rastreamento:|Natureza dos eventos rastreados|Conteúdo dos eventos rastreados|Eventos rastreados|Destino do usuário|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Off|N/D|N/D|Nenhum rastreamento é emitido.|N/D|  
|Crítico|"Negativo" eventos: eventos que indicam um processamento inesperado ou uma condição de erro.||Exceções sem tratamento, incluindo as seguintes são registradas:<br /><br /> -OutOfMemoryException<br />-ThreadAbortException (o CLR chama qualquer ThreadAbortExceptionHandler)<br />-StackOverflowException (não pode ser detectada)<br />-ConfigurationErrorsException<br />-SEHException<br />-Erros de aplicativo Iniciar<br />-Failfast eventos<br />-Sistema trava<br />-Mensagens suspeitas: mensagem rastreamentos que causam o falha do aplicativo.|Administradores<br /><br /> Desenvolvedores de aplicativos|  
|Erro|"Negativo" eventos: eventos que indicam um processamento inesperado ou uma condição de erro.|Processamento inesperado aconteceu. O aplicativo não pôde executar uma tarefa conforme o esperado. No entanto, o aplicativo é ainda em execução.|Todas as exceções são registradas.|Administradores<br /><br /> Desenvolvedores de aplicativos|  
|Aviso|"Negativo" eventos: eventos que indicam um processamento inesperado ou uma condição de erro.|Um possível problema pode ocorrer, mas o aplicativo ainda funcionará corretamente ou tenha ocorrido. No entanto, ele não pode continuar a funcionar corretamente.|-O aplicativo está recebendo mais solicitações de permitir que suas configurações de limitação.<br />-A fila de recebimento está próximo da capacidade máxima configurada.<br />-Tempo limite foi excedido.<br />-Credenciais são rejeitadas.|Administradores<br /><br /> Desenvolvedores de aplicativos|  
|Informações|"Positivos" eventos: eventos que marcar marcos bem-sucedida|Marcos importantes e bem-sucedida de execução do aplicativo, independentemente se o aplicativo está funcionando corretamente ou não.|Em geral, são geradas mensagens úteis para monitorar e diagnosticar o status do sistema, medir o desempenho ou criação de perfil. Você pode usar essas informações para gerenciamento de desempenho e planejamento de capacidade:<br /><br /> -Canais são criados.<br />-Ouvintes de o ponto de extremidade são criados.<br />-Mensagem entra/folhas de transporte.<br />-O token de segurança é recuperado.<br />-Configuração é lida.|Administradores<br /><br /> Desenvolvedores de aplicativos<br /><br /> Desenvolvedores de produtos.|  
|Detalhado|"Positivos" eventos: eventos que marcar marcos bem-sucedida.|Eventos de Nível baixos para o código do usuário e a manutenção são emitidos.|Em geral, você pode usar esse nível de otimização de depuração ou de aplicativo.<br /><br /> -Cabeçalho da mensagem compreendidos.|Administradores<br /><br /> Desenvolvedores de aplicativos<br /><br /> Desenvolvedores de produtos.|  
|ActivityTracing||Eventos de fluxo entre atividades de processamento e componentes.|Esse nível permite que os administradores e desenvolvedores correlacionar aplicativos no mesmo domínio do aplicativo:<br /><br /> -Rastreamentos para limites de atividade, como iniciar/parar.<br />-Transferências de rastreamentos.|Todos|  
|Todos||Aplicativo pode funcionar corretamente. Todos os eventos são emitidos.|Todos os eventos anteriores.|Todos|  
  
 Os níveis de log detalhado para crítico são empilhados uns sobre os outros, ou seja, cada nível de rastreamento inclui todos os níveis acima dele, exceto o nível de Off. Por exemplo, um ouvinte está escutando em nível de aviso recebe rastreamentos crítico, erro e aviso. O nível All inclui eventos do log detalhado para crítico e atividade de eventos de rastreamento.  
  
> [!CAUTION]
>  Os níveis de informações e Verbose ActivityTracing geram uma série de rastreamentos, que pode afetar negativamente a taxa de transferência de mensagem se você tiver usado a todos os recursos disponíveis no computador.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Configuração de rastreamento de atividades e propagação de correlação  
 O `activityTracing` valor especificado para o `switchValue` atributo é usado para habilitar o rastreamento de atividade, que emite rastreamentos limites de atividade e transferências de dentro de pontos de extremidade.  
  
> [!NOTE]
>  Quando você usa determinados recursos de extensibilidade no WCF, você pode obter um <xref:System.NullReferenceException> quando o rastreamento de atividades está habilitado. Para corrigir esse problema, verifique o arquivo de configuração do aplicativo e certifique-se de que o `switchValue` atributo para a origem de rastreamento não está definida como `activityTracing`.  
  
 O `propagateActivity` atributo indica se a atividade deve ser propagada para outros pontos de extremidade que participam da troca de mensagens. Ao definir esse valor como `true`, você pode colocar arquivos de rastreamento gerados por dois pontos de extremidade e observar como um conjunto de rastreamentos em um ponto de extremidade de fluxo para um conjunto de rastreamentos em outro ponto de extremidade.  
  
 Para obter mais informações sobre rastreamento de atividades e propagação, consulte [propagação](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Ambos `propagateActivity` e `ActivityTracing` valores booleanos se aplicam a TraceSource a System. ServiceModel. O `ActivityTracing` valor também se aplica a qualquer origem de rastreamento, incluindo WCF ou aquelas definidas pelo usuário.  
  
 Não é possível usar o `propagateActivity` atributo com fontes de rastreamento definidos pelo usuário. Para propagação de ID de atividade de código de usuário, verifique se você não definir ServiceModel `ActivityTracing`, ao mesmo tempo, ServiceModel `propagateActivity` atributo definido como `true`.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Como criar e inicializar ouvintes de rastreamento](http://go.microsoft.com/fwlink/?LinkId=94648)  
 [Criando um TraceListener](http://go.microsoft.com/fwlink/?LinkId=96239)
