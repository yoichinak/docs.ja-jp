---
title: Put 関数 (アンマネージ API リファレンス)
description: Put 関数は、名前付きプロパティに新しい値を割り当てます。
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fba929e5a1a1e4c2b69e15bf6c855211e25a67a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636620"
---
# <a name="put-function"></a>Put 関数

名前付きプロパティが新しい値に設定されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
[in]このパラメーターは使用されません。

`ptr`\
[in]ポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス。

`wszName`\
[in]プロパティの名前。 このパラメーターを `null` とすることはできません。

`lFlags`\
[in] 予約されています。 このパラメーターは、0 を指定する必要があります。

`pVal`\
[in]有効なへのポインター`VARIANT`新しいプロパティ値になります。 場合`pVal`は`null`を指す、または、`VARIANT`型の`VT_NULL`に設定されて`null`します。

`vtType`\
[in]型`VARIANT`によって示される`pVal`します。 参照してください、[解説](#remarks)詳細についてはします。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つまたは複数のパラメーターが無効です。 |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | プロパティの型は認識されません。 クラスが既に存在する場合は、クラスのインスタンスを作成するときに、この値が返されます。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | インスタンス。示します`pVal`を指す、`VARIANT`プロパティの型が正しくないのです。 <br/> クラス定義。親クラスのプロパティが既に存在し、新しい COM 型が古い COM 型と異なる。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。 |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)メソッド。

この関数は常を新しい現在のプロパティ値を上書きします。 場合、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)クラスの定義を指す`Put`を作成またはプロパティの値を更新します。 ときに[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) CIM のインスタンスを指す`Put`更新プログラムのプロパティの値だけです。`Put`プロパティ値を作成することはできません。

`__CLASS`システム プロパティは書き込み可能なクラスの作成時に場合にのみこれが空白にできません。 その他のすべてのシステム プロパティとは、読み取り専用です。

ユーザーは、アンダー スコア (_) で開始または終了する名前を持つプロパティを作成することはできません。 これはシステム クラスとプロパティの予約されています。

プロパティで設定した場合、`Put`親クラスの関数が存在する、プロパティの既定値が変わらない限り、プロパティの型が、親クラスの型と一致しません。 プロパティが存在しない型の不一致がない場合は、プロパティが作成されます。

使用して、 `vtType` CIM クラスの定義で新しいプロパティを作成する場合にのみ、パラメーターと`pVal`は`null`を指す、または、`VARIANT`型の`VT_NULL`します。 ここで、`vType`パラメーター プロパティの CIM 型を指定します。 その他のすべてのケースで`vtType`0 にする必要があります。 `vtType` 基になるオブジェクトがインスタンスの場合も、0 をある必要があります (場合でも`Val`は`null`) ため、プロパティの型は固定され変更できません。

## <a name="example"></a>例

例については、次を参照してください。、 [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)メソッド。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
