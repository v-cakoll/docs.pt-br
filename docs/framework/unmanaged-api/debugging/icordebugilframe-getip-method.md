---
title: Método ICorDebugILFrame::GetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: 3890cb4236f113bc6efc23bfb606d19a525ec234
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210261"
---
# <a name="icordebugilframegetip-method"></a>Método ICorDebugILFrame::GetIP
Obtém o valor do ponteiro de instrução e um valor de combinação de bits que descreve como o valor do ponteiro de instrução foi obtido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pnOffset`  
 fora O valor do ponteiro de instrução.  
  
 `pMappingResult`  
 fora Um ponteiro para uma combinação de bits de bit que descreve os valores de enumeração CorDebugMappingResult que descrevem como o valor do ponteiro de instrução foi obtido.  
  
## <a name="remarks"></a>Comentários  
 O valor do ponteiro de instrução é o deslocamento do registro de ativação no código MSIL (Microsoft Intermediate Language) da função. Se o registro de ativação estiver ativo, esse endereço será a próxima instrução a ser executada. Se o registro de ativação não estiver ativo, esse endereço será a próxima instrução a ser executada quando o quadro de pilha for reativado.  
  
 Se esse quadro for um quadro compilado JIT (just-in-time), o valor do ponteiro de instrução será determinado pelo mapeamento retroativo do ponteiro de instrução nativa real, de modo que o valor pode ser apenas aproximado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
