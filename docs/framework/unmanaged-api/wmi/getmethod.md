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
ms.openlocfilehash: b9cc185bf8cccb8ed3c24e28954afd86464602d7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798567"
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
からこのパラメーターは使用されていません。

`ptr`\
から[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスへのポインター。

`wszName`\
からメソッド名。 このパラメーターをに`null`することはできません`LPCWSTR`。また、有効なを指す必要があります。

`lFlags`\
[in] 予約されています。 このパラメーターには0を指定する必要があります。

`ppInSignature`\
入出力メソッドの in パラメーターを記述する[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスのアドレスへのポインター。 に`null`設定されている場合、このパラメーターは無視されます。

`ppOutSignature`\
入出力メソッドの出力パラメーターを記述する[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスのアドレスへのポインター。 に`null`設定されている場合、このパラメーターは無視されます。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定されたプロパティが見つかりませんでした。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するために必要なメモリが不足しています。 |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数は、 [IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)メソッドの呼び出しをラップします。

メソッドに in パラメーターがない場合、 `null` Windows Management は [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ポインターをに設定できます。

で`ppInSignature`は`ppOutSignature` 、とはそれぞれ、システムクラス[パラメーター](/windows/desktop/WmiSdk/--parameters)の`IWbemClassObject`インスタンスのプロパティとして in および out パラメーターを記述します。 `ppInSignature`のプロパティには*n*という名前が付け`Param`られます。ここで、 *n*はメソッドシグネチャ内`Param1`の`Param2`パラメーターの位置 (、など) です。 の`ppOutSignature`プロパティにも*n*と`Param`いう名前が付けられ、戻り`ReturnValue`値はという名前になります。 詳細と例については、「 [IWbemClassObject:: GetMethod メソッド](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)」を参照してください。

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
