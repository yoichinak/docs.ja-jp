---
title: StrongNameKeyInstall 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7121ace6777e7cf947fcc6ff30b1ea314851feff
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636715"
---
# <a name="strongnamekeyinstall-function"></a>StrongNameKeyInstall 関数

公開/秘密キーの組がコンテナーにインポートされます。

この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnamekeyinstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md)メソッド代わりにします。

## <a name="syntax"></a>構文

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a>パラメーター

`wszKeyContainer`\
[in]キー コンテナーの名前。 `wszKeyContainer` 空でない文字列である必要があります。

`pbKeyBlob`\
[in]バイナリ キーのペアです。

`cbKeyBlob`\
[in]サイズ (バイト単位) の`pbKeyBlob`します。

## <a name="return-value"></a>戻り値

`true` 正常に終了します。それ以外の場合、`false`します。

## <a name="remarks"></a>Remarks

使用して、 [StrongNameKeyDelete](strongnamekeydelete-function.md)キー コンテナーを削除する関数。

場合、`StrongNameKeyInstall`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** StrongName.h

**ライブラリ:** MsCorEE.dll でリソースとして含まれます

**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>関連項目

- [StrongNameKeyInstall メソッド](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete メソッド](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
