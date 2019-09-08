---
title: QualifierSet_Put 関数 (アンマネージ API リファレンス)
description: QualifierSet_Put 関数は、名前付き修飾子とその値を書き込みます。
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
ms.openlocfilehash: 40688a0e4273233245d00fcd927f95945a43f712
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798272"
---
# <a name="qualifierset_put-function"></a>QualifierSet_Put 関数

名前付き修飾子と値が書き込まれます。 新しい修飾子は、同じ名前の前の値を上書きします。 修飾子が存在しない場合は、作成されます。

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
からこのパラメーターは使用されていません。

`ptr`\
から[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)インスタンスへのポインター。

`wszName`\
から書き込む修飾子の名前。

`pVal`\
から書き込む修飾子を格納し`VARIANT`ている有効なへのポインター。 このパラメーターを `null` とすることはできません。

`lFlavor`\
からこの修飾子に必要な修飾子の種類を定義する、次のいずれかの定数。 既定値は`WBEM_FLAVOR_OVERRIDABLE` (0) です。

|定数  |Value  |説明  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | 修飾子は、派生クラスまたは派生インスタンスでオーバーライドできます。 **これが既定値です。** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | この修飾子は、インスタンスに反映されます。 |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | 修飾子は、派生クラスに反映されます。 |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | この修飾子は、派生クラスまたはインスタンスではオーバーライドできません。 |
| `WBEM_FLAVOR_AMENDED` | 0x80 | 修飾子はローカライズされています。 |

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | キーにすることができないプロパティで**キー**修飾子を指定しようとしましたが、無効です。 キーは、オブジェクトのクラス定義で指定され、インスタンスごとに変更することはできません。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが有効ではありません。 |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x8004-9 | `pVal`パラメーターが有効な修飾子の型ではありません。 |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | 所有しているオブジェクトでは`QualifierSet_Put`オーバーライドが許可されていないため、修飾子に対してメソッドを呼び出すことはできません。 |
| `WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数は、 [IWbemQualifierSet::P ut](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put)メソッドの呼び出しをラップします。

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
