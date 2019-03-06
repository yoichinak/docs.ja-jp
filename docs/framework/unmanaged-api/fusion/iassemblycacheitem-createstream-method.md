---
title: IAssemblyCacheItem::CreateStream メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 380e248c8c4e3407fff868cdd9a5c63b63e50c69
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353908"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream メソッド

指定した名前と形式を使用するストリームを作成します。

## <a name="syntax"></a>構文

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a>パラメーター

`dwFlags`\
[in]ものがありますで定義されているフラグ。

`pszStreamName`\
[in]作成されるストリームの名前。

`dwFormat`\
[in]ストリーミングされるように、ファイルの形式です。

`dwFormatFlags`\
[in]形式固有のものがありますで定義されているフラグ。

`ppIStream`\
[out]返されるのアドレスへのポインター [IStream](/windows/desktop/api/objidl/nn-objidl-istream)インスタンス。

`puliMaxSize`\
[in、省略可能]によって参照されるストリームの最大サイズ`ppIStream`します。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** Fusion.h

**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [IAssemblyCacheItem インターフェイス](iassemblycacheitem-interface.md)