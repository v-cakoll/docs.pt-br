---
title: Método EnumImportTypes
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448740"
---
# <a name="enumimporttypes-method"></a>Método EnumImportTypes

Enumera cada tipo em cada escopo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>Parâmetros

`hEnum`\
Identificador para o enumerador.

`dwMax`\
Número máximo de tipos a serem recuperados.

`aTypeDefs`\
Recebe tokens de tipo, sem exceder `dwMax`.

`pdwCount`\
Recebe o número real do tipo em `aTypeDefs`.

## <a name="return-value"></a>Valor retornado

Retorna S_OK se o método tiver sucesso.

## <a name="requirements"></a>Requisitos

Requer ALink. h

## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
