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
ms.openlocfilehash: 5aa629c2d07fb25db035cd80aba3c74413070e6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798397"
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
からこのパラメーターは使用されていません。

`ptr`\
から[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンスへのポインター。

`wszName`\
からプロパティの名前。 このパラメーターを `null` とすることはできません。

`lFlags`\
[in] 予約されています。 このパラメーターには0を指定する必要があります。

`pVal`\
から新しいプロパティ値になる`VARIANT`有効なへのポインター。 が`pVal` `VARIANT` `null`であるか、型`VT_NULL`のを指している場合、プロパティはに設定されます。 `null`

`vtType`\
からが指す`VARIANT` `pVal`の型。 詳細については、「[解説](#remarks)」を参照してください。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、 *WbemCli*ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。

|定数  |Value  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1つ以上のパラメーターが無効です。 |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x80041024 | プロパティの型が認識されません。 この値は、クラスが既に存在する場合に、クラスのインスタンスを作成するときに返されます。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するために必要なメモリが不足しています。 |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | インスタンスの場合:が、 `pVal`プロパティに対し`VARIANT`て正しくない型のを指していることを示します。 <br/> クラス定義の場合:プロパティが親クラスに既に存在し、新しい COM 型が古い COM 型と異なります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数の呼び出しに成功しました。 |

## <a name="remarks"></a>Remarks

この関数は、 [IWbemClassObject::P ut](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)メソッドの呼び出しをラップします。

この関数は、常に現在のプロパティ値を新しい値で上書きします。 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)がクラス定義を指している場合`Put` 、はプロパティ値を作成または更新します。 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)が CIM インスタンスを指している`Put`場合、はプロパティ値のみを更新します。`Put`プロパティ値を作成できません。

システム`__CLASS`プロパティは、クラスの作成時に、空白のままにできない場合にのみ書き込み可能です。 その他のすべてのシステムプロパティは読み取り専用です。

ユーザーは、アンダースコア ("_") で始まる名前のプロパティを作成することはできません。 これは、システムクラスおよびプロパティ用に予約されています。

`Put`関数によって設定されたプロパティが親クラスに存在する場合、プロパティの型が親クラスの型と一致しない限り、プロパティの既定値が変更されます。 プロパティが存在せず、型が一致しない場合は、プロパティが作成されます。

パラメーターを`vtType`使用するのは、CIM クラス定義に新しいプロパティを作成`null`し、がで`VARIANT`あるか`VT_NULL`、型のを指して`pVal`いる場合のみです。 この場合、パラメーターは`vType` 、プロパティの CIM 型を指定します。 それ以外の場合は`vtType` 、は0である必要があります。 `vtType`また、基になるオブジェクトがインスタンスである場合 (が`Val` `null`の場合でも)、プロパティの型が固定され、変更できないため、も0にする必要があります。

## <a name="example"></a>例

例については、「 [IWbemClassObject::P ut](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)メソッド」を参照してください。

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンスカウンター (アンマネージ API リファレンス)](index.md)
