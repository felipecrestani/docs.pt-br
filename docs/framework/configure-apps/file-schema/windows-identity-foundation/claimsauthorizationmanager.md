---
title: '&lt;claimsAuthorizationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 06824e20286f8905ad3a8ac9d2b4a30366a6ec10
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimsauthorizationmanagergt"></a>&lt;claimsAuthorizationManager&gt;
Registra um Gerenciador de autorização de declarações para as declarações de entrada.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<o claimsAuthorizationManager >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Um tipo personalizado que deriva de <xref:System.Security.Claims.ClaimsAuthorizationManager> classe. Para obter mais informações sobre como especificar o `type` de atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 Se não houver nenhum `type` atributo, ou se o `type` as referências ao atributo o <xref:System.Security.Claims.ClaimsAuthenticationManager> classe, o `<claimsAuthorizationManager>` elemento não tem elementos filho; no entanto, as classes derivadas de <xref:System.Security.Claims.ClaimsAuthorizationManager> podem definir elementos de configuração filho.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Especifica as configurações de identidade de nível de serviço.|  
  
## <a name="remarks"></a>Comentários  
 O comportamento padrão fornecido por meio de <xref:System.Security.Claims.ClaimsAuthorizationManager> classe sempre autoriza as declarações de entrada. Se nenhum `type` atributo for especificado ou se o `type` atributo especifica o <xref:System.Security.Claims.ClaimsAuthorizationManager> classe, o `<claimsAuthorizationManager>` elemento não tem elementos filho. Você pode especificar o `type` atributo para registrar um tipo derivado de <xref:System.Security.Claims.ClaimsAuthorizationManager> classe para implementar o comportamento personalizado. Classes derivadas podem dar suporte a configuração por meio de elementos filho de `<claimsAuthorizationManager>` elemento, substituindo o <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> método para lidar com esses elementos. O esquema definido para os elementos filho é até o designer de classe.  
  
> [!IMPORTANT]
>  Ao usar o <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ou <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe para fornecer controle de acesso baseado em declarações em seu código, a configuração de identidade que é referenciado pelo `<federationConfiguration>` elemento configura o Gerenciador de autorização de declarações e a política que é usada para fazer decisões de autorização. Isso é verdadeiro mesmo em cenários que não são cenários de Web passivos, por exemplo, aplicativos do Windows Communication Foundation (WCF) ou um aplicativo que não é baseado na Web. Se o aplicativo não é um aplicativo da Web passivo, o `<claimsAuthorizationManager>` elemento (e seus elementos de diretiva filho, se presente) da configuração de identidade referenciada são as únicas configurações aplicadas. Todas as outras configurações são ignoradas. Para obter mais informações, consulte o [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elemento.  
  
 Este elemento define o <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="example"></a>Exemplo  
 O XML a seguir mostra a configuração de uma autorização de declarações Gerenciador que implementa a diretiva composta de pares de ação de recurso de cada uma delas Especifica Boolianas combinações das declarações que um solicitante deve ter para executar a ação do recurso. O código que implementa o Gerenciador de autorização de declarações capaz de usar essa política pode ser encontrado no `ClaimsBasedAuthorization` exemplo.  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
