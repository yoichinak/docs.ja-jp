---
title: CompareTo 関数 (アンマネージ API リファレンス)
description: CompareTo 関数は、別の WMI オブジェクトにオブジェクトを比較します。
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
ms.openlocfilehash: 3566b9b8a3b4183f936c82c39c38dc5daa3aeae1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636687"
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
[in]このパラメーターは使用されません。

`ptr`\
[in]ポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス。

`flags`\
[in]比較検討するオブジェクトの特性を指定するフラグのビットごとの組み合わせ。 参照してください、[解説](#remarks)詳細についてはします。

`pCompareTo`\
[in]比較対象のオブジェクト。 `pCompareTo` 有効な[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス; することはできません`null`します。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 2 番目の呼び出し`BeginEnumeration`せずに、中間の呼び出しが行われた[ `EndEnumeration`](endenumeration.md)します。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
| `WBEM_S_DIFFERENT` | 0x40003 | オブジェクトが異なるです。 |
| `WBEM_S_SAME` | 0 | オブジェクトは、比較フラグに基づくものと同じです。 |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto)メソッド。

フラグとして渡すことができる、`lEnumFlags`で引数が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。 次のフラグのビットごとの組み合わせを指定することで、比較に関連する個々 の特性を指定できます。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | (サーバーと、元の名前空間) のソースを無視します。 |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | すべての修飾子を無視 (を含む**キー**と**動的**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | プロパティの既定値を無視します。 このフラグは、クラスの比較にのみ適用されます。 |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | 修飾子のフレーバーを無視します。 このフラグはまだ修飾子では考慮が反映規則などのフレーバーの区別は無視されます、制限を上書きします。 |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | 文字列値の比較で大文字小文字は無視されます。 これには、文字列と修飾子の値の両方が適用されます。 プロパティと修飾子の名前の比較では、常にこのフラグが設定されているかに関係なく大文字小文字を区別します。 |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | 比較対象のオブジェクトが、同じクラスのインスタンスであると仮定します。 そのため、このフラグは、インスタンスに関連する情報のみを比較します。 このフラグを使用すると、パフォーマンスを最適化できます。 同じクラスのオブジェクトがない場合、結果は未定義です。 |

または、次のように 1 つの複合フラグを指定することができます。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | 比較のすべての機能を検討してください。 |

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
