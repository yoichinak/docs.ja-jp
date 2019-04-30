---
title: 次の関数 (アンマネージ API リファレンス)
description: 次の関数は、列挙体では、次のプロパティを取得します。
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 240544330fa352cbfdc01944e4be6bcad28dc96f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000221"
---
# <a name="next-function"></a>次の関数
呼び出しで開始する列挙体では、次のプロパティを取得します。 [BeginEnumeration](beginenumeration.md)します。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
[in]このパラメーターは使用されません。

`ptr`\
[in]ポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス。

`lFlags`\
[in] 予約されています。 このパラメーターは、0 を指定する必要があります。

`pstrName`\
[out]新しい`BSTR`プロパティ名を格納しています。 このパラメーターに設定することができます`null`名前が必要ない場合。

`pVal`\
[out]A`VARIANT`のプロパティの値が格納されます。 このパラメーターに設定することができます`null`場合は、値は必要ありません。 関数は、エラー コードを返した場合、`VARIANT`に渡される`pVal`は左未変更の状態します。

`pvtType`\
[out]ポインターを`CIMTYPE`変数 (、`LONG`にプロパティの型が配置されます)。 このプロパティの値を指定できます、 `VT_NULL_VARIANT`、この場合は、プロパティの実際の型を決定するために必要です。 このパラメーターは指定できますも`null`します。

`plFlavor`\
[out]`null`、またはプロパティの原点の情報を受信する値。 使用可能な値 [注釈] セクションを参照してください。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 呼び出しがなかった、 [ `BeginEnumeration` ](beginenumeration.md)関数。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 新しい列挙を開始するのに十分なメモリがあります。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | リモート プロシージャを呼び出す間、現在のプロセスと Windows の管理に失敗しました。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列挙には、プロパティがあります。 |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next)メソッド。

このメソッドは、システムのプロパティも返します。

プロパティの基になる型がオブジェクトのパス、日付または時刻、または別の特殊な種類の場合は、し、返される型では十分な情報が含まれませんしません。 呼び出し元を確認する必要があります、`CIMTYPE`指定したプロパティ、プロパティがオブジェクト参照を日付または時刻、または別の特殊な種類を判断します。

場合`plFlavor`は`null`、`LONG`値が次のように、プロパティの発生元に関する情報を受信します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | プロパティは、標準のシステム プロパティです。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | クラス。プロパティは、親クラスから継承されます。 <br> インスタンス。プロパティを親クラスから継承したときに変更されていないインスタンスがします。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | クラス。プロパティは、派生クラスに属しています。 <br> インスタンス。インスタンスでプロパティを変更します。つまり、値が指定されましたまたは修飾子が追加または変更します。 |

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)