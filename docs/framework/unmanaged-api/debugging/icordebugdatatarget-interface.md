---
title: Interface ICorDebugDataTarget
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
ms.openlocfilehash: 54272dd18a12715bab58ec1b1a4c1dc00e4bf12b
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976519"
---
# <a name="icordebugdatatarget-interface"></a>Interface ICorDebugDataTarget
Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetPlatform](icordebugdatatarget-getplatform-method.md)|Fornece informações sobre a plataforma, incluindo arquitetura do processador e sistema operacional, em que o processo de destino está em execução.|  
|[Método ReadVirtual](icordebugdatatarget-readvirtual-method.md)|Obtém um bloco de memória contígua a partir do endereço especificado e a retorna no buffer fornecido.|  
|[Método GetThreadContext](icordebugdatatarget-getthreadcontext-method.md)|Solicita o contexto de thread atual para o thread especificado.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugDataTarget`e seus métodos têm as seguintes características:  
  
- Os serviços de depuração chamam os métodos nessa interface para acessar a memória e outros dados no processo de destino.  
  
- O cliente do depurador deve implementar essa interface conforme apropriado para o destino específico (por exemplo, um processo ao vivo ou um despejo de memória).  
  
- Os `ICorDebugDataTarget` métodos podem ser invocados somente de dentro de métodos implementados em outras `ICorDebug*` interfaces. Isso garante que o cliente do depurador tenha controle sobre qual thread ele é invocado e quando.  
  
- A `ICorDebugDataTarget` implementação sempre deve retornar informações atualizadas sobre o destino.  
  
 O processo de destino deve ser interrompido e não alterado de nenhuma forma `ICorDebug*` enquanto as interfaces ( `ICorDebugDataTarget` e, portanto, os métodos) estão sendo chamadas. Se o destino for um processo ao vivo e seu estado for alterado, o método [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) precisará ser chamado novamente para fornecer uma instância de ICorDebugProcess substituta.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
