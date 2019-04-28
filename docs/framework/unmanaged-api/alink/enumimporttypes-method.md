---
title: EnumImportTypes メソッド
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d0aefea7345bc3bf37bdb8d13cb2cda19cfe527
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789956"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes メソッド

それぞれのスコープでは、各種類を列挙します。

## <a name="syntax"></a>構文

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>パラメーター

`hEnum`\
列挙子の処理です。

`dwMax`\
取得する型の最大数。

`aTypeDefs`\
超えないように、型のトークンを受け取る`dwMax`します。

`pdwCount`\
型の実際の数を受け取る`aTypeDefs`します。

## <a name="return-value"></a>戻り値

メソッドが成功した場合は、S_OK を返します。

## <a name="requirements"></a>必要条件

Alink.h が必要です。

## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)