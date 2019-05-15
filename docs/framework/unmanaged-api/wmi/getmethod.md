---
title: GetMethod 関数 (アンマネージ API リファレンス)
description: GetMethod 関数は、メソッドに関する情報を取得します。
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 419fb33155cfa91199e52110da29efd44d606f4b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636605"
---
# <a name="getmethod-function"></a>GetMethod 関数

指定したメソッドに関する情報が取得されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
[in]このパラメーターは使用されません。

`ptr`\
[in]ポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス。

`wszName`\
[in]メソッドの名前。 このパラメーターにすることはできません`null`有効 をポイントする必要があります`LPCWSTR`します。

`lFlags`\
[in] 予約されています。 このパラメーターは、0 を指定する必要があります。

`ppInSignature`\
[out]アドレスへのポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)メソッドにパラメーターを記述するインスタンス。 設定されている場合、このパラメーターは無視されます`null`します。

`ppOutSignature`\
[out]アドレスへのポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)メソッドに out パラメーターを記述するインスタンス。 設定されている場合、このパラメーターは無視されます`null`します。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定したプロパティが見つかりませんでした。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)メソッド。

Windows の管理を設定できる、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)へのポインター`null`メソッドにパラメーターがあるない場合。

`ppInSignature`と`ppOutSignature`in および out パラメーターをそれぞれのプロパティとして、説明、`IWbemClassObject`システム クラスのインスタンス[_Parameters](/windows/desktop/WmiSdk/--parameters)します。 プロパティ`ppInSignature`という名前は`Param` *n*ここで、 *n*メソッド シグネチャ内のパラメーターの位置です (など`Param1`、`Param2`など。)。 プロパティ`ppOutSignature`とも呼ば`Param` *n*、戻り値の名前は`ReturnValue`します。 詳細と例では、次を参照してください。 [IWbemClassObject::GetMethod メソッド](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)します。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
