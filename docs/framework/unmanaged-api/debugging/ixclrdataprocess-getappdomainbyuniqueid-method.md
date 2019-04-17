---
title: IXCLRDataProcess::GetAppDomainByUniqueId メソッド
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8b468d40ef8eb523ba8881627fae15cf9b7c7b80
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614023"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a>IXCLRDataProcess::GetAppDomainByUniqueId メソッド

取得、`AppDomain`の一意の識別子に基づくプロセスにします。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a>パラメーター

`id`\
[in]AppDomain の一意の識別子

`appDomain`\
[out]AppDomain

## <a name="remarks"></a>Remarks

指定されたメソッドは、`IXCLRDataProcess`インターフェイスし、仮想メソッド テーブルの 20 のスロットに対応しています。 `IXCLRDataAppDomain*`返されるその他の Api との対話のために使用します。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。
**ヘッダー:** None**ライブラリ。** None **.NET Framework のバージョン。** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [IXCLRDataProcess インターフェイス](ixclrdataprocess-interface.md)
