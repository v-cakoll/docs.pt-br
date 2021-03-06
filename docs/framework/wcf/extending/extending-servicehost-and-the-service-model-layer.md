---
title: Estendendo a camada de modelo de serviço e o ServiceHost
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: e370316cd121f49953e00e83dfc9d2aec17de1e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795730"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>Estendendo a camada de modelo de serviço e o ServiceHost
A camada do modelo de serviço é responsável por extrair mensagens de entrada dos canais subjacentes, traduzi-las em invocações de método no código do aplicativo e enviar os resultados de volta para o chamador. As extensões de modelo de serviço modificam ou implementam o comportamento de execução ou de comunicação e os recursos que envolvem funcionalidade de cliente ou Dispatcher, comportamentos personalizados, interceptação de mensagem e de parâmetro e outras funcionalidades de extensibilidade.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estendendo clientes](extending-clients.md)  
 Descreve as interfaces que podem interceptar e modificar o tempo de execução do cliente, bem como as classes nas quais você pode inserir suas extensões personalizadas em aplicativos cliente. Por exemplo, você pode executar o log de mensagens do cliente personalizado, executar a serialização de mensagem personalizada e assim por diante.  
  
 [Estendendo dispatchers](extending-dispatchers.md)  
 Descreve as interfaces que podem interceptar e modificar o tempo de execução do serviço, bem como as classes nas quais você pode inserir suas extensões personalizadas em aplicativos de serviço. Por exemplo, você pode executar o log de serviço personalizado, a validação de mensagens no lado do serviço, a expedição personalizada e assim por diante.  
  
 [Objetos extensíveis](extensible-objects.md)  
 Descreve os cinco objetos extensíveis e o <xref:System.ServiceModel.IExtensibleObject%601> padrão. O padrão de objeto extensível é usado para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar um novo estado a um objeto. Extensões, anexadas a um dos objetos extensíveis, habilitam comportamentos em estágios muito diferentes no processamento para acessar o estado compartilhado e a funcionalidade anexada a um objeto extensível comum que eles podem acessar.  
  
 [Configurando e estendendo o tempo de execução com comportamentos](configuring-and-extending-the-runtime-with-behaviors.md)  
 Para alterar as configurações ou inserir extensões no tempo de execução do WCF, use comportamentos. O WCF inclui comportamentos implementados pelo sistema para controlar a limitação, a instanciação e muitos outros aspectos de serviços e operações. Esta seção descreve como criar seus próprios comportamentos personalizados e como torná-los disponíveis para uso programaticamente e usando arquivos de configuração.  
  
 [Estendendo a hospedagem usando ServiceHostFactory](extending-hosting-using-servicehostfactory.md)  
 Descreve como estender <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>e usar as <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes para personalizar o ambiente de host.  
  
## <a name="reference"></a>Referência  
  
## <a name="related-sections"></a>Seções relacionadas
