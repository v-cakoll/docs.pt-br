---
title: DbConnection, DbCommand e DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 09526f111adeecb817ce4c4e587ca3713e0d8cde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785192"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand e DbException
Depois de criar um <xref:System.Data.Common.DbProviderFactory> e um <xref:System.Data.Common.DbConnection>, você pode trabalhar com comandos e leitores de dados para recuperar dados da fonte de dados.  
  
## <a name="retrieving-data-example"></a>Recuperando exemplo de dados  
 Este exemplo usa um `DbConnection` objeto como um argumento. Um <xref:System.Data.Common.DbCommand> é criado para selecionar dados da tabela Categories definindo o <xref:System.Data.Common.DbCommand.CommandText%2A> como uma instrução SQL SELECT. O código supõe que a tabela Categories exista na fonte de dados. A conexão é aberta e os dados são recuperados usando <xref:System.Data.Common.DbDataReader>um.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Executando um exemplo de comando  
 Este exemplo usa um `DbConnection` objeto como um argumento. Se o `DbConnection` for válido, a conexão será aberta e um <xref:System.Data.Common.DbCommand> será criado e executado. O <xref:System.Data.Common.DbCommand.CommandText%2A> é definido como uma instrução SQL Insert que executa uma inserção na tabela Categories no banco de dados Northwind. O código supõe que o banco de dados Northwind exista na fonte de dado e que a sintaxe SQL usada na instrução INSERT seja válida para o provedor especificado. Os erros que ocorrem na fonte de dados são manipulados <xref:System.Data.Common.DbException> pelo bloco de código e todas as outras exceções são tratadas <xref:System.Exception> no bloco.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>Manipulando erros de dados com DbException  
 A <xref:System.Data.Common.DbException> classe é a classe base para todas as exceções geradas em nome de uma fonte de dados. Você pode usá-lo em seu código de manipulação de exceção para tratar as exceções geradas por provedores diferentes sem precisar fazer referência a uma classe de exceção específica. O fragmento de código a seguir demonstra como <xref:System.Data.Common.DbException> usar o para exibir informações de erro retornadas pela <xref:System.Exception.GetType%2A>fonte de <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>dados usando <xref:System.Exception.Message%2A> as propriedades, <xref:System.Exception.Source%2A>, e. A saída exibirá o tipo de erro, a origem que indica o nome do provedor, um código de erro e a mensagem associada ao erro.  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [DbProviderFactories](dbproviderfactories.md)
- [Obtendo um DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [Modificando dados com um DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
