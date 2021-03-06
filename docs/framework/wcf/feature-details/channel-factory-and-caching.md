---
title: Cache e fábrica de canal
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 5b8348a98b484ca08e3dbeba141dc49825c8c071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587359"
---
# <a name="channel-factory-and-caching"></a>Cache e fábrica de canal

Os aplicativos cliente do WCF usam a classe <xref:System.ServiceModel.ChannelFactory%601> para criar um canal de comunicação com um serviço WCF.  Criar instâncias de <xref:System.ServiceModel.ChannelFactory%601> resulta em alguma sobrecarga porque envolve as seguintes operações:

- Construir a árvore de <xref:System.ServiceModel.Description.ContractDescription>

- Refletir todos os tipos CLR necessários

- Construir a pilha de canal

- Descarte de recursos

Para ajudar a minimizar a sobrecarga, o WCF pode armazenar em cache fábricas de canal quando você está usando um proxy de cliente WCF.

> [!TIP]
> Você tem controle direto sobre a criação de fábrica de canal quando usa a <xref:System.ServiceModel.ChannelFactory%601> classe diretamente.

Os proxies de cliente do WCF gerados com a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) são derivados de <xref:System.ServiceModel.ClientBase%601> . <xref:System.ServiceModel.ClientBase%601>define uma <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> propriedade estática que define o comportamento de cache da fábrica de canais. As configurações de cache são feitas para um tipo específico. Por exemplo, `ClientBase<ITest>.CacheSettings` a configuração para um dos valores definidos abaixo afetará somente o proxy/ClientBase do tipo `ITest` . A configuração de cache para um específico <xref:System.ServiceModel.ClientBase%601> é imutável assim que a primeira instância de proxy/ClientBase é criada.

## <a name="specifying-caching-behavior"></a>Especificando o comportamento de cache

O comportamento de caching é especificado definindo a <xref:System.ServiceModel.ClientBase%601.CacheSetting> propriedade como um dos valores a seguir.

|Valor de configuração de cache|Descrição|
|-------------------------|-----------------|
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|Todas as instâncias de <xref:System.ServiceModel.ClientBase%601> dentro do aplicativo-domínio podem participar do Caching. O desenvolvedor determinou que não há nenhuma implicação de segurança negativa no cache. O cache não será desativado mesmo que as propriedades "sensíveis à segurança" <xref:System.ServiceModel.ClientBase%601> sejam acessadas. As propriedades "sensíveis à segurança" do <xref:System.ServiceModel.ClientBase%601> são <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> , <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> e <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A> .|
|<xref:System.ServiceModel.CacheSetting.Default>|Somente instâncias de <xref:System.ServiceModel.ClientBase%601> criadas a partir de pontos de extremidade definidos em arquivos de configuração participam do cache dentro do domínio de aplicativo. Qualquer instância do <xref:System.ServiceModel.ClientBase%601> criada programaticamente nesse aplicativo-domínio não participará do cache. Além disso, o Caching será desabilitado para uma instância do <xref:System.ServiceModel.ClientBase%601> uma vez que qualquer uma de suas propriedades "sensíveis à segurança" for acessada.|
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|O Caching é desativado para todas as instâncias de <xref:System.ServiceModel.ClientBase%601> um tipo específico dentro do aplicativo-domínio em questão.|

Os trechos de código a seguir ilustram como usar a <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> propriedade.

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))
         {
            // ...
            proxy.Test(msg);
            // ...
         }
      }
   }
}
// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }
```

No código acima, todas as instâncias do `TestClient` usarão a mesma fábrica de canais.

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase.CacheSettings = CacheSettings.Default;
      int i = 1;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))
         {
            if (i == 4)
            {
               ServiceEndpoint endpoint = proxy.Endpoint;
               ... // use endpoint in some way
            }
            proxy.Test(msg);
         }
         i++;
   }
}

// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}
```

No exemplo acima, todas as instâncias de `TestClient` usariam a mesma fábrica de canais, exceto #4 de instância. A instância #4 usaria uma fábrica de canais criada especificamente para seu uso. Essa configuração funcionaria para cenários em que um ponto de extremidade específico precisa de configurações de segurança diferentes dos outros pontos de extremidade do mesmo tipo de fábrica de canal (nesse caso `ITest` ).

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))
         {
            proxy.Test(msg);
         }
      }
   }
}

// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}
```

No exemplo acima, todas as instâncias de `TestClient` usariam fábricas de canal diferentes. Isso é útil quando cada ponto de extremidade tem requisitos de segurança diferentes e não faz sentido armazenar em cache.

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.ClientBase%601>
- [Compilando clientes](../building-clients.md)
- [Clientes](clients.md)
- [Usando um cliente do WCF para acessar serviços](../accessing-services-using-a-wcf-client.md)
- [Como usar o ChannelFactory](how-to-use-the-channelfactory.md)
