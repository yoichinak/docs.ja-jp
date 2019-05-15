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
ms.openlocfilehash: 717d2104db8addf40e5187cee4cc8c46e5dc355e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636735"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete 関数

指定したキー コンテナーが削除されます。

この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnamekeydelete](../hosting/iclrstrongname-strongnamekeydelete-method.md)メソッド代わりにします。

## <a name="syntax"></a>構文

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>パラメーター

`wszKeyContainer`\
[in]削除するキー コンテナーの名前。

## <a name="return-value"></a>戻り値

`true` 正常に終了します。それ以外の場合、`false`します。

## <a name="remarks"></a>Remarks

使用して、 [StrongNameKeyInstall](strongnamekeyinstall-function.md)公開/秘密キー ペアをコンテナーにインポートする関数。

場合、`StrongNameKeyDelete`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** StrongName.h

**ライブラリ:** MsCorEE.dll でリソースとして含まれます

**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>関連項目

- [StrongNameKeyDelete メソッド](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall メソッド](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
