---
title: CompareTo 関数 (アンマネージ API リファレンス)
description: CompareTo 関数は、オブジェクトを別の WMI オブジェクトと比較します。
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ec42dff333422e247a11b4a3a5b9aed9bd316fa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798779"
---
# <a name="compareto-function"></a>CompareTo 関数

オブジェクトが、別の Windows 管理オブジェクトと比較されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
からこのパラメーターは使用されていません。

`ptr`\
から[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスへのポインター。

`flags`\
から比較のために考慮するオブジェクト特性を指定するフラグのビットごとの組み合わせ。 詳細については、「[解説](#remarks)」を参照してください。

`pCompareTo`\
から比較対象のオブジェクト。 `pCompareTo`有効な[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスである必要があります。にする`null`ことはできません。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 特定できないエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | への2回`BeginEnumeration`目の呼び出しは、の間[`EndEnumeration`](endenumeration.md)の呼び出しなしで行われました。 |
| `WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。  |
| `WBEM_S_DIFFERENT` | 0x40003 | オブジェクトが異なります。 |
| `WBEM_S_SAME` | 0 | これらのオブジェクトは、比較フラグに基づいています。 |

## <a name="remarks"></a>Remarks

この関数は、 [IWbemClassObject:: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto)メソッドの呼び出しをラップします。

`lEnumFlags`引数として渡すことができるフラグは、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。 次のフラグのビットごとの組み合わせを指定することで、比較に含まれる個々の特性を指定できます。

|定数  |Value  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | ソース (サーバーとその元の名前空間) を無視します。 |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | すべての修飾子を無視する (**キー**と**動的**を含む) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | プロパティの既定値を無視します。 このフラグは、クラスの比較にのみ適用されます。 |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | 修飾子の種類を無視します。 このフラグは引き続き修飾子を考慮しますが、伝達規則やオーバーライドの制限などのフレーバーの違いは無視します。 |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | 文字列値の比較で大文字と小文字を区別しません。 これは、文字列と修飾子の値の両方に適用されます。 プロパティと修飾子の名前の比較では、このフラグが設定されているかどうかに関係なく、常に大文字と小文字が区別されます。 |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | 比較対象のオブジェクトが同じクラスのインスタンスであると仮定します。 その結果、このフラグは、インスタンス関連の情報のみを比較します。 パフォーマンスを最適化するには、このフラグを使用します。 オブジェクトが同じクラスではない場合、結果は未定義になります。 |

または、次のように1つの複合フラグを指定することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | 比較のすべての機能を検討します。 |

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
