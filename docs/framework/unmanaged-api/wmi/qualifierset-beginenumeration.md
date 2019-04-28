---
title: QualifierSet_BeginEnumeration 関数 (アンマネージ API リファレンス)
description: QualifierSet_BeginEnumeration 関数は、オブジェクトの修飾子の列挙子をリセットします。
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663434d3e3d44dc0c406e71592651493bd8f8dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597245"
---
# <a name="qualifiersetbeginenumeration-function"></a>QualifierSet_BeginEnumeration 関数

オブジェクトの修飾子の列挙子が列挙型の先頭にリセットされます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
[in]このパラメーターは使用されません。

`ptr`\
[in]ポインター、 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)インスタンス。

`lFlags`\
[in]フラグまたはで説明されている値のビットごとの組み合わせ、[解説](#remarks)セクション列挙体に含める修飾子を指定します。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` パラメーターが正しくありません。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 2 番目の呼び出し`QualifierSet_BeginEnumeration`せずに、中間の呼び出しが行われた[ `QualifierSet_EndEnumeration`](qualifierset-endenumeration.md)します。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 新しい列挙を開始するのに十分なメモリがあります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration)メソッド。

すべてのオブジェクトの修飾子を列挙するには、最初の呼び出しの前にこのメソッドを呼び出す[QualifierSet_Next](qualifierset-next.md)します。 修飾子が列挙される順序は、指定された列挙型のバリアントに保証します。

フラグとして渡すことができる、`lEnumFlags`で引数が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
|  | 0 | すべての修飾子の名前を返します。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 現在のプロパティまたはオブジェクトに特定修飾子の名前のみを返します。 <br/> プロパティ。(上書きを含む)、プロパティに固有の修飾子のみとクラス定義から反映された修飾子いないに返されます。 <br/> インスタンス。インスタンス固有の修飾子名のみが返されます。 <br/> クラス。クラスを派生させる特定の修飾子のみを返します。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 別のオブジェクトから修飾子の名前のみが反映される戻り値。 <br/> プロパティ。戻り値修飾子のみが反映されるこのプロパティに、クラス定義と、プロパティ自体から。 <br/> インスタンス。クラス定義からこれらの修飾子が反映される戻り値。 <br/> クラス。戻り値の修飾子名のみが親クラスから継承されます。 |

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)