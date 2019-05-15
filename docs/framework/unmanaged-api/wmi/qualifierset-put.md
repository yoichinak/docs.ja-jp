---
title: QualifierSet_Put 関数 (アンマネージ API リファレンス)
description: QualifierSet_Put 関数は、名前付きの修飾子とその値を書き込みます。
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42bef9ab728af251b043e29af4cee9e5cb3f405d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636542"
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put 関数

名前付き修飾子と値が書き込まれます。 新しい修飾子は、同じ名前の前の値を上書きします。 修飾子が存在しない場合は作成されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
[in]このパラメーターは使用されません。

`ptr`\
[in]ポインター、 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)インスタンス。

`wszName`\
[in]書き込む修飾子の名前。

`pVal`\
[in]有効なへのポインター`VARIANT`書き込む修飾子を格納しています。 このパラメーターを `null` とすることはできません。

`lFlavor`\
[in]この修飾子の必要な修飾子のフレーバーを定義する次の定数の 1 つ。 既定値は`WBEM_FLAVOR_OVERRIDABLE`(0)。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | 修飾子は、派生クラスまたはインスタンスでオーバーライドできます。 **これは、既定値です。** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | この修飾子は、インスタンスに反映されます。 |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | 修飾子は、派生クラスに反映します。 |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | この修飾子は、派生クラスまたはインスタンスではオーバーライドできません。 |
| `WBEM_FLAVOR_AMENDED` | 0x80 | 修飾子がローカライズされます。 |

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | 指定する無効なが試行されました、**キー**修飾子プロパティのキーにすることはできません。 キーが指定された om c; オブジェクトのクラス定義し、インスタンスごとに変更することはできません。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal`パラメーターが有効な修飾子型ではありません。 |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | 呼び出すことはできません、`QualifierSet_Put`メソッド修飾子を所有するオブジェクトが許可されていないためにオーバーライドします。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put)メソッド。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
