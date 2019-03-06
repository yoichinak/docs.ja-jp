---
title: QualifierSet_GetNames 関数 (アンマネージ API リファレンス)
description: QualifierSet_GetNames 関数は、オブジェクトまたはプロパティから修飾子の名前を取得します。
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da6321e50082c3f73477b8187cc5bf671655df21
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365946"
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames 関数

すべての修飾子のまたは現在のオブジェクトまたはプロパティから利用できる特定の修飾子の名前を取得します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
[in]このパラメーターは使用されません。

`ptr`\
[in]ポインター、 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)インスタンス。

`lFlags`\
[in]次のフラグまたは列挙体に追加するには、どの名前を指定する値の 1 つ。

|定数  |値  |説明  |
|---------|---------|---------|
|  | 0 | すべての修飾子の名前を返します。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 現在のプロパティまたはオブジェクトに特定修飾子の名前のみを返します。 <br/> プロパティ。(上書きを含む)、プロパティに固有の修飾子のみとクラス定義から反映された修飾子いないに返されます。 <br/> インスタンス。インスタンス固有の修飾子名のみが返されます。 <br/> クラス。クラスを派生させる特定の修飾子のみを返します。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 別のオブジェクトから修飾子の名前のみが反映される戻り値。 <br/> プロパティ。戻り値修飾子のみが反映されるこのプロパティに、クラス定義と、プロパティ自体から。 <br/> インスタンス。クラス定義からこれらの修飾子が反映される戻り値。 <br/> クラス。戻り値の修飾子名のみが親クラスから継承されます。 |

`pstrNames`\
[out]新しい`SAFEARRAY`要求の名前を格納しています。 配列要素の 0 ことができます。 エラーが発生した場合、新しい`SAFEARRAY`は返されません。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 新しい列挙を開始するのに十分なメモリがあります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames)メソッド。

修飾子の名前を取得すると名前での各修飾子をアクセスを呼び出して、 [QualifierSet_Get](qualifierset-get.md)関数。

そのため、0 個の修飾子に指定したオブジェクトのエラーではありませんで文字列の数`pstrNames`返された場合は、0、関数を返しても、`WBEM_S_NO_ERROR`します。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)