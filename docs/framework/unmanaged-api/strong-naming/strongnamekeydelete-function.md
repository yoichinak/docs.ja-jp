---
title: StrongNameKeyDelete 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17d35193f69966e02ac5e483924fcb3ee2e06758
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799020"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete 関数

指定したキー コンテナーが削除されます。

この関数は非推奨とされます。 代わりに[ICLRStrongName:: StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md)メソッドを使用してください。

## <a name="syntax"></a>構文

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>パラメーター

`wszKeyContainer`\
から削除するキーコンテナーの名前。

## <a name="return-value"></a>戻り値

`true`正常に完了した場合は。それ以外`false`の場合は。

## <a name="remarks"></a>Remarks

公開/秘密キーのペアをコンテナーにインポートするには、 [StrongNameKeyInstall](strongnamekeyinstall-function.md)関数を使用します。

関数が正常に完了しない場合は、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。`StrongNameKeyDelete`

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** StrongName

**ライブラリ**Mscoree.dll にリソースとして含まれています

**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>関連項目

- [StrongNameKeyDelete メソッド](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall メソッド](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
