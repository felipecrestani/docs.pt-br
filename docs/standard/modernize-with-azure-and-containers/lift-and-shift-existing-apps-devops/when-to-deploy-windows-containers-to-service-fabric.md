---
title: Quando implantar contêineres do Windows para serviço de malha
description: Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Quando implantar contêineres do Windows para serviço de malha
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 162714e86d1c714deea5ab7af640b66be8f330bd
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Quando implantar contêineres do Windows para serviço de malha

Aplicativos que são baseados em contêineres do Windows precisará rapidamente usam as plataformas que ainda mais afastar de VMs de IaaS. Isso é para maior escalabilidade automatizada e alta escalabilidade e obter melhorias significativas em uma experiência completa de gerenciamento para implantações, atualizações, monitoramento de integridade, reversões e controle de versão. Você pode alcançar essas metas com o orquestrador de malha do serviço do Azure, disponível na nuvem do Microsoft Azure, mas também no local, ou até mesmo em outra nuvem.

Muitas organizações estão levantar e deslocamento existentes monolíticos aplicativos contêineres por dois motivos:

-   Redução de custos, devido a remoção do hardware existente ou de aplicativos em execução em uma maior densidade e consolidação.

-   Um contrato de implantação consistente entre o desenvolvimento e operações.

Buscar reduções de custos é entendido e é provável que todas as organizações são caça a registros essa meta. Implantação consistente é mais difícil para avaliar, mas é igualmente importante. Um contrato de implantação consistente diz que os desenvolvedores estão livres para optar por usar a tecnologia que atenda às-los, e a equipe de operações é uma maneira simples para implantar e gerenciar aplicativos. Este contrato elimina a dificuldade de ter que lidar com a complexidade das muitas tecnologias diferentes operações ou forçar os desenvolvedores a funcionam apenas com algumas tecnologias. Essencialmente, cada aplicativo está em contêineres em uma imagem de implantação autossuficiente.

Algumas organizações continuará modernizar adicionando microservices (otimização de nuvem e nuvem nativo aplicativos). Muitas organizações parar aqui (nuvem DevOps pronto). Conforme mostrado na Figura 4-8, essas organizações não mova para arquiteturas microservices porque eles talvez não precise. Em qualquer caso, eles já obter os benefícios que usando contêineres de adição do Service Fabric experiência fornece um gerenciamento completo que inclui a implantação, atualizações, controle de versão, reversões e monitoramento de integridade.

> ![Comparar e Deslocar um aplicativo do Service Fabric](./media/image8.png)
>
> **Figura 4-8.** Comparar e Deslocar um aplicativo do Service Fabric

Uma abordagem chave para Service Fabric é reutilizar o código existente e simplesmente comparar e deslocar. Portanto, você pode migrar seus aplicativos do .NET Framework atuais, usando os contêineres do Windows e implantá-los ao Service Fabric. Será mais fácil manter vai modernizar, eventualmente, adicionando nova microservices.

Ao comparar o Service Fabric para outros orchestrators, é importante destacar que o Service Fabric é maduro em executar serviços e aplicativos baseados no Windows. Execução do Service Fabric serviços baseados em Windows e aplicativos, incluindo o nível 1 de missão crítica produtos da Microsoft, por anos. Era o orchestrator primeiro ter disponibilidade geral para contêineres do Windows (maio de 2017). Outros contêineres, como Kubernetes, o controlador de domínio/sistema operacional e o Docker Swarm, são mais maduros no Linux, mas menos maduro que contêineres do Windows e aplicativos baseados em malha do serviço do Windows.

A meta do Service Fabric é reduzir as complexidades de criação de aplicativos usando uma abordagem de microservices. Isso é onde você deseja, eventualmente, ser para determinados tipos de aplicativos, para evitar reformulações caras. Você pode começar pequeno, dimensionar quando necessário, substituir os serviços, adicionar novos serviços e desenvolver seu aplicativo com o uso do cliente. Sabemos que há muitos outros problemas que ainda precisam ser resolvidos para tornar microservices mais acessível para a maioria dos desenvolvedores. Se você atualmente é apenas levantar e deslocamento de um aplicativo com contêineres do Windows, mas você está pensando em Adicionar microservices com base em contêineres no futuro, que é o ponto de ideal de malha do serviço.

>[!div class="step-by-step"]
[Anterior](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[Próximo](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
